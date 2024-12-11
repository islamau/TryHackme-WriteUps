### Task 2: Dive into the data

![image](https://github.com/user-attachments/assets/24ff28e3-54b2-492f-949f-2e74e07aa70e)

I used the metadata command provided in the task:

![image](https://github.com/user-attachments/assets/15d936be-cd58-4f2a-97c7-48fd1bb72f11)

I received 103 results, with each source type's metadata such as first and last time of event trigger, and total count of the events of each source type.

### Task 3: 100 series questions

![image](https://github.com/user-attachments/assets/81077035-c03e-484e-875d-572cc7cdd7e5)

    Amber Turing was hoping for Frothly to be acquired by a potential competitor which fell through, 
    but visited their website to find contact information for their executive team. 
    What is the website domain that she visited?

First, I needed to find out amber's IP address:

![image](https://github.com/user-attachments/assets/cd413230-d946-4b67-bc73-b0ad8e05622c)

![image](https://github.com/user-attachments/assets/1bbb6ef2-5b81-40b2-bb02-fe54a7b0380b)

![image](https://github.com/user-attachments/assets/039eccad-7d44-4c36-b1fd-5ba5c27b29a0)

Now that I have amber's IP address, I needed to find the sites amber has visited:

![image](https://github.com/user-attachments/assets/d85c2ef7-bb70-4ce8-8bd7-d6874f931cda)

The above command extracts all the events with source type as HTTP upsteam traffic, with status code 200 and which will only display the unique site values in a table format.

![image](https://github.com/user-attachments/assets/2082cb2f-6c18-4f95-bec6-dafc7df528b4)

Narrowing down the search and knowing that Amber looked for a company which is in the similar industry Amber works for, I could determine that she visited the website "www.berkbeer.com".

    Amber found the executive contact information and sent him an email. 
    What image file displayed the executive's contact information? Answer example: /path/image.ext
    
![image](https://github.com/user-attachments/assets/36aa410a-05da-4774-a96d-92d65eadfb1e)

From the above query, I received a result set that can help see all the path accessed in the the uri_path field. From the refined result, I noticed that the file /images/ceoberk.png had the CEO's information.

    What is the CEO's name? Provide the first and last name.
    What is the CEO's email address?

Now I needed to shift our focus to looking at smtp traffic. Looking at the events, I could find Amber's email address which I could use to narrow down our search to find the rest of the information about the CEO.

![image](https://github.com/user-attachments/assets/1f6a8fcf-f786-4633-b541-379bbbae7ee3)

![image](https://github.com/user-attachments/assets/b61514ae-7a19-4cb0-bc5c-619e72e79f01)

![image](https://github.com/user-attachments/assets/2237d0ef-7e0e-4677-8d01-76612c17da1b)

Looking at one of the email traffic contents, I can determine the CEO's name Martin Berk and his email address as well.

![image](https://github.com/user-attachments/assets/625b3ec4-7d44-4717-89f8-32438e4c3e5c)

    After the initial contact with the CEO, Amber contacted another employee at this competitor. 
    What is that employee's email address?
    
Going back to the original search query, where I was looking for smtp traffics with amber's email in the query string to get refined search results. Looking at the events, I can determine the email address of the other employee at the same company, since I already knew the domain of the company's email address.

![image](https://github.com/user-attachments/assets/0192aa33-6fbf-46ba-b4a8-372806ee7e82)

![image](https://github.com/user-attachments/assets/a0b823a5-0f2a-43d7-a1a4-b9185bb85081)

![image](https://github.com/user-attachments/assets/1eac919f-9d9b-44e8-a77b-52ab82c204fe)

    What is the name of the file attachment that Amber sent to a contact at the competitor?

Selecting <attach_filename> from the additional fileds on splunk, I could easily find the name of the file attachment that Amber sent to the contact at the competitor.

![image](https://github.com/user-attachments/assets/38eb9839-d751-4985-b769-bf97dac38e6f)

    What is Amber's personal email address?
    
To find Amber's personal email address, I looked at the content body of the email that she sent to the other employer at berkbeer. I used this query to refine our search:

![image](https://github.com/user-attachments/assets/db11cbe0-247c-47ff-b38b-8e9b28817a81)

Here, I found an encoded message inside the content body:

![image](https://github.com/user-attachments/assets/981a46ed-153e-41bf-89a7-3b13a842b33e)

Using CyberChef to decode base64 message, I could determine Amber's personal email address:

![image](https://github.com/user-attachments/assets/ea2ad08d-244a-4e92-8670-bc7527261f5e)


### Task4: 200 series questions

    What version of TOR Browser did Amber install to obfuscate her web browsing? 
    Answer guidance: Numeric with one or more delimiter.

![image](https://github.com/user-attachments/assets/dcc1bb7a-a734-4bbe-984d-4d5cd28615d5)

![image](https://github.com/user-attachments/assets/34dc86ff-db6c-47c3-839e-8cb8571277ed)

To find out the version of the browser, I can use keyword search using keywords such as amber, tor and profile to find out the location where the tor browser executable was downloaded.

    What is the public IPv4 address of the server running www.brewertalk.com?
    
![image](https://github.com/user-attachments/assets/7cfd2bcb-0590-482c-97c0-fca5276a58e1)

![image](https://github.com/user-attachments/assets/7b4ac192-1518-48c3-bc19-01761a834b30)

If I run a query using just the name of the website as a keyword and hover over destination IP field on the left pane of splunk, a PUBLIC IP address should stand out which is <52.42.208.228>.

    Provide the IP address of the system used to run a web vulnerability scan against www.brewertalk.com.

![image](https://github.com/user-attachments/assets/2e674460-9caa-4c78-9fa9-e33743351618)

Hoveing over the source IP field, I could to notice an IP address with a huge number of event counts, that is the IP address <45.77.65.211> which sourced the vulnerability scan.

    The IP address from public IPv4 is also being used by a likely different piece of software to attack a URI path. 
    What is the URI path? Answer guidance: Include the leading forward slash in your answer. 
    Do not include the query string or other parts of the URI. Answer example: /phpinfo.php

![image](https://github.com/user-attachments/assets/2fef3b75-495f-4974-a226-b408e89766e4)

![image](https://github.com/user-attachments/assets/ee3d922e-5e1a-43a8-9536-a858f6894bda)

Running a query with the public IP address of breweretalk as a keyword, I noticed member.php file to be the target.

    What SQL function is being abused on the URI path from the previous question?

First, I ran the following query, where I specified the vulnerability scanner's IP and the target URI path on the taget system:

![image](https://github.com/user-attachments/assets/d593121a-99b8-4d8d-b8e4-eced7c5c83fa)

Looking at the form_data field, I noticed the payloads that ran against the victim, which includes the SQL function "updatexml" used in the payload.

![image](https://github.com/user-attachments/assets/5744c7d5-61a9-47a6-b754-0e26c83a60ed)

![image](https://github.com/user-attachments/assets/1e38f488-3326-42d5-a866-2e9bc27a77bf)

    What was the value of the cookie that Kevin's browser transmitted to the malicious URL as part of an XSS attack? 
    Answer guidance: All digits. Not the cookie name or symbols like an equal sign.

![image](https://github.com/user-attachments/assets/23fa9187-f240-459d-8ac0-59248b13428e)

![image](https://github.com/user-attachments/assets/84833214-9cf2-48b7-ab3d-eab19efe8e69)

I looked at the cookie fields that were associated with Kevin's device. Cookie #1502408189 has the source IP of kevin's public IP, validating that this was the cookie sent to the scanner site.

    What brewertalk.com username was maliciously created by a spear phishing attack?

![image](https://github.com/user-attachments/assets/d161bf78-43e8-4e70-becb-ff725234b8e9)

![image](https://github.com/user-attachments/assets/f03d9a3a-66ed-4033-9533-7956a4504db4)

![image](https://github.com/user-attachments/assets/48c6d13c-20e0-4af4-8277-ca62adf0fdbf)

By querying using the CSRF token that was given in the hint, we can get the username "kIagerfield" from the form_data field values.

### Task 5: 300 series questions

    Mallory's critical PowerPoint presentation on her MacBook gets encrypted by ransomware 
    on August 18. What is the name of this file after it was encrypted?

![image](https://github.com/user-attachments/assets/b8f2ae4c-233c-4645-82b9-7d0886968744)

![image](https://github.com/user-attachments/assets/5578591f-997a-4c6d-8441-0337a92c9e74)

![image](https://github.com/user-attachments/assets/5423761f-10bc-4615-935b-096438c48129)

![image](https://github.com/user-attachments/assets/48675de9-af60-47ed-82a3-92b457e6c007)

I began this task by finding information about Mallory, such as her Macbook's name which was in the host field. I used the name of the host and used PowerPoint extensions as keyword to refine our result. Then, I looked at the target_path to find the name of the PowerPoint file that was encrypted for ransomware.

    There is a Games of Thrones movie file that was encrypted as well. What season and episode is it? 

![image](https://github.com/user-attachments/assets/4cbb8eff-7039-483c-ba34-63c6417f7e52)

![image](https://github.com/user-attachments/assets/66cebf1d-8b82-43f2-99f2-0b194f2172e8)

To find the encrypted file name, I used the extension of an encrypted file to sort and find our answer.

    Kevin Lagerfield used a USB drive to move malware onto kutekitten, Mallory's personal MacBook. 
    She ran the malware, which obfuscates itself during execution. 
    Provide the vendor name of the USB drive Kevin likely used. Answer Guidance: 
    Use time correlation to identify the USB drive.

![image](https://github.com/user-attachments/assets/3e5d01e6-1dc2-4e54-904a-07dee87cec46)

![image](https://github.com/user-attachments/assets/ce81b238-48eb-40fe-a1fb-b69e29175fd1)

![image](https://github.com/user-attachments/assets/76a21fc7-c0e1-46c7-8d23-0ffdd3d51860)

I used the name of the computer as well as the eventype to begin my search, which le me to the name of devices that were connected to the computer. That lead me to the vendor ID which I used to find the name of the vendor which is Alcor Micro Corp.

    What programming language is at least part of the malware from the question above written in?

![image](https://github.com/user-attachments/assets/617a0a7f-cd7d-403d-b992-df07443ebeac)

![image](https://github.com/user-attachments/assets/ed0bb0c6-9184-4c6e-ac9f-5cb39ab3f06a)

![image](https://github.com/user-attachments/assets/d7c70c9e-a79d-4f9a-ae51-cfac0e4b9ea6)

I kept looking through the logs and interesting fields, which led to the columns.md5 field. Running the hash on virustotal, I figured out the language that was used to write the program.

    When was this malware first seen in the wild? Answer Guidance: YYYY-MM-DD

![image](https://github.com/user-attachments/assets/d518ac35-3ec6-4094-aeb7-6c5e1dfd0ed9)

    The malware infecting kutekitten uses dynamic DNS destinations to communicate with 
    two C&C servers shortly after installation. What is the fully-qualified 
    domain name (FQDN) of the first (alphabetically) of these destinations?

![image](https://github.com/user-attachments/assets/fc6e0801-7cbe-49d7-95cf-c061dcc232df)

    From the question above, what is the fully-qualified domain name (FQDN) 
    of the second (alphabetically) contacted C&C server?

![image](https://github.com/user-attachments/assets/bef02ed3-f315-4ae4-b2bd-d8a8d48b8198)

### Task 6: 400 series questions

    A Federal law enforcement agency reports that Taedonggang often spear phishes its victims with 
    zip files that have to be opened with a password. What is the name of the attachment sent to 
    Frothly by a malicious Taedonggang actor?

![image](https://github.com/user-attachments/assets/67be0bd7-7761-4ef1-8461-292aabc6f2c4)

![image](https://github.com/user-attachments/assets/7ef58429-af79-486d-8149-d91020e90c23)

Running a query on finding events related to emails and .zip extension, I can easily find the name of the attachment in the attach_filename field.

    What is the password to open the zip file?

![image](https://github.com/user-attachments/assets/a6bb8be9-1dcb-48af-9e5d-c945bbd3b5f4)

I went through the events and tried to thoroughly read the email content, which is where I found the password to the encrypted zip file attachment.

    The Taedonggang APT group encrypts most of their traffic with SSL. 
    What is the "SSL Issuer" that they use for the majority of their traffic? 
    Answer guidance: Copy the field exactly, including spaces.

![image](https://github.com/user-attachments/assets/61cff19d-f53e-4788-8aed-e61018254576)

![image](https://github.com/user-attachments/assets/38e9aa0b-50ce-4395-9caf-aac4e38be632)

Knowing the Scanner/"Attacker"s IP address from a previous task, I used the IP address against TCP connections to find the SSL issuer.

    What unusual file (for an American company) does winsys32.dll cause to be downloaded into the Frothly environment?

![image](https://github.com/user-attachments/assets/89288c8d-cfa9-43be-9541-f47a183379ca)

![image](https://github.com/user-attachments/assets/09be8404-0106-471c-9039-a73c603cac8f)

![image](https://github.com/user-attachments/assets/50ea6c44-f6b9-4789-af2f-014bf3193084)

![image](https://github.com/user-attachments/assets/083f30d2-2f5b-4590-9cec-0c8191d222de)

To tackle this task, firstly I found the tool which is FTP that was used to download an unsual file. I used the sourcetype as FTP stream and selected method "RETR", which is used to download file on client machine, to return results which gave me the unusual filename.

    What is the first and last name of the poor innocent sap who was implicated in the 
    metadata of the file that executed PowerShell Empire on the first victim's workstation? 
    Answer example: John Smith

Source: https://www.hybrid-analysis.com/sample/d8834aaa5ad6d8ee5ae71e042aca5cab960e73a6827e45339620359633608cf1/598155a67ca3e1449f281ac4

![image](https://github.com/user-attachments/assets/853b4695-3824-4291-9bfd-b4db533adc0c)

    Within the document, what kind of points is mentioned if you found the text?
    
Source: https://app.any.run/tasks/15d17cd6-0eb6-4f52-968d-0f897fd6c3b3

![image](https://github.com/user-attachments/assets/d2b3ca51-1d92-4c17-97fe-2be486ecd6b8)

    To maintain persistence in the Frothly network, Taedonggang APT configured several 
    Scheduled Tasks to beacon back to their C2 server. What single webpage is most contacted 
    by these Scheduled Tasks? Answer example: index.php or images.html

![image](https://github.com/user-attachments/assets/db763909-8e6f-46e5-a9a2-4ae59296dc7b)

![image](https://github.com/user-attachments/assets/018e2e7f-c4a0-4b03-8550-6fd761693624)

![image](https://github.com/user-attachments/assets/cca9f353-6f1f-45ae-b577-a1d3eea6da4a)

![image](https://github.com/user-attachments/assets/1bc9ae9c-a1ae-4016-8b64-a2c1a4d725be)

![image](https://github.com/user-attachments/assets/6d67583b-2c74-4b19-8f68-922f200cfd13)

![image](https://github.com/user-attachments/assets/7f7ab38c-3868-4969-8c74-16d97d7551c4)

I started this task by looking at all the scheduled tasks in the dataset. In the result of the command line values, I noticed 3 commands that were executed to schedule tasks. which gave me the path in the HKLM registry where the script is stored. Looking at the registry location, I found 4 events, each having base64 encoded data. Going through the base64 decoding, I determined the contacted webpage is called process.php.
