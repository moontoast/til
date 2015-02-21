# Removing Old Versions from Homebrew

If you're using [Homebrew][brew] and looking to remove old versions of packages in your `/usr/local`, use the `cleanup` command.

    $> brew cleanup

When run without any arguments, `cleanup` will attempt to remove all old versions for all installed packages.
By default, however, it will skip any packages that aren't at the latest version.

If you want to be specific about what to remove, you can do that:

    $> brew cleanup <package>

This will remove old versions of `<package>`, but leave all other packages alone.
You may remove multiple packages at the same time by passing multiple to the `cleanup` command, separated by spaces.

If you're a more cautious person, try a dry-run first:
    $> brew cleanup -n

This will tell you what will be deleted, but won't actually delete anything until you remove the `-n`.

There are plenty of reasons to keep old versions around, but if you need some space or just want a tidier system, `cleanup` is what you're looking for.

[brew]: http://brew.sh/
