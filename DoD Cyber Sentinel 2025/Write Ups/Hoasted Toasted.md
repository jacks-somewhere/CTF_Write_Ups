# Hoasted Toasted
Category: Recon

Points: 150

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

## Question 
We have discovered what we believe is a North Torbian public website and have suspicions there is a secret internal-only site hidden there as well. Figure out how to connect to the hidden site and find the flag!

The sites is at https://not-torbian.ethtrader-ai.com/

Hint (-25 points)

Pay attention to the TLS certificate. Are there other hostnames on there? This may indicate Host-header injection vulnerabilities.

# Solve
Based on the wording of the question, my first thought was to try and fuzz the website. To do this I chose to use ffuf.

The first thing that I ran was ffuf --help to review the syntax for the tool.

After reviewing the syntax, I ran a few commands that did not work (see Note below):

> ffuf -u https://not-torbian.ethtrader-ai.com/
- Missing wordlist and "FUZZ"

> ffuf -w -u https://not-torbian.ethtrader-ai.com/
- Missing wordlist and "FUZZ"

> ffuf -w /usr/share/seclists/ -u https://not-torbian.ethtrader-ai.com/ 
- Missing wordlist and "FUZZ"

> ffuf -w /usr/share/seclists/Discovery/Web-Content/ -u https://not-torbian.ethtrader-ai.com/FUZZ
- Missing wordlist

At this point in time, I asked ChatGPT for help:

> ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u https://not-torbian.ethtrader-ai.com/FUZZ    
- found: index.html

> ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -u https://not-torbian.ethtrader-ai.com/FUZZ

---

### Note
Why where the first 4 commands wrong? I did not take to the time to fully understand or process what was required to run this tool. That is clearly reflected in my attempts.

Missing "FUZZ"

ffuf requires that the word "FUZZ" is in the provided URL. This indicates where ffuf can insert words from the wordlist.

Missing wordlist

ffuf requires a wordlist to run.

---

Nothing came of these commands except for index.html. Going to https://not-torbian.ethtrader-ai.com/index.html brought up a new page.

![Screenshot 2025-06-14 124046](https://github.com/user-attachments/assets/9d58072d-10cf-470b-a216-c535be105b48)

After going to this page I got stuck so I paid the 25 points for a hint.

Hint:

Pay attention to the TLS certificate. Are there other hostnames on there? This may indicate Host-header injection vulnerabilities.

Going back to the website I looked at the cert:

![Screenshot 2025-06-14 124357](https://github.com/user-attachments/assets/4799600b-3d08-437c-9649-608efd289cb3)

The only other domain was definitelynotaflag.north.torbia. Looking up “Host-header injection vulnerabilities” led to https://portswigger.net/web-security/host-header/exploiting. 

Using the information for the article, I opened Burp Suite and launched browser. I plugged in https://not-torbian.ethtrader-ai.com/ and sent captured packet to the repeater. In the repeater, I changed the host to definitelynotaflag.north.torbia and sent it as a request.

Scrolling though the HTML response gave me the flag.

![Screenshot 2025-06-14 125413](https://github.com/user-attachments/assets/55608845-baa6-4f95-b3ff-1a382c63e5b6)

# Flag
C1{vH0st_S4n_M4g1c_R3ve4l3d}
