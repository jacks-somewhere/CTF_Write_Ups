# D7: Endpoints and Exfiltration

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
In D5, we identified the backup server that is the source of the transfer, and the IP address that the threat actor is possibly sending data to. Now the question is, what software on the backup server is responsible for the exfiltration?

Luckily, InfoSec has identified this backup server as one that stores highly sensitive data, and have endpoint agents installed on the server that have been monitoring its activities. The other incident responders queried the data gathered about this host for the timeframe of the suspected exfiltration, and have given you a set of files that may shed some light on the situation. The data files you've been given contain the outputs of shell commands run directly on the endpoint. You'll be examining the outputs of the commands "lsof", "ps", and "history".

### Objectives  
Your task is to identify the OS process, user, and software that is performing the exfiltration, and where the software came from. Along the way, you may notice a sneaky tactic that the attacker used to attempt to conceal the software he was using. Let what you found out from the PCAP challenge lead you to the needle in the haystack!

### Flag format
To build the flag, you'll need...
- the username on the backup server that is running the exfil proocess (USER)
- the name of the executable file that actually created the exfil process (FILE)
- the process ID (PID) of the process performing the exfiltration
The format of the flag will be...

USER_FILE_PID

# Solve
I knew the IP DNS was most likely sending the information too so I did a search for “251.91.13.37”.
-	Found process and user in lsof.txt
-	Found process in ps.txt and got file name
-	Found file in bash-history.txt and original file

<img width="1415" height="812" alt="Screenshot 2025-07-07 122635" src="https://github.com/user-attachments/assets/f3f7dcf6-07a7-4bb5-8311-9b364f7a1019" />

<img width="1423" height="819" alt="Screenshot 2025-07-07 122649" src="https://github.com/user-attachments/assets/af2c190f-2440-4f07-9053-d249b1001ede" />

<img width="1418" height="815" alt="Screenshot 2025-07-07 122710" src="https://github.com/user-attachments/assets/babab16a-f195-4d60-95e1-8c33ed4b9abb" />

# Flag

backupsys_jot_64866, backupsys_backup_64866
