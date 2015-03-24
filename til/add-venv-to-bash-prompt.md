#Today I learned

##How to add the current active virtual environment to my bash prompt

###Start by adding this function to your bash profile.

```
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

###Then we disable the normal functionality of virtualenvwrapper so that it plays nice with git

```
export VIRTUAL_ENV_DISABLE_PROMPT=1
```

###Create a new environment variable using our function to display the correct env

```
export VENV="\$(virtualenv_info)"
```

###Then insert that variable in your prompt, here is my current PS1. Notice the use of VENV.

```
PS1="\[\033[0;33m\]${VENV}\[\033[0m\]\[\[\033[0;32m\][\w]\[\033[0m\]\$(__git_ps1)\n\[\033[1;36m\]\u\[\033[0;32m\]$ \[\033[0m\]"
```
