# Task 15- Chess Industry
Category: boot2root

Points: 15*

*Only 7.5 pts where earned due to only find 1 of 2 flags.

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
"NullRook prowls a smart chessboard hub where automation meets strategy. In the digital workshop, subtle flaws in the robot interface threaten to tip the balance of play."

<Target ip>


# Solve

Note: I ran out of time on my machines several times while working on this so the target IP does change! This challange does NOT involve working with multible IPs, ONLY 1.

### Flag 1
The first thing I did was input the provided IP into a browser and got the chess website.

![Screenshot 2025-06-28 150925](https://github.com/user-attachments/assets/47868900-e202-4b9a-b951-9fdbaf75ce7e)

Next, I run an nmap scan on the IP.

```
nmap <ip> 
```

| PORT | STATE SERVICE |
| --- | --- |
| 22/tcp open | ssh |
| 79/tcp open | finger |
| 80/tcp open | http |

After trying without success to connect via SSH, I tried connecting to finger via netcat.

```
netcat <ip> 79
```

Inputting names from the website showed some new information.
- admin- no information
- Magnus- no information
- magnus- Logged in
- fabiano- Logged in
- hikaru- Logged in
- user- Logged in

![Screenshot 2025-06-28 151658](https://github.com/user-attachments/assets/5e7ffe71-66a2-4441-aff6-3644b13c6a14)

![Screenshot 2025-06-28 161320](https://github.com/user-attachments/assets/ad54d7b1-dcc9-4d29-8c1c-9791fc01406f)

![Screenshot 2025-06-28 161601](https://github.com/user-attachments/assets/7d648009-4710-4230-b3b8-8c1c8009b0ea)

When I tried fabiano, it outputted a string under ‘Plan:’
- ZmFiaWFubzpvM2pWVGt0YXJHUUkwN3E=

Inputted the string into CyberChef and decoded from base64.
- Result: fabiano:o3jVTktarGQI07q

Trying to decode the result further with CyberChef and Dcode did not work.

After trying some stuff that did not lead anywhere, I decided to check the code from Fabiano again. Looking at the decrypted base64 code again, I realized that it might be a ssh username and password.

Running SSH and inputting ‘o3jVTktarGQI07q’ as the password worked!!!

```
ssh fabiano@<target IP>
```

![Screenshot 2025-06-28 163011](https://github.com/user-attachments/assets/9ed24295-bfce-49c8-8b91-9ff4f4901134)

Running ls showed the only file was user.txt. Running ‘cat user.txt’ got me the flag.

### Flag 2

While SSH into fabiano's account I checked for hidden files. I found that I could access magnus and hikaru's accounts and look though them. They did not have any files that I could see however. Running grep for charaters like "THM{" did not result in anything.

Netcating back into hikaru's account on port 79, I reviewed the information there. I was not able to make any progress with it though.

# Flag

### Flag 1
THM{bishop_to_c4_check}

### Flag 2
MISSING



