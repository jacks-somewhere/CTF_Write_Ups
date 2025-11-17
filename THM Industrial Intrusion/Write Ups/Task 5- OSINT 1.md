# Task 5- OSINT 1
Category: OSINT

Points: 15

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
“Hexline, we need your help investigating the phishing attack from 3 months ago. We believe the threat actor managed to hijack our domain (virelia-water.it.com) and used it to host some of their infrastructure at the time. Use your OSINT skills to find information about the infrastructure they used during their campaign.”

# Solve
The first thing I did was check https://virelia-water.it.com/ for anything useful, there was nothing.

Next, I tried to go to https://virelia-water.it.com/robots.txt and found and error 404 from GitHub.
-	The site is hosted by github, so there must be a version history

![Screenshot 2025-06-27 113708](https://github.com/user-attachments/assets/2d91ae2b-ff93-4714-b00e-79a4d5fb930b)

Heading over to GitHub, I searched for “virelia-water.it.com”.

![Screenshot 2025-06-27 114044](https://github.com/user-attachments/assets/c7d4849c-65d7-4cf6-8bf4-56de34938a9e)

The search brought up 3 accounts, virelia-water, solstice-tech1, and SanTzu. Clicking on the virelia-water account first, I checked out their repos.
- https://github.com/virelia-water

![Screenshot 2025-06-27 114311](https://github.com/user-attachments/assets/f1fecb47-86d5-4eb1-906d-2164c8041c89)

Solstics-tech1 showed they had a repo that also had changes that where related to the website around the same time as virelia-water’s repo.
- https://github.com/solstice-tech1/ot-auth-mirror/commits/main/

![Screenshot 2025-06-27 114204](https://github.com/user-attachments/assets/9ae15187-d2a8-4620-bf66-30f7bdccffd8)

Looking though the ot-auth-mirror repo first, I opened index.html. It was html code for a redirect to a new page created by the attacker (solstice-tech1). 
- Hint: this was important later on

![Screenshot 2025-06-27 114442](https://github.com/user-attachments/assets/2e51df6d-26f9-4959-9a8d-bbe740dca0ca)

Checking out their other repo staging-panel and then the CNAME file led to another website that I could visit.
- https://stage0.virelia-water.it.com/

![Screenshot 2025-06-27 114946](https://github.com/user-attachments/assets/d834f869-70a4-4b0a-8989-eece645185b1)

Looking at the site’s html on GitHub (https://github.com/solstice-tech1/staging-panel/blob/main/index.html) showed that the operator ID and Control Zone where read only inputs. That means that trying to input or change these values probably was not the way to go.

At the bottom of the index.html code there was a link to a script (https://raw.githubusercontent.com/SanTzu/uplink-config/refs/heads/main/init.js). The user listed in this script was “SanTzu” who was followed by solstice-tech1. In addition, SanTzu showed up in the search for the website on GitHub. I was sure looking into them was part of this CTF.

![Screenshot 2025-06-27 115544](https://github.com/user-attachments/assets/ddc6e021-6815-44b0-9cd7-163560d7f16d)

Following the script link led to a GitHub file.
- https://raw.githubusercontent.com/SanTzu/uplink-config/refs/heads/main/init.js. 

![Screenshot 2025-06-27 121423](https://github.com/user-attachments/assets/b4075161-9eaf-4df6-a7fc-d43d654a8b1a)

Trying to input the fallback_dns link into a web browser in did not yield anything besides server not found. 
Taking another look at the network tab of the dev tools of the https://stage0.virelia-water.it.com/ showed that the init.js script was being queried but was blocked. 

![Screenshot 2025-06-27 121745](https://github.com/user-attachments/assets/ce0dbf08-4c35-4ff5-889e-55455fae0c87)

Reaching a dead end, I went back to THM and looked at the question again and OSINT 2 and 3. 

#### Task 5- OSINT 2 Challange
“Great work on uncovering that suspicious subdomain, Hexline. However, your work here isn’t done yet, we believe there is more.”

I know that I was looking for a subdomain, but I was not on the right track with stage0. After thinking, I thought the answer may be related to the attack vector such as a redirect.

I had seen a redirect in solstice-tech1's index.html so I headed back to it. 
- https://github.com/solstice-tech1/ot-auth-mirror/blob/main/index.html

![Screenshot 2025-06-27 133833](https://github.com/user-attachments/assets/25206ab9-d37c-4ab1-ade5-f2c158a994cf)

url= “https://54484d7b5375357373737d.virelia-water.it.com/reset”

copying the url and pasting it into a browser did not yield anything besides a “server not found”. Feeling defeated, I inputted the whole index.html code into ChatGPT to see if it had any other suggestions that I could try. It took one look at the url said it was hexadecimal and decoded it to “THM{Su5sss}”. 

Hoping over to CyberChef, I verified that it was hexadecimal and that the flag was correct!

# Flag
Thm{contact}

Thm{github}

Thm{stage0}

Thm{uplink}

#### THM{Su5sss} (Correct)



