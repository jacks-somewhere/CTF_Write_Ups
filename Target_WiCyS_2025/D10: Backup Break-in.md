# D10: Backup Break-in

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
### Introduction

At this point, you're pretty sure someone made a malicious commit to the Git repo, causing the data exfiltration. The goal of this step is to figure out how the attacker got the credentials of the Git committer.
To start, note down the username of the Git committer from "Shadow Commit." That person's password will be the flag for this assignment.

### Objectives  
As part of your forensics, you've been given access to Personalyze.io's backup server, which has a full copy of all the data from their company server.

First, find out how to log into the backup server: target-securevault.chals.io

Once you're logged in, you can download all the files from Personalyze. It's about 50 MB.

Next, search through the files for the leaked credentials. They're in there! And you'll find out how the attacker could have obtained them...

### Flag format
The flag for this challenge is the password for the credentials that you found. (Only the password - no username.)

It starts with "wicys".

# Solve
Following the provided link led to a web portal. In order to get into the website I had to find the password.

I checked the HTML and found the password in Base64.

Website password: WiCys_SecureVault_Challenge_2025!

I download the file and clicked though the files.

I came across a .zip called slack_archive and opened it.

I ran a grep command to try and locate the flag.

```
Grep -rie ‘password’
```

The only result led me to the password!

‘@elesiuta hey, that header includes a password — can you delete that real quick and DM it if needed?",’

Following the conversation, I found the password encoded in Base64.

<img width="1919" height="967" alt="Screenshot 2025-07-31 041642" src="https://github.com/user-attachments/assets/6bbacd1a-aa07-4f33-80f7-9757b0100d9f" />

<img width="1847" height="903" alt="Screenshot 2025-07-31 041629" src="https://github.com/user-attachments/assets/e3627bc5-a2a0-437e-b72e-3b6b7181c470" />

Decodes to eslesiuta:wicys_slack_flag_2025!

# Flag
wicys_slack_flag_2025!
