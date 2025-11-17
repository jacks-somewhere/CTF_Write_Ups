# Secret.txt Society
Category: Web Security 	

Points: 75

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question
Our team suspects that a Juche Jaguar developer accidentally left something interesting behind on a public site. You’ve been tasked with examining its structure. Can you uncover what the bots were told to ignore? Start with the usual entry points a crawler might explore. One disallowed path leads to a page where someone left behind more than just code.

https://juche.msoidentity.com/

# Solve
At this point I decided to take a break from some of the harder questions and do something easy. I followed the provided link and it brought me to this website.

![Screenshot 2025-06-14 161737](https://github.com/user-attachments/assets/0e70c7dd-b475-4427-831f-7a98fa1b9ad0)

With the site clearly wanting me to head to robots.txt I checked it out.

https://juche.msoidentity.com/robots.txt

![Screenshot 2025-06-14 161825](https://github.com/user-attachments/assets/0a7aac05-608a-4ddd-87b6-9491dc3b22ee)

That’s suspicious…

https://juche.msoidentity.com/juchejaguar/

![Screenshot 2025-06-14 161927](https://github.com/user-attachments/assets/90461ff6-ccfe-410a-9268-8f8f92925b5f)

Yay, I found the flag!

# Flag
C1{r0b0ts_arent_4lways_p0lit3}
