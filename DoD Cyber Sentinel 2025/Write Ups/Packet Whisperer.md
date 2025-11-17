# Packet Whisperer
Category: Networking

Points: 75

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

## Question 
Missing the question but it was asking you to find the a username within a packet capture.

# Solve
I downloaded the provided login.pcap file and opened it in Wireshark. I then found a POST /login packet and right clicked on it. I chose "Follow" then "http stream" to follow all the data related to the login process.

![Screenshot 2025-06-17 124001](https://github.com/user-attachments/assets/a2ea1638-b869-4a7e-a1e4-852f90767efc)

I found username line and converted it to the flag.

“username=ironpotatoadmin&password=C1%7Bmaybe_TLS_would_be_nice%7D”

![Screenshot 2025-06-14 110918](https://github.com/user-attachments/assets/938cf53e-f89a-4e85-8602-38d4e7309d8b)

# Flag
C1{maybe_TLS_would_be_nice}
