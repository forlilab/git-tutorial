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

Modify both lines of `file1.txt` and add a third line:
```
Oxygens are red.
Nitrogens are blue.
In Cryo-EM everything is grey.
```

#### 2.4 add and commit the changes
```console
user@host project $ git add file1.txt
user@host project $ git commit -m "change to elements"
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

#### 2.7 create a new commit in a new branch `beautify`

```console
user@host project $ git branch beautify
user@host project $ git checkout beautify
```

Change `everything` to `all` in the third line of `file1.txt`.

```console
user@host project $ git add file1.txt
user@host project $ git commit -m "improve wording"
user@host project $ git status
user@host project $ git adog
```

#### 2.8 go back to `master` and commit

```console
user@host project $ git checkout master
user@host project $ git adog
```

Change `grey` to `gray` in the third line of `file1.txt`:

```console
user@host project $ git add file1.txt
user@host project $ git commit -m "changed to gray"
```

#### 2.9 run `git log --all --decorate --online --graph` to see the branching

```console
user@host project $ git adog
```

#### 2.10 Look at differences between specific commits

Consider the following commit graph
```
* 82e34e7 (HEAD, master) changed to gray
| * 8b3c5d6 (beautify) improve wording
|/  
* 362bffc change to elements
* 62fbfe6 roses to tomatoes
* 758fe9d initial draft of mock text
```

We can look at the differences between `master` and `beautify` with either of these two commands:

```console
user@host project $ git difftool -t vimdiff master beautify
user@host project $ git difftool -t vimdiff 8b3c5d6 82e34e7
```

#### 2.11 Merge
There will be conflicts, which need to be manually resolved.

```
Roses are red.
Nitrogens are blue.
<<<<<<< HEAD
In Cryo-EM everything is gray.
=======
In Cryo-EM all is grey.
>>>>>>> test
```
