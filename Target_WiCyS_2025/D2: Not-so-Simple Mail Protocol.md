# D2: Not-so-Simple Mail Protocol

Points: 100

[Challange](#Challange)  
[Solve](#Solve)  
[Flag](#Flag)  

# Challange
We've received a menacing extortion email from an unknown sender, claiming that sensitive data has been stolen from the company. The email demands a ransom and threatens to release the data if the demand is not met within 48 hours.

Unfortunately, it's clear based on the extortion email that the sender attempted to send this email before... Since the demand's due date is relative, we need to find the first email sent so we can estimate a lower bound on the deadline for the legal and finance teams to plan around.

Can you trace the digital breadcrumbs and find the first extortion email sent by this threat actor?
Objective

Our trusty log dashboard Insightful Horizon (Link to dashboard) is back! Use it to pivot and find the first extortion email from this incident.
•	Username: analyst
•	Password: analyst

Once you've found it, use the email address that sent the email as the flag.

### Note
This challenge was created earlier in 2025, so the last data you'll see is from March.

### Flag Format
An email address, for example:
•	example@wicys.example

# Solve
Opening the provided link led to a dashboard Opensearch Dashboard.

As this challange was based on the previous one, I reviewed what I knew: 
- The first email was likely sent to the same email address and from the same IP.

Based on this I created a query:

```
to:"security@personalyz.io" AND path:252.44.98.29 OR path:250.24.46.164
```

### How does this query work?
- " to:"security@personalyz.io" "
  - Show only emails sent to security@personalyz.io
- " path:252.44.98.29 OR path:250.24.46.164 "
  - Show only emails that have one of these ip address

When the query is put together it will search for any emails that where sent to security@personalyz.io and that have 252.44.98.29 or 250.24.46.164 in their path.

<img width="1513" height="755" alt="Screenshot 2025-07-02 164026" src="https://github.com/user-attachments/assets/86118fc2-d8d7-42c0-9545-7f520cdcfde8" />

# Flag

tharris456@tgwnaagm.co
