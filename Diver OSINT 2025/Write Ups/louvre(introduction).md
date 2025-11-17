### Question
Answer the vendor of one of the Louvre's public Wi-Fi access points that meets the following criteria.
-	Information was collected on 28 February 2025. This can be accessed via online.
-	Determine the vendor according to the BSSID.
Flag format: Diver25{Company Name} (e.g. If the company is Apple Inc., the flag should be Diver25{Apple Inc.}.)

--------------------------------------------

The first thing I did was look up Louvre. It is a famous museum located in Paris, France. Now that I had the location, I looked for an access point as I know that it would list information needed to find the flag.

After logging into wigle.net and looking up the Lourvre, I zoomed in and picked one of their guest WiFi access points. This outputted a bunch of information including the bssid.

![Screenshot 2025-06-11 162920](https://github.com/user-attachments/assets/72c7fee6-844a-4ee2-b982-3f451c7874ae)

Searching for “can you find the OUI based on the bssid” led to maclookup.app. Inputting the bssid listed the OUI as Hexlett Packerd Enterprise. This was the correct answer.

### Answer
Diver25{Hewlett Packard Enterprise}
