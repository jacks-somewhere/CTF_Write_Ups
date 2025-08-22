# D8: Shadow Commit

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
We've identified the piece of software that's responsible for the exfiltration, and it's one of Personalyz.io's internally developed apps... that's not good. We reach out to the developer of the software and they quickly report back that their repository was compromised. Looks like all we received was a .git directory—no source files, no README, just the version history.

Somewhere in the commit log, a change was made that allowed the threat actor to use it to exfiltrate data. Your task is to uncover the commit ID of that shady operation and identify the malicious IPv4 address.

### Objectives  
Find the commit hash where the malicious change was introduced and obtain the malicious IPv4 address.

### Flag format
###.###.###.###

### Given
shadow.zip (git file)

# Solve
Knowing that I was looking for an IP address, I ran the  grep command on the shadow.zip file.

```
grep -r “[0-9][0-9].[0-9] [0-9] [0-9].”
```

```
grep -rEo '[0-9]{1,3}(\.[0-9]{1,3}){3}'
```

When grep did not work, I decided to enter the IP from the previous challenge. And it worked! (I did talk with the Target Team about this challenge and they said that it was an small oversite that worked out in my favor thankfully.)

# Flag
251.91.13.37
