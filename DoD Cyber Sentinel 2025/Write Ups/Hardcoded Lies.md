# Hardcoded Lies

Category: Malware/Reverse Engineering

Points: 75

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

## Question 
The malware sample doesn’t appear to print anything useful. But our threat intel team believes it holds a hardcoded configuration string. Can you pull on some strings to retrieve it?

Provided File: hardcodedlies.zip (contained "hardcodedlies")

# Solve

Based on the wording of the question I knew that I had to running strings to extract all of the string data in the file.

I downloaded, unzipped, and copied the file over to Kali. I ran strings and quickly found the flag.

> strings hardcodedlies

![Screenshot 2025-06-14 115751](https://github.com/user-attachments/assets/6b5a7111-175d-4809-8861-fba20cb3a05d)

# Flag
C1{h4rdc0ded_but_0verlooked}
