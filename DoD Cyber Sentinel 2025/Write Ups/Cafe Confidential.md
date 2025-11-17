# Cafe Confidential

Category: OSINT

Points: 150

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
Two photos were posted minutes apart by someone of interest. One shows them enjoying a slice of cake in a boutique café; the other captures a well-known landmark in the background. We believe both photos were taken on the same outing. Can you determine exactly which café they visited, and where is it? 

![Image_1](https://github.com/user-attachments/assets/829a2a2b-f56d-43ea-b3f2-758c3f8bd624)

![Image_2](https://github.com/user-attachments/assets/75bbd6bf-3ce8-49f5-b7eb-fbd02c2c66fd)

# Solve
The first thing I did was do a quick search for “key green p cake store”. This did not return anything useful. 

Next, I reverse image searched the building in the picture with my phone. This returned the building as Harrods on Brompton Road in London. I was able to confirm this by comparing known photos to the location.

Next, I searched for cake shops in London on Google Maps. I quickly realized this was not helpful as none of the logos appeared next to the name. In addition, none of the top results matched the first photo at a glance.

I reversed image searched the photo of the cake, quickly getting a hit for Parker’s Jumeirah Lowndes Hotel.

![Screenshot 2025-06-14 131047](https://github.com/user-attachments/assets/765e8737-5d48-43d5-8b4c-9e2d4fde8f6d)

To confirm that I had the correct flag, I checked the distance from Harrods to the cake store. It was a short 8-minute walk.

![Screenshot 2025-06-14 131023](https://github.com/user-attachments/assets/f59f8088-416c-487b-b8c1-aa695d17cb31)


# Flag
C1{Parker's Jumeirah Lowndes Hotel} 

#### C1{Parker's_Lowndes} (Correct)

