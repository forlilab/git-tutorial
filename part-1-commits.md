## 1. Start git and create a couple of commits 

Let's assume we are in a folder called `project` that has a single file named `file1.txt`, with the following text:
```console
user@host project $ cat file1.txt
Roses are red.
Violets are blue.
```

#### 1.1 run `git init`
```console
user@host project $ git init
Initialized empty Git repository in /path/to/project/.git/
```
That `.git` folder is where git keeps all the info. Do not delete it :-)

#### 1.2 run `git status` just to see what's up.
```console
user@host project $ git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	file1.txt
nothing added to commit but untracked files present (use "git add" to track)
```
In short, git is telling us that file `file1.txt` is not tracked.

Committing changes is a two step process. First, we select which files to commit
and then we actually commit them.

#### 1.3 run `git add file1.txt`
```console
user@host project $ git add file1.txt
user@host project $ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   file1.txt
#
```

#### 1.4 Check username and email to sign commits

Now, before we commit these changes, let's check the username and email address that will sign the commit.
Each commit will carry this information permanently. If this repository is made public online, the username
and email address will be visible and unchangeable.
```console
user@host project $ git config user.name
user@host project $ git config user.email
```

If this prints nothing, or if you want to change it, do:
```console
user@host project $ git config user.name tinkywinky
user@host project $ git config user.email tinkywinky@darkside
```

Optionally use `--global` to set username and email for all repositories (info is saved in `~/.gitconfig`) .

#### 1.5 finally commit

The string after the `-m` option is a message describing the changes.

```console
user@host project $ git commit -m "initial draft of mock text"
[master (root-commit) ad3de4c] initial draft of mock text
 1 file changed, 8 insertions(+)
 create mode 100644 file1.txt
```

#### 1.6 Verify that everything went well

`git status` should say something like "nothing to see here":

```console
user@host project $ git status
On branch master
nothing to commit, working tree clean
```

`git log` should display the commit that we just did

```console
user@host project $ git log
commit ad3de4cff1abdba0ceeaf53a95429f1eadb4a42f (HEAD -> master)
Author: tinkywinky <tinkywinky@darkside>
Date:   Tue Aug 10 22:39:05 2021 -0700

    initial draft of mock text
```

#### 1.7 modify a file and compare it to the committed version

Change the second line of the `file1.txt`, from `Violets are blue.` to `Nitrogens are blue.`. Now let's visualize the changes. The following command will bring up a multipanel vim editor. 

```console
user@host project $ git difftool -t vimdiff
```
The left panel is what is commited, and the second panel is the current state of `file1.txt`.


#### 1.8 restore a file

If we regret changing the file we can revert the changes with either `git checkout` or `git restore`:
```console
user@host project $ git checkout file1.txt
Updated 1 path from the index
```
Now, the contents of the file match what was committed, and the changes were lost.
So, be careful with `git checkout` and `git restore`. Imagine you worked 10h on a file, forgot to commit the changes, and then restored it. You just lost 10h.

We can also delete files and bring them back to the working directory:
```console
user@host project $ rm file1.txt
user@host project $ git checkout file1.txt
Updated 1 path from the index
```

#### 1.9 create a second commit

Again, change the second line of `file1.txt`, from `Violets are blue.` to `Nitrogens are blue.`.

Add the changes and commit them:
```console
user@host project $ git add file1.txt
user@host project $ git commit -m "changed violets to nitrogens"
[master 4391f65] expanded 2nd to second
 1 file changed, 1 insertion(+), 1 deletion(-)
 
user@host project $ git log
commit 4391f659eb71153d0e2fd88197e7ac78b7ab0274 (HEAD -> master)
Author: tinkywinky <tinkywinky@darkside>
Date:   Tue Aug 10 23:01:16 2021 -0700

    changed violets to nitrogens

commit ad3de4cff1abdba0ceeaf53a95429f1eadb4a42f
Author: tinkywinky <tinkywinky@darkside>
Date:   Tue Aug 10 22:39:05 2021 -0700

    initial draft of mock text
```

### Go to next part
[part 2 - branches](part-2-branches.md)
