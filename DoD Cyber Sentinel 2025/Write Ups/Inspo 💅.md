# Inspo 💅
Category: OSINT

Points: 200

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
We believe that the North Torbians are heavily influenced by North Korean developments and wish to match them. We have suspicions that Juche Jaguar will try to build out similar spaces to ones in these pictures. Can you find the coordinates of where these pictures were taken?

The flag is any valid decimal degree coordinate notation within a 500m radius of the building. The flag is in the following format: C1{XX.XXX,XX.XXX}

For example, the White House would be at decimal degree notion of 38.897, -77.036. The flag for the White House would be: C1{38.897,-77.036}

Note that this flag is a regex match for any valid coordinate within the 500m radius.

# Solve
THIS IS NOT A WALK THOUGH SOLVE. I WAS UNABLE TO RETRACE EVERY STEP SO STEPS ARE MISSING.

Doing a quick reverse image search on the photo of the computer room I found the same photo in a reddit post.

![Screenshot 2025-06-14 135144](https://github.com/user-attachments/assets/77c1aaa7-e828-4ddb-81e5-4b4cb7fd3edc)

At this point in time I did not keep record of every step to find the coordinates. My history did not track every search I will be listing my general search and flow.

Using DuckDuckGo I did a quick search for:

- "North Korea DPRK computer club" 
- "north korea computer club location"
- "north korea Pyongyang computer club" 

But I did not gather much after a quick skim though a few websites.

Kim Jong-un visits North Korea's first computer club without computers: https://dprk.news-pravda.com/en/dprk/2025/04/08/4828.html

North Korea Launches a Modern Elite Cyber Club: https://baltimorechronicle.com/tekhnologii/2025/04/27/north-korea-launches-a-modern-elite-cyber-club/

Switching to Google, I search for "north korea Pyongyang computer club" and used their AI mode to see if I could get a location. This led to another reddit post but no location. 

https://www.reddit.com/r/NorthKoreaPics/comments/1kelbad/north_korea_opens_first_online_gaming_cafe/#:~:text=North%20Korea%20in%20recent%20weeks%20has%20revealed,to%20other%20mass%20online%20gaming%20hubs%20elsewhere!

Hitting a dead end, I opened Google Maps. I searched for:
- "north korea Pyongyang computer club"
- "和盛區雙峰塔" (hwasong district, searched several times)
- "internet cafe"
- "화성 콤퓨터 오락관"

Going back to DuckDuckGo, I then searched for "Mars Computer Entertainment Center" and searched though images. I was likely trying to find a match to the given photos to try and confirm the location.

After switching back and forth between DuckDuckGo and Google Maps, I search for "39.0960642,125.7674291". These are the coordinates to the flag. I did not trust my gut and contuned to search.

I vistited https://www.hani.co.kr/arti/politics/defense/1190629.html and then searched for the coordinates again on Google Maps. I then submited the Flag a minute later.

# Flag
C1{39.0960,125.7674}
