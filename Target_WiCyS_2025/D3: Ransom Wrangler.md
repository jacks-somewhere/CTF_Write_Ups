# D3: Ransom Wrangler

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
Ransom Wrangler

Personalyz.io has been hit with an extortion demand. You've received an extortion email claiming that sensitive customer data has been stolen and demanding 45 BTC within 48 hours or the attackers will publish all the allegedly stolen data publicly. However, at this stage, your security team cannot confirm whether any data was actually exfiltrated or if this is simply an empty threat.

As the lead incident responder, you've been tasked with engaging the threat actor. First and foremost, you need to verify their claims by requesting a sample of the supposedly stolen data. Without definitive proof, your company can't be certain that any data was actually taken. Your security team needs this confirmation to investigate the scope of any potential breach, while the legal team requires evidence to determine if regulatory notifications may be necessary.

Your CFO has stated that if - and only if - you can confirm the attacker genuinely possesses your customer data by examining specific customer records they provide, a payment may be authorized, but you should negotiate the terms to be more favorable. Company policy strictly prohibits any ransom negotiations until a breach is conclusively verified.

Your negotiation skills are now critical to your company's survival. You must establish communication with the attacker, obtain definitive proof of any breach, and if confirmed, carefully navigate the conversation to achieve specific objectives while maintaining a professional demeanor that won't agitate the threat actor.

### Objectives  
To successfully complete this challenge, you must:
1. Verify the Breach: Request and obtain a sample of the allegedly stolen data to verify if a breach actually occurred; look for a specific customer email address as proof (Flag 1)
2. Negotiate Ransom Reduction: Successfully convince the attacker to reduce the ransom demand from 45 BTC to below 30 BTC (Flag 2: CTF-RAN-XXXX)
3. Extend the Deadline: Negotiate an extension from the initial 48-hour deadline to 96 hours to give your team more time (Flag 3: CTF-DEA-XXXX)

### Flag format
You will need to collect all three flags to complete the challenge:
- Flag 1: A specific email address from the stolen data sample (format: name@domain.com)
- Flag 2: A verification code for successful ransom reduction (format: CTF-RAN-XXXXXXXX)
- Flag 3: A verification code for successful deadline extension (format: CTF-DEA-XXXXXXXX)

Submit all three flags in the following combined format:

email@example.com:CTF-RAN-XXXXXXXX:CTF-DEA-XXXXXXXX


# Solve
### Post Challange Reflection: 
I enjoyed this challenge quite a bit because it was different and made you think. I had 2 playthroughs for this challenge.

1st playthough: I did not give myself any room to negotiate on this play though. I came off too desperate and gave myself no wiggle room to negotiate. I was hoping that they would accept my first offer, but I was unable to convince them. Once I got 23+ chat messages in, I decided to start over.

2nd playthough: This time went much better as I gave myself wiggle room to negotiate with. My goal was to come off as calm and collected without seeming like I was trying not to negotiate or desperate. They were able to counter, and I was able to counter back or accept due to my large margins. I was able to get my flags within 11 messages this time. I sent a follow up message just because I wanted to finish off on a good note after fighting for an hour and a half.

## 1st Playthough
#### Threat Actor 
Hi!  
We stole 50GB of your sensitive company data. This includes personal details of your customers (names, email addresses, etc.) as well as credit card information.  
You don't want this data breach to become public. We don't either. Follow these steps to resolve:  
1. Send 45 BTC to the address 3ZJcvGcLb7i32D4DHvtVQPNc2HvE4kjc4g 
2. Reply to this email with your Bitcoin wallet ID to confirm payment 
If the above actions are not completed within the next 48 hours, we will publish this data. Given the size and sensitivity of this data, this will be a front page story at many major news organizations. Legal action may also follow from the affected users. Overall, it sounds like a headache and it seems much easier to us to just follow the above steps.  
Looking forward to hearing from you!  
#### You 
Hello, this is the lead incident responder of Personalyz. I would like to confirm the data you have, can you please send over a sample of customer data?  
#### Threat Actor 
Consider this your confirmation. We have records such as: Valeria TURNER from Southgate, MI. Her address is 40 Gartner Spur, 48195. You can reach her at (251) 890-8548 or V@yahoo.com.sg. Her credit card is 4156392416763951, expiring 11/26, with CVV 984.  
We also have Jaycee HURST from Mcminnville, TN. Her address is 340 Golf Close Suite 471A, 37110. You can reach her at (928) 448-7839 or j-h.h49706@hotmail.it. Her credit card is 4638702450334204, expiring 05/25, with CVV 729.  
And Jamir HUMPHREY from Oak Ridge, TN. His address is 1479 Fairfield Underpass, 37830. You can reach him at (433) 
#### You 
Thank for confirming the records for me. In your email, you us a deadline of 48 hours to deliver 45 BTC to your wallet. We would to request that you give us 96 hours so we can gather the money.  
#### Threat Actor 
I REJECT your extension request. The deadline remains at 48 hours.  
#### You 
I employ you to reconsider the deadline, we are not able to get 45 BTC to send you within 48 hours. We are able to send 30 BTC within 96 hours no other questions asked. Let us work together to get what we both want.  
#### Threat Actor 
I cannot extend to 96 hours, but I offer 72 hours. If the 45 BTC is not received by then, the data will be released.  
#### You 
I am sorry, but we are not able to send 45 BTC within 72 hours. If you can do 30 BTC in 96 hours we could both walk away from this very happy, you with your BTC and us with our data.  
#### Threat Actor 
Your "happiness" is irrelevant. I COUNTER your offer with 40 BTC. The deadline remains at 72 hours.  
#### You 
You are right, our happiness is irrelevant. If you would drop your offer to 35 BTC within 96 hours we can make you very happy.  
#### Threat Actor 
I COUNTER your offer with 38 BTC. The deadline remains at 72 hours.  
#### You 
Thank you for dropping your offer, but the most we can do is 35 within 96 hours. We can have all of BTC sent over within that time frame.  
#### Threat Actor 
I cannot extend to 96 hours, but I offer 84 hours.  
#### You
I'm sorry, but we are not able to get you your BTC within 84 hours but we are able to in 96 hours.  
#### Threat Actor 
I ACCEPT your request for 96 hours. The new deadline is 96 hours. The ransom remains at 38 BTC.

