# D5: Ahoy, PCAP'n!

Points: 300

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
The threat actor (TA) has contacted us with their demands and now we have some "evidence" of what sensitive data may have been stolen. But how did they get the sensitive data in the first place? And importantly, do we need to worry about them still being active in our environment?

We've received an alert that may be related to this threat actor activity and could clue us in as to where and how they stole the data they are now ransoming. But where exactly are they and what are they doing, besides holding your sensitive data for ransom?
1. Pirating your super-secret client-monitoring software?
2. Stealing your intellectual property or your confidential financial plans for next year?
3. Hijacking your social media feed?
4. Coercing your company systems into acting as a botnet crew for their nefarious purposes?

In the vast ocean of network traffic monitored by the company's Network Security team, you need to find out:
- the compromised machine's name
- and the Command-and-Control (C2) IP address of the threat actor (where they are sending the data to)

The Network Security team has packet captures ("PCAPs") of the company's network traffic around the time of the alert, but due to a tight Information Technology (IT) budget and a lack of resources, it's limited to a small window of time.

Great. Sarcastically send a reminder to yourself to make the IT team "walk the plank!" for how much this corner-cutting will cost the company!

You'll just have to work with what's available, and the clues the Incident Management team has provided about the TA's demands.

Time to get your hands dirty and start digging (or swimming) through the PCAPs! Take the leap into the (Wire)Shark-infested waters and find the treasure!

### Objectives  
This challenge is to identify which machine is sending the stolen data out of your environment and where it went, by looking at how protocols can be used and abused for malicious intent.

From the provided PCAP file, you need to identify 2 important pieces of information:
- the name of our compromised machine sending our super-secret data
- the Command-and-Control (C2) IP address the data is being sent to, where the TA is doing their dirty work

### Flag format
The flag should be in the format:

<compromised-hostname>_<C2-IP>

### Hint 1: Can I have some clues?
A compass heading? Anything?

Avast there, matey! There be some mischief afoot, and clues hidden in this scrap of information the Cap'n has given ye. Let's be wading through it together!

Background

Computers communicate using "protocols", which define how data is formatted, transmitted, and interpreted.

Common protocols include but are not limited to:
- HTTP/HTTPS – for web traffic (ports 80/443)
- TCP/UDP – for reliable or fast data transfer
- FTP, SSH, SMTP, POP, IMAP – for file transfer, remote access, and email
- SNMP, DHCP, ARP, ICMP – for network services and diagnostics

Which protocols are used for names? Take a look at the Wikipedia page linked in the challenge resources.

Ports act like doors for specific types of traffic (e.g., FTP on 21, SMTP on 25). Note that some protocols can use multiple ports, be wrapped ("tunneled") through others, broadcast on multiple ports, or use a port typically reserved for another protocol.

Like the "Pirate Code", protocols are more like guidelines than hard rules (but 99.9% of the time, they are followed).

Threat actors may exfiltrate data using:
- Common protocols (like HTTP/HTTPS) to blend in with normal traffic commonly allowed
- Encrypted protocols (like SSH) to hide content
- Unusual or custom protocols (e.g., ICMP, ARP) to circumvent prevention or detection systems watching for common protocols
- Tunneling data through protocols not originally intended sending data (but really, all protocols are for sending data, right?)

Getting Started

See the main challenge page for links to download and install WireShark, and the link to download the PCAP file. Save the PCAP somewhere you can find it easily, like your Desktop or Downloads folder. Load up the PCAP file in WireShark (File Menu->Open) and let's start our search for the TA!

Analyzing the Packet Capture

Study the packet capture file and see if you can identify any patterns in the data.
- What looks normal, reasonable, common? 
  - A conversation between two computers typically has a request and a response, with some short time between them.
  - Some protocols may have multiple requests and responses in a row, but they are usually related to each other (a "stream")
  - Look for packets that match the protocol they're using, e.g. HTTP requests for web pages for example
