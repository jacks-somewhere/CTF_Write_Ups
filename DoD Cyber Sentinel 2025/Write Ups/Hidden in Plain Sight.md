# Hidden in Plain Sight
Category: Forensics

Points: 75

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
Analysts recovered a suspicious image from a threat actor’s social media account. At first glance, it looks like an innocent selfie - but insider reports suggest that a flag might be hiding in the image metadata. Can you extract it?

![selfie](https://github.com/user-attachments/assets/6d942233-08ee-45f4-86b8-5a9e925f591c)

# Solve
Downloaded the file and Checked the Properties for the flag.

I then uploaded it to:
- CyberChef
- exiftool

The flag was found using exiftool under comment.

![Screenshot 2025-06-14 150833](https://github.com/user-attachments/assets/31b8da48-7498-447f-a9b4-97ac9cb2ff99)

# Flag
C1{smile_youre_flagged}
