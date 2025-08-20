# D1: Mystery Mail

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
What a way to start your day... you've just logged on as a member of Personalyz.io's Cybersecurity team and see the last thing any cyber professional wants to see: an extortion email at the top of your inbox. Looks like we've received a menacing message from an unknown sender, claiming that sensitive data has been stolen from the company. The email demands a ransom and threatens to release the data if the demand is not met within 48 hours.

Given the nature of the data we process, this is a serious threat to us and our customers.

You've been tasked with performing some analysis on the email itself to ensure our responding teams can respond appropriately.

To start, can you determine the sender's original IP address?

### Objectives  
Identify the sender's IP address using the attached email file.

Don't overthink it!

### Flag format

The flag will be a valid IP address, for example:  
•	242.229.211.211  
•	243.151.196.173  

# Solve
I opened file with Autopsy but I only saw the last IP that the email was sent from, 251.14.1.16.  
Next, I tried to run exiftool, but I did not get any new information.  
Lastly, I opened the email with notepad and located all IPs the email was sent from at the top.  

<img width="975" height="442" alt="image" src="https://github.com/user-attachments/assets/c20a16a4-a260-4a77-9fc6-c19bdade81fc" />


# Flag

252.44.98.29
