# Task 7- OSINT 3
Category: OSINT

Points: 60

[Challange](#Challange)

[Solve](#Solve)

[Flag](#Flag)

# Challange
"After the initial breach, a single OT-Alert appeared in Virelia’s monthly digest—an otherwise unremarkable maintenance notice, mysteriously signed with PGP. Corporate auditors quietly removed the report days later, fearing it might be malicious. Your mission is to uncover more information about this mysterious signed PGP maintenance message."

# Solve
I remember seeing a deleted report under the virelia-water GitHub while working on OSINT 1.
- https://github.com/virelia-water/compliance/commit/bf80b28d73cdbbccaa37c34633de98cd00e7b236

![Screenshot 2025-06-27 154255](https://github.com/user-attachments/assets/abbba812-53df-4058-8189-f2043d485374)

I found the pgp key again.

iQFQBAEBCgA6FiEEiN7ee3MFE71e3W2fpPD+sISjEeUFAmhZTEQcHGFsZXJ0c0B2aXJlbGlhLXdhdGVyLml0LmNvbQAKCRCk8P6whKMR5ZIUCADM7F0WpKWWyj4WUdoL6yrJfJfmUKgJD+8K1neFosG7yaz+MspYxIlbKUek/VFhHZnaG2NRjn6BpfPSxfEkuvWNIP8rMVEv32vpqhCJ26pwrkAaUHlcPWqM4KYoAn4eEOeHCvxHNJBFnmWI5PBFpXbj7s6DhyZEHUmTo4JK2OZmiISP3OsHW8O8iz5JLUrA/qw9LCjY8PK79UoceRwWtJj9pVsE+TKPcFb/EDzqGmBH8GB1ki532/1/GDU+iivYSiRjxWks/ZYPu/bhktToNNcOzgEfuSekkQAz+CiclXwEcLQb219TqcS3plnaO672kCV4t5MUCLvkXL5/kHmsSh5H=jdL7

Trying to search for the whole key did not yield any results.
-	https://keys.openpgp.org/
-	https://keyserver.ubuntu.com/

Running into a dead end, I asked chatgbt what else I could search or do. It suggested searching for a shortened version of the key and alerts@virelia-water.it.com.

Going back to the key servers, I search for “virelia-water.it.com” and got a hit on https://keyserver.ubuntu.com/.

![Screenshot 2025-06-27 154315](https://github.com/user-attachments/assets/2aad7d5a-ea07-41da-8fe4-543ab414849e)

# Flag

THM{h0pe_th1s_k3y_doesnt_le4d_t0_m3}

