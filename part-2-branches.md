## 2. Merging branches

#### 2.1 create a new branch called `crazyidea`

```console
user@host project $ git branch crazyidea
user@host project $ git checkout crazyidea
```

#### 2.2 run `git status` to make sure everything is OK
```console
user@host project $ git status
```
It will state which branch is checked out, make sure it's `crazyidea`.

#### 2.3 make changes

Delete the second paragraph of `file1.txt` (Starting with "Let us add...") and add the following two lines:
```
Branches are not folders. They are like pointers and act as anchors
to append new commits.
```

The contents of the file now are:
```console
user@host project $ cat file1.txt
This is the first line of the file.
And this is the second line.
We are just adding some random text here for the sake of modifying it and
keeping track of the differences later.
Differences are calculated line by line.

Branches are not folders. They are like pointers and act as anchors
to append new commits.
```

#### 2.4 add and commit the changes
```console
user@host project $ git add file1.txt
user@host project $ git commit -m "modified paragraph 2"
```

#### 2.5 visualize the graph of commits
```console
user@host project $ git log --all --decorate --oneline --graph
```
Each commit is one line.
HEAD points to the commit that is checked out (the latest commit).
The `crazyidea` branch points to the latest commit.
The `master` branch is still pointing to second commit.

#### 2.6 merge crazyidea to master

In this case, merging is equivalent to updating the `master` branch to point to the latest commit.

```console
user@host project $ git checkout master
user@host project $ git merge crazyidea
user@host project $ git log --all --decorate --oneline --graph
```

#### 2.7 create yet another branch: `fixwording`
```console
user@host project $ git branch fixwording
user@host project $ git status
user@host project $ git log --all --decorate --oneline --graph
```

We created the `fixwording` branch, but we are still in the master branch.

#### 2.8 do changes and commit them to `master`

Split the first paragraph of `file1.txt` into two, by expanding the last line
of the first paragraph into its own paragraph. The contents now are:
```console
user@host project $ cat file1.txt
This is the first line of the file.
And this is the second line.
We are just adding some random text here for the sake of modifying it and
keeping track of the differences later.

Differences are calculated line by line.
We can add binary files but the differences are not very useful.

Branches are not folders. They are like pointers and act as anchors
to append new commits.
```

Commit the changes.
```console
user@host project $ git add file1.txt
user@host project $ git commit -m "split first paragraph in two"
```

#### 2.9 run `git log --all --decorate --online --graph` to see what's up

Branch `fixwording` should point to the previous commit, while `master` points
to the latest commit.

#### 2.10 commit changes to branch `fixwording`

First checkout the branch. Run git status before and after changing branch.
```console
user@host project $ git status
user@host project $ git checkout fixwording
user@host project $ git status
```

Also run the long `git log` command to make sure that HEAD is where we want it to be.
```console
user@host project $ git log --all --decorate --online --graph
```

Edit the file. Change lines 3, 4, and 5 from
```
We are just adding some random text here for the sake of modifying it and
keeping track of the differences later.
Differences are calculated line by line.
```
to
```
We are adding random text to modify it and to
keep track of the differences later.
Text differences are calculated line by line.
```

Add and commit the changes
```console
user@host project $ git add file1.txt
user@host project $ git commit -m "improved wording"
```

Look at the graph with `git log --all --decorate --online --graph`


#### 2.10 Look at differences between specific commits

Consider the following commit graph
```
* 82e34e7 (HEAD, fixwording) improved wording
| * 8b3c5d6 (master) split first paragraph in two
|/  
* 362bffc modified paragraph 2
* 62fbfe6 expanded 2nd to second
* 758fe9d initial draft of mock text
```

We can look at the differences between `master` and `fixwording` with either of these two commands:
```console
user@host project $ git difftool -t vimdiff master fixwording
user@host project $ git difftool -t vimdiff 8b3c5d6 82e34e7
```

#### 2.11 Merge
There will be conflicts :-)
