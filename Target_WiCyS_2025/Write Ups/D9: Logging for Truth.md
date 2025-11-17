# D9: Logging for Truth 

Points: 300

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
Logging for Truth

So now we know how the data was exfiltrated - a shady commit in a GitHub repo. And, going by the reference logs, it looks like Erik is responsible!

But Erik is the developer who gave us the compromised repository - and he made all the commits in the log. So is he really bad at covering his tracks? Or is he being framed?

We could use some proof...

Luckily for us, GitHub keeps logs of all actions users do on the codebase - which is pretty helpful for situations like this! Personalyz imports the logs from GitHub and stores them in our log dashboard Insightful Horizon, so that's where you're headed now.

Unfortunately, Erik didn't tell you which repository that .git directory came from, and he's been out of office and unreachable for the last few days. So you've got the audit logs for all the repositories he's worked on in the last six months to sift through to try and figure out what really happened here.

### Objectives  
Into the audit logs! Head over to the Insightful Horizon log dashboard at one of these servers:
- https://target1.chals.io
- https://target2.chals.io
- https://target3.chals.io

You'll want to use the audit-logs index for this challenge.

Dig deep and find the evidence - who really added that malicious code to the application?

Once you think you have a solid case, use the IP address of the insider as the flag.

### Flag format
###.###.###.###

# Solve
If 'elesiuta' is the name the change was uploaded under then when does he not upload under his normal ip?

I Filtered for 'elesiuta' and filtered out his normal IP address.

<img width="1919" height="859" alt="Screenshot 2025-07-30 230210" src="https://github.com/user-attachments/assets/87e02038-e467-442b-8113-1234d0192ec9" />

His normal IP was 192.168.1.42 and the only other value was 241.17.22.80

# Flag
241.17.22.80
