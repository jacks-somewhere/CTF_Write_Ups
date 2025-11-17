# Field Reports Mayhem
Category: Web Security

Points: 150

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
We've gained access to the Juche Jaguar’s Field Reports archive through an operative's use of weak credentials. Upon logging in, the operative sees their previous field reports and can file new ones. Somewhere in here, I am sure some 'leet' agent stashed the Supreme Leader's secret pizza discount code!

Log in to the portal at: http://35.245.106.190/login.html

Use the credentials: 1234:spudpotato

Hint 1 (-25 points)

Figure out what IDOR is and why it is relevant.

Hint 2 (-25 points)

That "leet" agent probably has a leetspeak ID

# Solve
Logging into the site brought me to a page where I could view different reports from my agent ‘1234’.

The first thing that I checked was the different reports to see what was there and what changed in the URL. The reports did not provide much information; they mostly talked about food that the agent ate. 

Something did catch my eye though, “You are viewing reports for Agent 1234. (Your ID: 1234)”.

![Screenshot 2025-06-14 162633](https://github.com/user-attachments/assets/a09ec5ea-4420-45e3-bae9-7e16cd414c9a)


After changing things in the URL such as the agent_id and report code without sucess I bought the first hint.

---
Hint 1

Figure out what IDOR is and why it is relevant.

---

Acourding to Port Swigger an Insecure direct object reference or IDOR is a type of access control vulnerability that happens when a user is able to supply input to an object directly. 

I opened up Burp Suite to see what I could capture about the login.

Loggin back into the portal using the provided information I caught the POST login packets.

I tried first tried to change the agent_id in the packet to 125512 (‘leet’ alphabet letter location). This returned the error agent id or password was wrong. Next, I tried agent id 1234 and ‘spudpotat’ and got the same error. This showed me that I had no way of checking to see if the agent_id existed.

Running out of ideas again I bought the next hint.

---

Hint 2

That "leet" agent probably has a leetspeak ID

---

According to How To Geek leetspeak that uses similar looking numbers or symobols to replaces English letters.

Asking ChatGPT to help me, it had me try the leetspeak ID of 'leet'. Plugging '1337' into the URL while logged in as agent 1234 brough up a new dashboard.

![Screenshot 2025-06-14 171218](https://github.com/user-attachments/assets/c96b38b7-2d48-426b-9c29-4f698b8976e1

By clicking though the reports I found the flag.

# Flag
C1:{IDOR_F13LD_R3PORT)

