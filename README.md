<h1>Group-Based-Script-Permissions-Linux</h1>


<h2>Description</h2>
This project demonstrates secure user and group management in a Linux environment using group-based permissions and shell scripting. It shows how to restrict script execution so that only authorized users from specific groups can run them, using tools like chmod and chgrp. The solution reinforces the concept of access control and secure scripting in multi-user systems.
<br />


<h2>Languages and Utilities Used</h2>

- Shell Scripting (Bash) – For automating user/group setup and enforcing access rules.
- Linux User & Group Management – Using useradd, groupadd, usermod, etc.
- chmod, chgrp – For setting script permissions based on group ownership.
- Terminal/CLI – Command-line interface for all configurations and testing.

<h2>Environments Used </h2>

- Kali Linux (via VirtualBox)
- Host OS: macOS Ventura 13.7.4 (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Launch the Terminal on Linux and create user1 using the following command: sudo adduser user1. Follow the on-screen prompts, set the user's password as 1234, and press enter for all other details: <br/>
<img src="https://i.imgur.com/gsEcZ0j.png"/>
<br />
<br />
Repeat the steps and create 3 more users: user2, user3, and user4:  <br/>
<img src="https://i.imgur.com/NNv8mjz.png"/>
<br />
<br />
List all the users using the following command: cut -d: -f1 /etc/passwd: <br/>
<img src="https://i.imgur.com/u7feHnP.png"/>
<img src="https://i.imgur.com/LQwW1xm.png"/>
<br />
<br />
Create group1 using the following command sudo groupadd group1:  <br/>
<img src="https://i.imgur.com/X7SU9e5.png"/>
<br />
<br />
Add user1 and user2 to group1 using the following commands: sudo usermod -aG group1 user1 for user1 and sudo usermod -aG group1 user2 for user2:  <br/>
<img src="https://i.imgur.com/80nfOEc.png"/>
<br />
<br />
Create group2 using the following command: sudo groupadd group2:  <br/>
<img src="https://i.imgur.com/p5eJuTv.png"/>
<br />
<br />
Add user3 and user4 to group2 using the following commands: sudo usermod -aG group2 user3 for user3 and sudo usermod -aG group3 user4 for user4:  <br/>
<img src="https://i.imgur.com/8v849hz.png"/>
<br />
<br />
Switch to user1 and navigate to the /tmp directory using the following command: su - user1 and cd /tmp directory:  <br/>
<img src="https://i.imgur.com/Q19rCKA.png"/>
<br />
<br />
Create a script file for group1 using the following command: nano group1script.sh and paste script in the file
#!/bin/bash
echo "Script accessible by Group 1." then press Ctrl + O to write the file(Save), press Enter and Ctrl + X to exit nano :  <br/>
<img src="https://i.imgur.com/epbOExb.png"/> 
<img src="https://i.imgur.com/Y9Bt3Wf.png"/> 
<br />
<br />
Set execute permissions for group1 script by running chmod 750 group1script.sh.
This will ensure that only the root user and members of group1 can execute the script:  <br/>
<img src="https://i.imgur.com/eInmRG9.png"/>
<br />
<br />
Switch to user3 and navigate to the /tmp directory using the following commands: su – user3 and cd /tmp directory:  <br/>
<img src="https://i.imgur.com/Il5HSLE.png"/>
<br />
<br />
Create a script file for group2 using the following command: nano group2script.sh and paste the script in the file
#!/bin/bash
echo "Script accessible by Group 2." then press Ctrl + O to write the file(Save), press Enter and Ctrl + X to exit nano:  <br/>
<img src="https://i.imgur.com/8NEn6sD.png"/>
<img src="https://i.imgur.com/GUfTDGx.png]"/>
<br />
<br />
Set execute permissions for group2 script using chmod 750 group2script.sh.
This will ensure only the root user and members of the group2 can execute the script:  <br/>
<img src="https://i.imgur.com/2R35TaH.png"/>
<br />
<br />
Run the script as user3 using the following command: . /group1script.sh. It should
deny permission to access since user1, a group1 member, has permission:  <br/>
<img src="https://i.imgur.com/t9beCx4.png"/>
<br />
<br />
Switch to user1 using the following command: su – user1, run the script as user1 by using /tmp/group1script.sh. It should display the output as group 1 user has permission:  <br/>
<img src="https://i.imgur.com/ZDXWztp.png"/>
<br />
<br />
Run the script as user1 using /tmp/group2script.sh command. It should fail because group 1 users don’t have permission: <br/>
<img src="https://i.imgur.com/ZNL1ILi.png"/>
<br />
<br />
Switch to user3 by running su - user3. Then, run the script as user3 using tmp/group2script.sh. It should display the output because Group 2 user has permission:<br/>
<img src="https://i.imgur.com/9LnxqjE.png"/>
Done! You've successfully implemented secure script execution based on group permissions — a key skill for managing multi-user Linux environments.
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
