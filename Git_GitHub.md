# Github and Github 

![Static Badge](https://img.shields.io/badge/Git_Github-red) 
![Static Badge](https://img.shields.io/badge/Terminal-white)


# Overview
How to start with Git/Github.
[x] Create an ssh connection between local and distant repo.
[x] Main git commands



# Git Bases

## Git vs Github

Git is the versionning tool or "language" to work locally.
Guthub is the place where all the repos are stored.-> to collaborate with colleagues.

## Installation
```bash
sudo apt update
sudo apt install git
```

## Git init
Using the terminal, locally go to the folder of the project and type **git init**
This create a folder .git in the project folder.

## Git add 
When I modified my work locally I need to do **git add .** to add all the files.
Or we can do **git add file_name**

## Git commit

After the git add, we need to do **git commit -m 'comment'**

## Git push
To push the files in the commit zone to the distant repo.


## Git clone
To clone a repo from distant repo to local repo.
- HTTPS
- SSH
SSH is more secure.
### SSH procedure
1- Generate a SSH key opening the terminal.
  
  ```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

We have generated a **private key** (NEVER SHARE IT!!)

2- In the terminal have a look to the public key.
  cat /Users/xxxxxx/.ssh/id_xxxx.pub

3- Copy the ssh public key and go to Github

4- Open Settings

5- SSH and GPG keys

6- Create a new ssh key and paste the key-> we can connect git and github now!

### Cloning procedure
On github select the repo to clone. Copy the clone ssh link.
Open a terminal and type **git clone paste_link_from_Github**

We have now locally a clone of the repo from github.


## Git pull
This upload locally the last modification made to the distant repo.
This is the first thing to do when you start your day. You pull the distant repo to the local repo incase someone worked previously.

## Git log
To see all the commit performed.

## Git checkout
**git checkout commit_number** 

We can go back to a specific version using the commit number.


## Git branch
**git branch** return the name of the different branches.
**git branch name_branch** create a new branch 
**git checkout name_branch** move us to the branch name_branch.

## Git merge
```bash
git checkout main
git merge branch_to_merge
git add .
git commit -m 'fusion 2 branhes'
git push
```

## Git ignore
This is super important to ignore the virtual environment folder created at the beginning of the project. This folder does not need to be in the different pushes.
In the project folder, create a **.gitignore** file and write in it the files/folders you want to ignore.

```txt
# Ignore folder
/folder_name
```

In the terminal we **GO TO MAIN**, and wew do the git merge name_branch.

**DO NOT FORGET TO DELETE THE BRANCH AT THE END**


## Git fetch




## Git fork
This does a copy of the repo in github. The copy is in github NOT LOCALLY.
In other words:
Distant copy of a distant repo.

