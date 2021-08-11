#### 3.1 create a new folder and start a new git repository
```console
user@host project $ mkdir ../project_repo2
user@host project $ cd ../project_repo2
user@host project $ git init
```

#### 3.2 configure a new user name and email just for fun
```console
user@host project_repo2 $ git config user.name dumbledore
user@host project_repo2 $ git config user.email dumbledore@darkside
```

#### 3.3 add the original repository as a remote
```console
user@host project_repo2 $ git remote add firstrepo ../project
```
Note that we could just `git clone` it, but it's more "fun" to do it by hand.
`firstrepo` is the local name for the original repository.
With `git clone` the default name for remotes is `origin`.
We can add many remotes.

#### 3.4 print information about remotes
```console
user@host project_repo2 $ git remote -v
```

#### 3.5 get all the data with `git fetch`
```console
user@host project_repo2 $ git fetch firstrepo
```

#### 3.6 see what's in the current directory and run the long `git log` command
```console
user@host project_repo2 $ ls
```
No files. It's OK.
```console
user@host project_repo2 $ git log --all --decorate --oneline --graph
```
There should be the same commits as in the other repository.
The branches are prefixed by the name of the remote. We will need local branches too.


#### 3.7 checkout the master branch from firstrepo
```console
user@host project_repo2 $ git checkout firstrepo/master
```
Git will complain that no local branches exist. Let's make a branch `main`
Use `git status` and the long `git log` command to visualize the current branch and where HEAD is pointing to.
```console
user@host project_repo2 $ git branch main
user@host project_repo2 $ git status
user@host project_repo2 $ git log --all --decorate --oneline

user@host project_repo2 $ git checkout main
user@host project_repo2 $ git status
user@host project_repo2 $ git log --all --decorate --oneline
```

#### 3.8 do some changes and commit them

Add something to `file1.txt` and then commit

```console
user@host project_repo2 $ git add file1.txt
user@host project_repo2 $ git commit -m "some changes"
```

#### 3.9 visualize local branches and remote branches

```console
user@host project_repo2 $ git log --all --decorate --oneline
```

#### 3.10 push branch main to the first repo
```console
user@host project_repo2 $ git push firstrepo main
```

Alternatively we could have set up `project_repo2` as a remote of `project`, and fetch the `main` branch.

#### 3.11 change dir to the original repository and visualize the main branch we just pushed
```console
user@host project_repo2 $ cd ../project
user@host project $ git log --all --decorate --oneline
```

#### 3.12 merge main onto master
```console
user@host project $ git checkout master
user@host project $ git merge main
user@host project $ git log --all --decorate --oneline
```

#### 3.13 alias the long `git log` command
```console
user@host project $ git config --global alias.adog "log --all --decorate --oneline --graph"
user@host project $ git adog
```
Could have done this earlier, maybe.
