# How to Customize the virtualenv Info in Your `PS1`
Start by installing XCode Command Line tools using this terminal command

```sh
xcode-select --install
```

And add this line before the line containing the PS1 assignment

```sh
source /Library/Developer/CommandLineTools/usr/share/git-core/git-prompt.sh
```

Then, add this function to your `.bash_profile` or `.bashrc` file:

```sh
function virtualenv_info() {
    # Get Virtual Env
    if [[ -n "$VIRTUAL_ENV" ]]; then
        # Strip out the path and just leave the env name
        venv="${VIRTUAL_ENV##*/}"
    else
        # In case you don't have one activated
        venv=''
    fi
    [[ -n "$venv" ]] && echo "($venv) "
}
```

Then we disable the normal functionality of virtualenvwrapper so that it plays nice with git, and create a simple variable that will hold our venv info.
Do this by also adding the following to your `.bash_profile` or `.bashrc`:

```sh
export VIRTUAL_ENV_DISABLE_PROMPT=1
export VENV="\$(virtualenv_info)"
```

With that, you can use `$VENV` in your `PS1` however you see fit. Here's an example of placing it at the beginning of your prompt, and coloring it yellow:

```sh
PS1="\[\033[0;33m\]${VENV}\[\033[0m\]\[\[\033[0;32m\][\w]\[\033[0m\]\$(__git_ps1)\n\[\033[1;36m\]\u\[\033[0;32m\]$ \[\033[0m\]"
```
