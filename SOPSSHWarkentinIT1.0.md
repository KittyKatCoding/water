# Standard Operating Procedure for Setting Up SSH Key Authentication on a Linux Server

# Warkentin IT
https://github.warkentin.uk

Date: July 22, 2026



### Purpose

The purpose of this Standard Operating Procedure Document is to outline the proper method of setting up SSH key authentication on a Linux server.

### Scope

This document is for network technicians setting up SSH access with SSH keys.

### Accountability Matrix

| Task | Responsible Party | Notes |
| :--- | :--- | :--- |
| **Server SSH Setup** | Administrator | The server SSH setup is to be done by the administrator. |
| **SSH Connection Testing From Client Computer** | Client | The client should use their work computer to test if it works. |

### Revision History

| Version | Date | Changes Made By | Summary of Changes
| :--- | :--- | :--- | :--- |
| **1.0** |⠀2026-07-22 | Evan Warkentin| Initial Release of Document|
| ⠀|⠀| ⠀ | |


### Approval Table 

| Version | Date | Name |Designation|
| :--- | :--- | :--- | :--- |
| **1.0** | 2026-07-22 | Evan Warkentin |Author|
| **⠀** | ⠀ | ⠀ | |


### Procedure Steps:



To prepare a Linux server you must have access to the root account or a user with sudo permissions.



Open the terminal and type these commands to install and enable openssh.

###### \[YourServer]$ sudo dnf install openssh-server

###### \[YourServer]$ systemctl enable --now sshd



To verify that the status is running type:



###### \[YourServer]$ sudo systemctl status sshd



To find your local IP address for ssh access type the command ip addr

###### \[YourServer]$ip addr





On the server, generate a public key, then share it.

To generate the keys, type this:



###### \[YourServer]$ sudo ssh-keygen



To share the public key with a client computer type this command:



###### \[YourServer]$ sudo ssh-copy-id remoteuser@clientcomputer



Enter the client's password, then that computer has the public key which means it can login without a password.



To verify that SSH key authentication works try connecting by SSH from the client computer.



For firewall to work, make shure you allow SSH in the firewall.

###### \[YourServer]$ sudo firewall-cmd --permanent --add-service=ssh



Then you need to reload the firewall.

###### \[YourServer]$ sudo firewall-cmd --reload



If you can not connect try pinging the ip address, if you can not ping between both computers there could be a network issue.



Make sure your passwords are always at least 20 characters long with uppercase and lowercase letters and symbols so that the password is difficult to brute force.



### References:



Amoany, Evans.(2022, April 27). How to configure key-based authentication for SSH. [https://www.redhat.com/en/blog/key-based-authentication-ssh](https://www.redhat.com/en/blog/key-based-authentication-ssh)

Amoany, Evans. (2022, May 5). How to access remote systems using SSH. [https://www.redhat.com/en/blog/access-remote-systems-ssh](https://www.redhat.com/en/blog/access-remote-systems-ssh)



