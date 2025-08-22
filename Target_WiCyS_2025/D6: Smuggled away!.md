# D6: Smuggled away!

Points: 500

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
Smuggled away!
Aye, ye be a smart one! Looks like we found where the stolen data is being smuggled out from... Since it looks like the pirates have already stolen some of our data, can we at least find out what they stole? If it's customer data, we may have an obligation to notify the affected parties...

Use your best skills to discover and what they took.

### Objectives  
Now that you can see where things are being exfiltrated, can you provide:
- the credit card's expiration date and CVV
- the email

of the poor soul (aka "gullible client") who we saw in the PCAP?

### Flag format
The flag is in the format:

<CreditCardExpiration>_<CVVofCreditCard>_<email>

# Solve
### 1st attempt

I copied the hex dump of the packets and tried to enter them into CyberChef to decode them. I was looking for hidden byte data contained in the query. This was a dead end, and I did not find any data.

### 2nd attempt

After walking away and clearing my mind, I came back to this problem and I finally solved it.

What I did:
1.	Take the string at the start of every standard query sent from bvlik to 251.91.13.37 and combine them.

```
d6fqqaecfjjgqax7bxglcducgaiabuhz73remhou332tqyetdajb2zeqzgyway2mfzenv6x76ia665iwm4mk77pd3ygsbjbv6yqrp5hjqxr7us3qrffutqpqs3w3hqxqasrjuglwjtkr4g27dxmloddblphhtgw762oyehmxldaaxk4iunlbwjjbochhjqzh577bt4hmlrzqaaaa
```

2-	Heading over to dCode.fr I used the “Identifying a coded message” feature.
3-	Went through all of the results intel I reached “Decipherment by Substitution”
  -	All this did was capitalize every letter. It did not change anything else about the string
New String

```
D6FQQAECFJJGQAX7BXGLCDUCGAIABUHZ73REMHOU332TQYETDAJB2ZEQZGYWAY2MFZENV6X76IA665IWM4MK77PD3YGSBJBV6YQRP5HJQXR7US3QRFFUTQPQS3W3HQXQASRJUGLWJTKR4G27DXMLODDBLPHHTGW762OYEHMXLDAAXK4IUNLBWJJBOCHHJQZH577BT4HMLRZQAAAA
```

4-	I copied this new output of the “Decipherment by Substitution” into CyberChef.
5-	Used the Magic wand to get the recipe
  -	Trying to input the string without first capitalizing every letter will not decode the message. The Magic Wand will only work if it is capitalized.

<img width="1531" height="836" alt="Screenshot 2025-07-07 112256" src="https://github.com/user-attachments/assets/a10b270b-ba23-40bb-a676-257c4f69528b" />

# Flag

11/30_0016_alec@sbcglobal.net
