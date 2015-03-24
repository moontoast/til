#Today I learned

##how to roll back a commit.

I had committed something to develop accidentally. I created a new branch off the current state of develop (with the commit). Then I went back to develop and used git reset --soft HEAD^ [found here] (http://stackoverflow.com/questions/2941517/how-to-fix-committing-to-the-wrong-git-branch).
