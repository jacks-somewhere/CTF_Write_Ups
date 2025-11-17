# Task 6- OSINT 1
Category: OSINT

Points: 30

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
“Great work on uncovering that suspicious subdomain, Hexline. However, your work here isn’t done yet, we believe there is more.”

# Solve

Taking another look at solstice-tech1, I went back to their staging-panel repo. From there, I went back to SanTzu’s uplink-config repo.

![Screenshot 2025-06-27 121423](https://github.com/user-attachments/assets/b935ebd8-8e6e-40b3-b263-c7e25ab9b4c1)

Getting stuck, I asked ChatGPT for help. I inputted both the html from the staging-panel website and the init.js. It decoded the token (JBSWY3DPEBLW64TMMQQQ==) from Base 32 to “hello world” and provided some next steps that I could attempt to find the flag. 

Decoding the token for myself in CyberChef from Base 32 showed the token actually said “Hello World!”, which still was not useful.  

Going back to https://stage0.virelia-water.it.com/ I looked for anywhere I could edit the DNS, session_id, token, or cookie. Not being able to find anything, I tried capturing packets with BurpSuite. Looking at the packets, there where no place to pass any of the information found in the init.js file.

Trying to add the session_id onto the end of the url did not work either. 
- stage0.virelia-water.it.com/O-TX-11-403
- virelia-water.it.com/O-TX-11-403

Taking a look into the DNS from SanTzu's init.js did not lead anywhere. Trying to input it into the browser did not work and looking it up with Nslookup.io did not reveal any information. At this point, I had to take a break at from this problem and come back to it.

My teammate also tried similar things and could not find anything new.

### The next day: 11:03 PM

I decided to take another look at this as my machines were busy running a grep search. Searching back though the Github repos, I looked that the fallback DNS from SanTzu's init.js again. 

I copyed the fallback_dns into Google and found a website called whoisfreaks.com. 
- https://whoisfreaks.com/tools/dns/lookup/uplink-fallback.virelia-water.it.com

![Screenshot 2025-06-28 230338](https://github.com/user-attachments/assets/02331bde-a499-4cc4-8a32-a3d371e384b1)

This pulled up a long string of text. Dumping into CyberChef revealed the flag.

# Flag
THM{uplink_channel_confirmed}


