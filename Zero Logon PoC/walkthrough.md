## impacket installation
First we need to install impacket in our machine in a virtual environment.

![image](https://github.com/user-attachments/assets/8cd2416a-19ff-4f71-bb6a-403e932eb24e)


The source for the proof of concept to check whether Domain Controller is exploitable or not can be found at this source: https://raw.githubusercontent.com/SecuraBV/CVE-2020-1472/master/zerologon_tester.py

The source code needed to be modified a little bit to exploit the Zero Logon vulnerability. The modified source code can be found here: https://raw.githubusercontent.com/Sq00ky/Zero-Logon-Exploit/master/zeroLogon-NullPass.py


## Task 3: The Proof of Concept of the TryHackMe room

	What method will allow us to change Passwords over NRPC?
![image](https://github.com/user-attachments/assets/04eb93fe-6345-4b6d-9243-6d552b7e9092)


	What are the required fields for the method per the Microsoft Documentation?
![image](https://github.com/user-attachments/assets/930172e6-9ff0-4214-9f6f-365d544be7c4)


	What Opnumber is the Method?
![image](https://github.com/user-attachments/assets/131248b5-fc5a-44dc-9b4c-fa01bfa5ea36)

Source: https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-nrpc/14b020a8-0bcf-4af5-ab72-cc92bc6b1d81


## Task 4: Lab it Up!

Firstly, we are going to run an nmap scan against our target IP address, with the -sC and -sV options to enable default script scan and version detection for each servive found running on open ports:

![image](https://github.com/user-attachments/assets/cce80cd8-f40b-430e-926b-1e2af26c673c)


	What is the NetBIOS name of the Domain Controller?
![image](https://github.com/user-attachments/assets/e5728381-d24f-4ea7-b713-4449b4518cbf)


 	What is the NetBIOS domain name of the network?
![image](https://github.com/user-attachments/assets/ba3a1e48-8386-4705-ac76-57625c2242ef)


 	What domain are you attacking?
![image](https://github.com/user-attachments/assets/3bafbc80-0f06-4b68-b747-4917ddc335d1)


Now that we know our Domain Controller's NetBIOS name, we can verify if the target can be exploited using the tester script.

![image](https://github.com/user-attachments/assets/09737d3a-8ca4-4b01-8863-78758e87e8f8)


Since we verified, we can execute our nullpass.py script against the target DC and IP to exploit and change the account password:

![image](https://github.com/user-attachments/assets/fb0bdad3-df9f-414f-89cd-1abefb9c6d81)


 	What is the Local Administrator's NTLM hash?
In order to retrieve the hashes, we can use secretsdump script to dump all the hashes from the target machine.
Source: https://raw.githubusercontent.com/fortra/impacket/refs/heads/master/examples/secretsdump.py

![image](https://github.com/user-attachments/assets/713e9108-c6cd-41ae-8a2e-72a2ace0cfd1)


We need to use -just-dc option to extract NTLM hashes of the DC and use -no-pass option to provide null password. Once we run the above mentioned command, we retreive the hashes of the accounts in the DC:

![image](https://github.com/user-attachments/assets/6af0f15a-f455-4db0-b59d-11a5102dcabf)


NTLM hash of the local administrator:

![image](https://github.com/user-attachments/assets/42cbee2d-efc7-4d8c-bc5b-09d3266a8113)


 	How many Domain Admin accounts are there?
![image](https://github.com/user-attachments/assets/71abc65e-c3e2-421a-b4c1-41c94ceaaab8)


![image](https://github.com/user-attachments/assets/a7684437-b2a8-4d85-a94d-dd9260d33974)


As mentioned in the question hint, the domain admin accounts start with a prefix a- highlighted in the above figure.


 	What is the root flag?
![image](https://github.com/user-attachments/assets/aea1c94e-0564-45fb-896d-17591731544c)


In order to gain the root flag, we can use evil-winrm to gain command execution on the target machine. I ran into a few issues running evil-winrm on the provided VM by TryHackMe. I had to switch to my kali machine to execute the process of getting command injection. The target machine needed to be restarted, thus, a different IP is displayed in command line in the figure below:

![image](https://github.com/user-attachments/assets/2446efee-b58e-4e42-bbf7-a0f964cf2d89)


![image](https://github.com/user-attachments/assets/17e0cc3a-a673-4a36-a121-cb16d89cdfa6)
