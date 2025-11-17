# D4: Trout of Office

Points: 500

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
Trout of Office

It’s 03:04, and you've gotten a text on your phone waking you out of deep dreams of relaxing beaches and sunsets, fruity drinks and pleasant scenery and company.
You groggily silence the grating beeping and read the message from your manager, and it’s not good news. Personalyz.io has apparently had a data breach, and they need you on it immediately.

What's up? you text back, still half-asleep.

Seconds later, your phone buzzes again with a reply.

We got a ransom email from a threat actor claiming to have exfiltrated our data, and we need to validate if it was ours or not.

Get online ASAP and check the emails, we need to know if we have a problem.

You rub your eyes and try to shake off the sleepiness, but it’s not working. The company’s database administrator, Zeke "Bro" Libnal could have answered this for them; Zeke knows the data systems inside and out. But Zeke actually is on vacation, not just dreaming about it, enjoying his annual "Fishing and Fritatas" experience off the grid in Alaska, and you’re the only one who can help.

Half asleep and still in your pajamas, you stumble to your computer and log in, firing up the coffee maker on the way. You're greeted by a mountain of emails, but one stands out.

From: Enterprise Incident Management  
Date: 2025-03-23 22:41  
To: Security Team  
Subject: URGENT: Data Breach Incident  
Importance: High

Incident Security Team,

We've received a ransom demand from a Threat Actor claiming to have 50GB+ of sensitive data. Legal needs to know if the Threat Actor has actually stolen our data, or if we're "lucky" and it was someone else's. Zeke's absence has left us in a bind, and we need your expertise to identify if this info was indeed taken from our systems.

This is a Priority 1 incident, and we need answers by sunrise to prepare for the legal fallout.

Susan in EIM will be coordinating with you on this.

Enterprise Incident Management

Ugh. There goes your relaxing vacation dream, and you haven't even had your coffee yet. Without Zeke, you don’t have access to the database, or the data itself. But you do have something:
•	Partial records
•	System logs from internal components
•	And just enough metadata to piece it all together.

Trout of Office is the name of the game, and no, it’s not a holiday.

The company’s network has been compromised, and Legal wants answers by sunrise. You’ve got some names, a bunch of logs, and no coffee.

Good luck.

### Objectives  
This challenge is to identify something that conclusively proves that the data was stolen from the company, by showing we have a lot of info about that victim in our system (and probably the threat actor does now as well).

For the purposes of this challenge, you need to find personally identifiable data of a victim that strongly suggests it's ours. You've gotten some of the victim data from the Threat Actor, from conversations the Negotiations team has had with them. In other words, one of the people whose data was stolen (see Challenge D3. Ransom Wrangler).

You'll need to find the following additional information:
•	the name of the system that has the "source of truth" for the data, i.e. the most authoritative source of the data
•	victim data of one of the victims of the data breach, including: 
  o	their birthdate
  o	their middle initial of the victim whose birthdate you found, i.e. the person whose data was stolen.
  o	the last 4 digits of their Social Security Number (SSN)
  o	their person-record-id - their ID in our system (think "Primary Key" from a database table)
Note : Despite the scenario's (made-up) urgency, you do not need to find the answer by sunrise! (But in a real incident, you might!)


### Flag format
The flag should be in the format:

<system-name>_<birthdate>_<middle-initial>_<last-4-digits-of-SSN>_<person-record-id>

For example, if:
•	the system name is database-server-01
•	the victim's: 
  o	birthdate is January 2nd, 1990, and the format is YYYY-MM-DD, so: 1990-01-02
  o	middle initial is M
  o	SSN is 123-45-6789
  o	person-record-id is abc123

the flag would be:
•	database-server-01_1990-01-02_m_6789_abc123
•	DATAbase-SERver-01_1990-01-02_M_6789_ABC123 - the case doesn't matter

Note: : The system name is not the hostname of the system, but rather the name of the application itself, e.g. CRM-01 or HumanResources-X02-PROD.

### Required Tools
•	The Personalyz.io dashboard log viewer, Insightful Horizon! (Insightful Horizon is our OpenSearch Dashboards instance, which is a web-based interface for searching and visualizing data stored in OpenSearch. It's basically a fork of the ELK - ElasticSearch, Kibana, LogStash - stack).

Pick from one of the servers below:
o	https://target.io
o	https://target2.io
o	https://target3.io

Use it to cast through the company data and see if we can "hook" the info Legal needs to prepare for the incident fallout.
o	Username: analyst
o	Password: analyst

Zeke thinks a lot of himself, and you'll find the logs named zekes-logs-..., with a fishy theme to them. You'll also need to review the http-logs to find out how to query the system.
•	Security has access to an entrypoint to access the Personalyz.io application system here

Note : you'll have to figure out the right API calls from the logs!
•	Tool for making HTTP requests, passing and seeing headers for request and response
  o	curl - command line
  o	Postman - UI based
  o	netcat - more lower-level command line (for the masochistic!)
If you need a refresher on some of the victims from D3 Ransom Wrangler, connect to the company email here using your email that you signed up for the challenges with.

Note: You don't have to renegotiate with the Threat Actor, or even have solved D3. Just ask them for proof including full name, address and credit card details.

Good luck!

# Solve
I did not solve this challange.

# Flag


