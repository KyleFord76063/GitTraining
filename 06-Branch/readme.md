git-branch
==========

* List, create or delete branches

Let's list branches we have:

    git branch [--list]

Great, we've got this:

    * master

We can see one branch called `master` with asterisk marking currently
active branch. Create new branch

    git branch new_brach

again, let's check (with `git branch`) what branches we currently have

    * master
	  new_brach

oh, we made a mistake in spelling! But don't worry, we can fix that with

	git branch -m new_brach new_branch

we just renamed the branch to fix it

	* master
	  new_branch

And you know what? We don't need the new branch, since we don't know how
to switch into it (yet!) anyway, so let's delete it

    git branch -d new_branch

So, to sum up what we've just learned

* git branch [--list]
	* list branches
* git branch $BRANCH_NAME
	* creates branch named $BRANCH_NAME from current HEAD
* git branch -m $OLD_BRANCH_NAME $NEW_BRANCH_NAME
	* rename branch
* git branch -d $BRANCH_NAME
	* delete branch

More informations
-----------------

I recommend checking [git-branch documentation](https://git-scm.com/docs/git-branch) for more detail,
you can use `git-branch` to manage/list remote branches as well, set upstream for branch, create new
branch from specific commit and more. All of that is out of scope of this tutorial.
