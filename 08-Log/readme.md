git-log
=======

* Show commit logs

You can use `git log` for inspecting history of a repository, individual files or even specific lines in a file! But remember, this text is just a brief introduction into `git-log`, so go see documentation for more details if you need to.

Now, let me just start this with a quick remark that very few of you will likely use `git-log` on a daily basis. But still, it's good to know how to use it.

It's simplest form `git log` we already know, so let's try something more compact

	$ git log --oneline
	81b21df My first lab commit 2
	12893d6 My first lab commit 1
	4930d89 First commit and comment for it

we can see history of current branch. Now, you can provide branch

	$ git log --oneline my_apple_app
	323c19e OS X version
	81b21df My first lab commit 2
	12893d6 My first lab commit 1
	4930d89 First commit and comment for it

specific file(s)

	$ git log --oneline MyConsoleApp/console.txt
	81b21df My first lab commit 2
	12893d6 My first lab commit 1

or even directory

	$ git log --oneline MyConsoleApp
	81b21df My first lab commit 2
	12893d6 My first lab commit 1

But this is all just iterations of the same, so let's try something more interesting.

	$ git mv MyWindowsApp/code.txt MyWindowsApp/dll.txt
	$ git commit -m "moved code into dll"
	[master 5afd97a] moved code into dll
	 1 file changed, 0 insertions(+), 0 deletions(-)
	 rename MyWindowsApp/{code.txt => dll.txt} (100%)
	$ git log --follow --oneline MyWindowsApp/dll.txt
	5afd97a moved code into dll
	81b21df My first lab commit 2
	12893d6 My first lab commit 1

We can see that the file was tracked even across renames! We can even add `-p` flag and let git list diff for complete history of the file across renames.

	$ git log --follow -p MyWindowsApp/dll.txt
	commit 5afd97a08c72c88e7dbf36b77ac58fc667f22957
	Author: Wolf <wolf@wolfsden.cz>
	Date:   Tue Mar 29 17:14:43 2016 +0200

		moved code into dll

	diff --git a/MyWindowsApp/code.txt b/MyWindowsApp/dll.txt
	similarity index 100%
	rename from MyWindowsApp/code.txt
	rename to MyWindowsApp/dll.txt

	commit 81b21df59ecbeea7d84b5b64a46e2e6fd9d76467
	Author: Wolf <wolf@wolfsden.cz>
	Date:   Tue Mar 29 14:27:21 2016 +0200

		My first lab commit 2

	diff --git a/MyWindowsApp/code.txt b/MyWindowsApp/code.txt
	index e69de29..fc8502f 100644
	--- a/MyWindowsApp/code.txt
	+++ b/MyWindowsApp/code.txt
	@@ -0,0 +1 @@
	+Added during git workshop

	commit 12893d6b26503372a03df3d257f4bd28aa235fba
	Author: Wolf <wolf@wolfsden.cz>
	Date:   Tue Mar 29 14:26:30 2016 +0200

		My first lab commit 1

	diff --git a/MyWindowsApp/code.txt b/MyWindowsApp/code.txt
	new file mode 100644
	index 0000000..e69de29

> I'm not using `--oneline` here, since without colors it gets kinda dense.

More informations
-----------------

I recommend checking [git-log documentation](https://git-scm.com/docs/git-log) for more details, there is a **lot** of options for `git log`.
