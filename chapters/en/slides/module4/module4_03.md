---
type: slides
title: 'module4_03'
---

# Reset your Git project to an earlier state

Notes:
In this slide deck we will see how we can restore past versions of our Git projects.

---

## Time travelling

<br>
<br>
<br>


We are going to learn two ways to travel back in time to a previous commit:
<br>
1. **Doing a hard reset**
2. **Reverting previous changes**

Notes:
It's not uncommon to realize that we made a mistake when viewing the history! 
Maybe we didn't mean to delete an important file and we want to undo our latest commit. 
Don't worry, we can now take advantage of tracking our files  
using version control to retrieve a previous state of a file and replace the current version.

There are two ways of traveling back in time to an earlier state of the repo:

1. Remove commits from the Git history (a "hard reset").
2. Create a new commit to undo previous changes (a "reversion").

In this slide deck we will look into `git reset` and in the next one
we will cover `git revert`.

---

## Hard reset (JupyterLab)

<center>

<img src='/module4/vc-hard-reset.png' width="800px" alt="404 image"/>

</center>

Notes:
A hard reset deletes your changes AND the history of your project
by removing the commits from your current branch.
To perform a hard reset in JupyterLab,
you should click the clock icon next to the commit you would like to travel back to.

---

## Hard reset (JupyterLab)


<center>

<img src='/module4/vc-hard-reset-warning.png' width="800px" alt="404 image"/>

</center>

Notes:
Be careful! This action can't be undone and JupyterLab will display a dialog box 
to confirm that you are sure that you want to discard your commits.

---

## Hard reset (JupyterLab)


<center>

<img src='/module4/vc-hard-reset-pull.png' width="800px" alt="404 image"/>

</center>

Notes:
After doing a hard reset on your local Git repository,
you would need to push your changes to the remote repository
for them to be visible online.
However,
because you have changed the Git history by removing some commits,
this would lead to issues for your colleagues
who still have these commits on their computers.
Therefore,
it is not recommended to use a hard reset when working with collaborators,
unless there are extraordinary circumstances requiring it.

If you have performed a hard reset locally,
but you change your mind
you could use the backup on the remote repository to undo your local changes
by pulling back the commits from the remote repository.

---

## Hard reset (Terminal)

`git reset --hard <commit hash>`
`git push -f/--force`

<center>

<img src='/module4/vc-reset-hard-push.png' width="800px" alt="404 image"/>

</center>




Notes:
In the terminal,
you can look at the `git log` output to find the commit hash we want to reset our project to. 
Then we can use the command `git reset --hard <commit hash>`.

Git by default protects from unintentionally pushing after a hard reset.
If you really want to delete the commits and remove them from GitHub,
you must use the command `git push -f` to "force" the push in the terminal,
regardless of whether you choose to execute the hard reset 
using the JupyterLab IDE or the terminal.

After doing a hard reset,
JupyterLab will offer you to pull
the locally deleted commits from the remote.
You shouldn't pull if you want to preserve
the deletion of commits you made with the hard reset!

Extra
If we want to make a new commit with the changes since the reset point,
we can perform a "soft" reset with `git reset --soft`.
This command will not discard the information on the deleted commits as `git reset --hard`,
if not will save all in the staging area in case you would like to create a new commit with those changes.
This command is useful if you want to combine a series of local commits into one.
Note that `git reset --soft` is only avaible in the terminal,
and not via JupyterLab.

---

# Let's apply what we learned!