- What looks unusual or out of place?
- Are there oddly sized packets, or have unusual content? 
  - Look for packets that are larger or smaller than the typical size for that protocol, or have unusual content.
  - For example, an HTTP request typically has a small payload, while an HTTP response may have a larger payload with lots of data, such as a web page or image.
- Where are things going to or coming from? Is there any pattern there? 
  - Network types and IP address ranges can help here: 
    - Often "Private Network" IP addresses (like 10.x.x.x, 172.16.x.x, 192.168.x.x) are used for internal traffic within an organization, while "Public Network" IP addresses are used for external traffic (the Internet).
    - So if you see a packet from a private IP address like 192.168.1.2 to a public one like 142.250.190.78 (google.com), or vice versa, it could be relevant, whereas packets between two private IP addresses are likely not.
  
Tools to Help Analyze the Data

WireShark has some great functionality to help with this:
- packet "dissection", that looks at the contents of packets in more detail 
  - look at the bottom left of the screen to see the dissection of the selected packet
  - you can expand the sections to see more details, e.g. Frame, Ether, IP, TCP, HTTP, etc.
  - as you do so, you'll notice the byte(s) change color on the lower right of the screen (raw byte view of the packet)
- sorting by columns 
  - click on the column header, like "Protocol" or "Source"
- filtering 
  - right-click on one of the fields in a packet (or the various entries in the Dissector view in the bottom left) to apply a filter to that field or add it to a filter you are building
  - use the filter bar at the top to enter a filter expression, e.g. ip.src == 1.2.3.4
- following streams 
  - right-click on a packet and select "Follow" to see the stream of packets related to that one
- resolving IP addresses to hostnames (if they're available) 
  - click on the Statistics menu and select Resolved Addresses to see what hostnames WireShark has resolved
  - you can sort and filter this list to find the hostnames you're interested in.
  - see below for what you might want to search for.
  - 
Pay attention to the protocols being used, and the ports they are using (you can find Port info in the "Info" column, as well as the dissection of the packet in the bottom left of the screen).

If you've read this far, you should have a good idea of what to look for in the packet capture.

If not, recall what the challenge is asking for:
- The compromised machine's name (so we should be looking for a hostname; what protocols typically deal with names?)
- The Command-and-Control (C2) IP address of the threat actor (where they are sending the data to; what protocols typically use IP addresses? All of them! But it would be related to the 1st item, so if you've found the hostname from its IP address, use the filters or other features in WireShark to find the related packets and see where they are going to or coming from.)

# Solve
This one was very hard for me, check out [Rabbit Holes](#Rabbit-Holes) to see what I tried.

Open the file in Wireshark.

At the top in the search bar, type in 'dns' to filter for dns queries.

<img width="1919" height="1016" alt="Screenshot 2025-07-04 163013" src="https://github.com/user-attachments/assets/b4a4643c-83d0-48bb-9602-f03df686a707" />

Some of the dns querys are being sent from an internal endpoint to and external IP address. In addition, the websites the requests are being send for are very odd looking.

## Rabbit Holes
Rabbit Holes I fell Down:

1. Conversations: I was looking for http conversations between a local host with a resolved name and an external IP. I was looking for a high number of bytes transferred.
2. External IP names: I looked at RESOLVED external IP address names that communicated with internal IPs.
3. Odd DNS names: I looked for odd DNS names, not factoring in the number of requests. I wrote off a few because they were structured with real web names such as xxx.github.com.
4. Slack Messages: I searched for “D5” in Slack to see if I could get any hints, everyone kept talking about filtering by DNS but I had to buy the hint for me to finally understand.
5. While the hint did not directly help me, it did put me on the right path. It mentioned unusual traffic such as using the wrong protocol or packets of the wrong size. This along with the Slack messages hinting at the DNS, I rechecked it. At this point I finally saw the odd DNS traffic right in front of me.

# Flag
Bvlik_251.91.13.37
