# Virtual Machine
![Static Badge](https://img.shields.io/badge/Virtual_Machine-red) 
![Static Badge](https://img.shields.io/badge/SSH_Connection-white)
![Static Badge](https://img.shields.io/badge/Linux-green) 


# Overview
During the MLOps part of my formation, I had to connect to a virtual machine from AWS using an SSH connection. Here are a summarize of the big ideas of this ssh connection from my host machine to the virtual one.

# SSH Connection
Secured connection between my local machine and the distant one. 
We need to download an authentification key (**.pem) and keep it on the local machine.



# How to connect?
## First connection

  1- Download the private key .pem.

  2- Change the rights of the key.
    - Go to the folder containing the key
    ```bash
cd /home/[user_name]/Downloads
```
    - Check the key is present
```bash
ls | grep data_engineering_machine.pem
# This list all the files in the folder, and then filter (grep) the files having the name data...
```
    - Change the rights
    ```bash
    chmod 400 data_enginering_machine.pem```

3- Connection to the machine
**Once in the folder containing the private key**, we can connect.
ubuntu is the name of the user, and X.X.X.X is the IP dynamic of this machine. This was changing every time when swtiching on the machine on the platform.
```bash
ssh -i "data_engineering_mahcine.pem" ubuntu@X.X.X.X
```


# Download files from the distant to local machine

## Work on your distant machine
- You have create a main folder named BashLinux.
- You have put some files/folder in it.
    -> Exam_linux
        ->exam_bash_jb
    -> Exam_bash
        ->exam_linux_jb

- Go to parent folder
  ```bash
  cd BashLinux
  ```

- Create an archive
 
  ```bash
  tar -cvf exam_bash_jb.tar exam_bash_jb
  ```
  
## From your local machine

- Go to the folder where the .pem key is and type

```bash
scp -i "data_engineerin_machine.pem" ubuntu@X.X.X.X: "exam_bash_jb.tar" .
```


# Connection with a Tunnel ssh

To redirect a process from a distant machine to the local one. **-L** to **redirect a local port to a distant one**.
```bash
ssh -i "data_engineering_nachine.pem" -L 1234:localhost:4321 ubuntu@X.X.X.X
```
This redirect the process occuring on the local port 1234 to the distant one 4321.


# Deconnection
```bash
exit
```


#

