# Bash Commands
![Static Badge](https://img.shields.io/badge/Bash-red) 


# Overview
Repo compiling the main bash commands I used during my DS-MLOps journey. Very short repo. 
For more details, check/ask for the obsidian folder.

# Bash Language
## Cheatlist keywords
- cd
- pwd
- ls
- touch
- echo
- cat
- rm
- cp
- mv
- grep: filter the lines containing the expression we want.
- |: pipe to take in input the output of the previous command.
- &&: to combine commands with no links between them.
- chmod: change rights
- man: for the manual of the function (man ls)

## Bash Script

A Bash script is a file containing code lines in bash.
On top it has a **shebang** to indicate  the location of the shell to execute the code.

```bash
#!/bin/bash
```
Or
```bash
#!/bin/python3
```
## How to execute 
- To read only the script.
```bash
bash script.sh
```
- To execute the script. Be careful with the rigths!
Or
```bash
./script.sh
```

## Change the rights
```bash
chmod +x script.sh
```


# File and Folder manipulation

## Creation (touch or mkdir)

```bash
touch file_name1 file_name2
mkdir folder_name1 folder_name2
```

## Remmove (rm)

```bash
rm file_name1
rm /home/ubuntu/filename1
rm -r /home/ubuntu/folder_name1
```

## Copy/Paste or Cut/Paste (cp - mv)

```bash
cp ./file1 ./folder_x/
cp ./file1 ./folder_x/new_file2


# Edition and read (echo cat)

## Write (Edition)

```bash
echo hello world > file1
echo hello world >> file2
```

**> erases the content**
**>> appends the content**


## Read
```bash
cat file1
```


# ...More (check obsidian for more details)

We can also
- Define a variable
  ```bash
  my_var=hello
  echo $my_var
  ```
- Math operation
  ```bash
  let "a=2"
  let b=2
  ```
  - Loop (for and while)
  - Function



# Bonus
## apt
apt is a paquet manager.

```bash
sudo apt-get update
sudo apt-get install curl
```






