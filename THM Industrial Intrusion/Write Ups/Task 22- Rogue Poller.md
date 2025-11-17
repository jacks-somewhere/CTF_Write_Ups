# Task 22- Rogue Poller
Category: Networking

Points: 15

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
An intruder has breached the internal OT network and systematically probed industrial devices for sensitive data. Network captures reveal unusual traffic from a suspicious host scanning PLC memory over TCP port 502.

Analyse the provided PCAP and uncover what data the attacker retrieved during their register scans.

Provided Files: rogue-poller.pcap

# Solve

I downloaded the packet and took a look at the stream. 
- Right clicked on 1 of the packets and followed the TCP stream
- Filtered by data sent from the server to the attacker
- Selected show in ACSII 
- Typed out Flag and submitted it

![Screenshot 2025-06-27 200629](https://github.com/user-attachments/assets/b57db758-c39a-42d8-9f6b-b6026107d6ae)

# Flag

THM{1nDu5tr14L_r3g1st3rs}


