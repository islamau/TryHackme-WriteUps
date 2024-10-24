	Task 1: Windows 10 Disk Image

![{0F8EC8EB-2B34-4509-A5C8-4241A3F6D7D0}](https://github.com/user-attachments/assets/d9f2143f-206c-46aa-bdb3-2c323995548e)

	What is the MD5 hash of the E01 image?

![image](https://github.com/user-attachments/assets/bf5a0f63-0232-44f4-b5fc-5c7ebe1fa544)

Data Sources Summary window of the disk image shows all the hash values.

![image](https://github.com/user-attachments/assets/a65c27ad-9f8d-4eb6-a26b-8515355b655a)

	What is the computer account name?

![image](https://github.com/user-attachments/assets/33916c6f-1dd5-4fcd-b439-2c47dd698634)

Results > Operating System Information > Source File - SYSTEM > Name

![image](https://github.com/user-attachments/assets/018a46a9-8ab3-4596-84eb-86a697d8ad2e)

	List all the user accounts. (alphabetical order)

![image](https://github.com/user-attachments/assets/9096ce8b-12e8-4141-8f1a-126495b00dac)

Results > Operating System User Account
This Pane gives all the Usernames from the SAM file.
I used ChatGPT to sort the list of names for me in alphabetical order.

![image](https://github.com/user-attachments/assets/bb94f098-d2b5-411f-8b16-c2e0b2f22766)

	Who was the last user to log into the computer?

![image](https://github.com/user-attachments/assets/9dfbd0c7-971e-4ce2-a2ab-96dcdf98bfde)

I set the list of users in descending order by the Date Accessed column to find who logged in last.

![image](https://github.com/user-attachments/assets/06a04801-5d94-49a8-b5c1-7cf3c8833fd6)

	What was the IP address of the computer?

![image](https://github.com/user-attachments/assets/43cd1f92-d16c-473b-9e3e-92def0efdc86)

There's a folder called Look@LAN inside the Program files(x86) folder inside vol3 drive, the file irunin.ini in this folder displays the IP address of the machine.

![image](https://github.com/user-attachments/assets/90a74ada-71b5-44cf-9425-3f8dd84145d5)

	What was the MAC address of the computer? (XX-XX-XX-XX-XX-XX)

![image](https://github.com/user-attachments/assets/f66eea12-575d-4723-acc9-9cb836cf25c1)

The answer is in the same location as the previous question, the value LANNIC needs to be looked at.

![image](https://github.com/user-attachments/assets/73376094-a80d-429a-be99-53ac9dad22c2)

	What is the name of the network card on this computer?

I struggled to answer this question as this marked Application tab was not visible to e for some reason. I researched about this issue and found out that a bypass is to change the case name, which I did and was able to solve the issue by enabling the Application tab, which would give valuable information.

![image](https://github.com/user-attachments/assets/9280b5d4-5eb7-4977-b598-7205e3884501)

![image](https://github.com/user-attachments/assets/4727975b-fc7c-4f7c-95cf-10bdfb02b493)

Operating System Information > SOFTWARE > Application tab

![image](https://github.com/user-attachments/assets/46fde0ac-e5b4-4258-b13d-98ed394be70b)

Microsoft > Windows NT > CurrentVersion > NetworkCards > 2 > Description

![image](https://github.com/user-attachments/assets/0bf93c7b-6e6a-4ce6-95bc-645da3d0e8ce)

![image](https://github.com/user-attachments/assets/ec120666-10e5-46b2-9bfc-cce6595255c7)

	What is the name of the network monitoring tool?

![image](https://github.com/user-attachments/assets/a1fdddc9-ea8f-4985-8d54-d1a45c63b757)

![image](https://github.com/user-attachments/assets/4ba25a67-51b7-4ec9-84af-3064d844d189)

Installed Programs > Find and researched about the tool

![image](https://github.com/user-attachments/assets/cb877a6d-e1c7-4619-8b79-4f7caf5bad49)

	A user bookmarked a Google Maps location. What are the coordinates of the location?

![image](https://github.com/user-attachments/assets/90d64c79-63e4-4f51-b7db-7125c697559b)

![image](https://github.com/user-attachments/assets/2ac24b22-cdcb-4514-9f0f-9c3632831fb3)

	A user has his full name printed on his desktop wallpaper. What is the user's full name?

Images/Videos > joshwa > Downloads

![image](https://github.com/user-attachments/assets/e627b974-45c4-45c1-be13-ab56823e104a)

![image](https://github.com/user-attachments/assets/6d7bb073-b727-499f-bb2c-fe42f1bcd22d)

![image](https://github.com/user-attachments/assets/3c881132-6ad9-4084-beb2-3d54d2eb5be0)

	A user had a file on her desktop. It had a flag but she changed the flag using PowerShell. What was the first flag?

Usually a flag is kept in a text. I searched the case file with .txt extension and found ConsoleHost_history.txt.lnk file, which hints out the text file.

![image](https://github.com/user-attachments/assets/72804fb3-38ce-4a72-b555-f4ef55430ec4)

![image](https://github.com/user-attachments/assets/72917118-416f-46cd-afee-92e66b7093ec)

![image](https://github.com/user-attachments/assets/dc154e24-9368-4b9f-92d0-0acff52860b0)

	The same user found an exploit to escalate privileges on the computer. What was the message to the device owner?

![image](https://github.com/user-attachments/assets/e1f3f551-61d1-4ae1-91c9-5b37bd67ec76)

![image](https://github.com/user-attachments/assets/30a89641-009c-46c3-a7c5-fb2371897b2e)


	2 hack tools focused on passwords were found in the system. What are the names of these tools? (alphabetical order)

Searching the "Run Programs" & "Web Downloads", the 2 tools can be found.

![image](https://github.com/user-attachments/assets/dfe9eb19-ea2e-4538-8b58-a401f66bbb21)

![image](https://github.com/user-attachments/assets/f8d9caf4-ae37-4bb6-ad40-03e3e659a219)

![image](https://github.com/user-attachments/assets/81085e1e-f731-4d02-a473-8f9cce1df5fc)

	There is a YARA file on the computer. Inspect the file. What is the name of the author?

![image](https://github.com/user-attachments/assets/844474ea-adff-4838-b783-4978d8cb4225)

![image](https://github.com/user-attachments/assets/b7a3b7eb-566d-4cf3-97a3-5d8134336fee)

I searched the case with the extension .yar to find the yara file.

![image](https://github.com/user-attachments/assets/20089cc4-2d8c-4d13-965b-60c8787e8322)

	One of the users wanted to exploit a domain controller with an MS-NRPC based exploit. What is the filename of the archive that you found? (include the spaces in your answer) 

Searching the web with the exploit name, the name of the vulnerability can be found. I used the name of vulnerability to search within the case to find the file. 

![image](https://github.com/user-attachments/assets/4a05b18f-63ad-40fd-bcee-6fb17c938dc5)

![image](https://github.com/user-attachments/assets/ebb13f86-a969-441e-be07-e7131bcf7d37)

![image](https://github.com/user-attachments/assets/ef1f5b7a-8094-4761-8d9c-ab466856b198)


