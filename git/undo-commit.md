# How to Roll Back a Commit

I accidentally committed something to develop that needed to be on its own branch.
To fix this, I created a new branch off the current state of develop (with the accidental commit).

    git checkout -b new-branch develop

Then I went back to `develop` (`git checkout develop`) and removed the accidental commit from the history using...

    git reset --hard HEAD^
    
This command says "move history back one commit, throwing away that commit entirely".
Now I have what I needed in the first place: `develop` is clean and untouched, and my commit is safe on its own branch.

If you want an alternative way of accomplishing this, you can check out [this StackOverlow question](http://stackoverflow.com/questions/2941517/how-to-fix-committing-to-the-wrong-git-branch).

