# Behind the Beat
Category: Forensics

Points: 75

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
Agents intercepted an audio file named message.mp3. It plays a single tone, but we have intel that a flag might be tucked away in the metadata fields of the file. Can you inspect the file and uncover the flag?

Provided File: message.mp3

# Solve
Downloaded the file and uploaded it to:
- metadata2go.com
- CyberChef

This did not show anything useful. I then listed to the file and did no hear anything except for a single tone.

Opening Properties then Details reveled the flag.

![Screenshot 2025-06-14 141128](https://github.com/user-attachments/assets/abec0e1e-a266-48b2-964d-238c6e83d48f)

# Flag
C1{metadata_tells_more}