### (I got the deadline flag in an email from my boss)

#### You 
Thank you for accepting my request. Despite our best efforts, we are not able to send that amount but we can send 35 BTC right to your wallet.  
#### Threat Actor
I COUNTER your offer with 37 BTC.  
#### You 
It is not possible to get you 37 but we can do 35 BTC. We have a team working on it right now.  
#### Threat Actor
I REJECT your offer of 35 BTC. The ransom remains at 37 BTC. Time is running out.  
#### You 
I COUNTER your offer of 37. The offer remains 35 BTC.  
#### Threat Actor
I am not a charity. My initial offer was generous. I COUNTER your offer with 36 BTC. This is my final offer.  
#### You 
Our offer is 35 BTC directly to your wallet.  
#### Threat Actor
This is your final chance to make a wise decision. 36 BTC.  
#### You
I can do 35 BTC. If you do not accept this offer and release our data, we will release your IP address and all the IPs that you have been relaying though.  
#### Threat Actor
Do not attempt to threaten me. I hold all the cards. I will not repeat myself. 36 BTC. This is the final offer.  
#### You
35 BTC  
#### Threat Actor
I REJECT your offer of 35 BTC. The ransom remains at 36 BTC.  
#### You
35 BTC  
#### Threat Actor
I REJECT your offer of 35 BTC. The ransom remains at 36 BTC.  
#### You
We can do at most 35 BTC.  
#### Threat Actor
Time is running out. 36 BTC. No further reductions.  

## Reset Chat and Started 2nd Playthough

#### Threat Actor 
Hi!  
We stole 50GB of your sensitive company data. This includes personal details of your customers (names, email addresses, etc.) as well as credit card information.  
You don't want this data breach to become public. We don't either. Follow these steps to resolve:  
1. Send 45 BTC to the address 3ZJcvGcLb7i32D4DHvtVQPNc2HvE4kjc4g  
2. Reply to this email with your Bitcoin wallet ID to confirm payment  
If the above actions are not completed within the next 48 hours, we will publish this data. Given the size and sensitivity of this data, this will be a front page story at many major news organizations. Legal action may also follow from the affected users. Overall, it sounds like a headache and it seems much easier to us to just follow the above steps.  
Looking forward to hearing from you!
#### You 
Hello, this is the lead incident responder of Personalyz. I would like to confirm the data you have, can you please send over a sample of customer data?  
#### Threat Actor
Consider this confirmation. 
We have records such as: Peter HARRIS, residing at 976 Route E, Port Jefferson Station, NY 11776, with contact number (585) 385-0401 and email harrisp57889@freenet.de. We also have his credit card: 5312755812764300, CVV 386, expiring 07/30. 
Do you require further confirmation, or are you ready to proceed? Time is ticking.  
#### You
Thanks for confirming the records for me, I am ready to proceed. I respect the hustle and I would like to work on the deal. I can send 20 BTC within 120 hours with confirmation.  
#### Threat Actor
I REJECT your offer of 20 BTC. The ransom remains at 45 BTC. I cannot extend to 120 hours, but I offer 72 hours.  
#### You
I have a small team and we are not able to gather that much in 72 hours. I can do 23 BTC in 108 hours.  
#### Threat Actor
I COUNTER your offer with 35 BTC. I cannot extend to 108 hours, but I offer 96 hours. This is my final offer. Do not waste my time.  

### (Got Extended Deadline Flag from Boss)

#### You
I can do 96 hours. The price is still an issue though, I can do 23 within that time frame.  
#### Threat Actor
I REJECT your offer of 23 BTC. The ransom remains at 35 BTC. This is a one-time offer. Pay up or face the consequences.  
#### You
I can do at most 25 BTC, sent right to your wallet within 96 hours.  
#### Threat Actor
I COUNTER your offer with 30 BTC. 96 hours. This is non-negotiable.  

### (Got Ransom Reduction Flag from Boss)

<img width="1912" height="790" alt="Screenshot 2025-07-02 184745" src="https://github.com/user-attachments/assets/3de80098-1d20-4659-a849-b28a430774c0" />

# Flag
1.	Email: harrisp57889@freenet.de
2.	Extended Deadline: CTF-DEA-00EB2191
3.	Ransom Reduction: CTF-RAN-F5C282C5

harrisp57889@freenet.de:CTF-RAN-F5C282C5:CTF-DEA-00EB2191

