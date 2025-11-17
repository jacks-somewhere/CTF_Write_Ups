# Screamin' Streamin' 😱
Category: Recon

Points: 200

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
We've received intel that Juche Jaguar has exposed a network stream on the host 34.85.185.78 between TCP ports 5000 and 10000. Once you find the port, connect to the correct stream name and report back with a flag.

Find the network stream and get the flag!

Hint (-50 points)

The open port uses RTSP. Once the port is found, you will need the correct stream name.

You will need to enumerate the stream name through some type of brute forcing. Use tools like ffprobe to help find the correct stream name in order to connect to it with a tool such as VLC.

# Solve
The first step was to run a Nmap scan to try and find a port to connect to. Running the scans showed that port 8774/TCP was open but the service was unknown.

> nmap -p 5000-10000 -T4 34.85.185.78

> nmap -sV -p 8774 34.85.185.78

![Screenshot 2025-06-14 153739](https://github.com/user-attachments/assets/f2c77134-8b62-42ab-a164-8517824fdee9)

Next, I tried connect via telnet and netcat. The connections were successful but they would not respond to any input.

> telnet 34.85.185.78 8774

> nc 34.85.185.78 8774

![Screenshot 2025-06-14 154203](https://github.com/user-attachments/assets/d579bc52-e8bb-4bc6-8c38-5e42e5edd203)

At this point I was stuck so I bought the hint.

---

Hint:

The open port uses RTSP. Once the port is found, you will need the correct stream name.

You will need to enumerate the stream name through some type of brute forcing. Use tools like ffprobe to help find the correct stream name in order to connect to it with a tool such as VLC.

---

After inputting the Challange and hint to ChatGPT, it walked me though the next steps in order to connect to the stream.

First it had me create a text file called streams.txt

```
cat << EOF > streams.txt
juche
juche_jaguar
jaguar
power
stream
video
live
test
flag
EOF
```

Next, it had me run a loop in the terminal that tried every word in the list created above. the goal was to see if there were any responses that would indicated that there was a connection or the word was right.

```
for stream in juche juche_jaguar jaguar power video stream test; do
    echo "Trying stream: $stream"
    ffprobe rtsp://34.85.185.78:8774/$stream
done
```

After running the loop, I got error 404 for every attempted connection except for 1, stream.

![Screenshot 2025-06-14 160626](https://github.com/user-attachments/assets/8c3f8493-864f-4de3-acc1-3513d73cf113)

I took the output and plugged it into ChatGPT to confirm that ‘stream’ was the word that I was looking for. The next thing to do was to try and connect to the stream. I asked ChatGPT what commands to run next.

In the loop above I tried to connect with ffprobe but the connection failed. I then tried vlc and ffplay.

> vlc rtsp://34.85.185.78:8774/stream

> ffplay rtsp://34.85.185.78:8774/stream

ffplay was able to finally pull up the stream! It was a looping video of a man holding a piece of paper with the flag on it. 

![image(1)](https://github.com/user-attachments/assets/de7ffc9b-6710-459b-bba7-449049e23d5e)

This image was posted to Official DoD Challenge Slack Channel 02-need-help by Challenge Dev Chris Haller.

# Flag
C1{RTSP_you_found_me}
