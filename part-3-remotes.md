#### 3.1 generate ssh keys if they dont exist yet

The keys are in the `.ssh` folder in the home directory.
```console
$ ssh-keygen -t ecdsa -b 521
```

#### 3.2 copy the `.pub` key to the github webpage

Click on user image, then Settings > SSH and GPG keys, then green button `New SSH key`
and copy paste the the public key (filename ends with `.pub`).

#### 3.3 create a new GitHub repository

#### 3.4 add it as a remote and push contents

#### 3.5 close elsewhere, mimicking a second user

#### 3.6 create a new branch `paragraph2` and push to GitHub

#### 3.7 the other user fetches and checks out

```console
$ git fetch
$ git checkout origin/paragraph2
```

#### 3.8 create GitHub PR from the `paragraph2` branch

#### 3.9 fork this repo on GitHub

#### 3.10 push to fork's main branch and create PR
