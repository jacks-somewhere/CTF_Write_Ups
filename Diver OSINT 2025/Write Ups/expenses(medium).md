### Question
Answer the amount (in local currency) paid by the mayor of São Miguel do Guamá to a food-related company by credit card payment in January 2025.
Flag Format: Diver25{1234.56} (Currency symbol or code not required)

--------------------------------------------------

This was the second to last question that I answered. At this point it was around 9:00 pm with the CTF ending at 11:00 pm and I had been working non-stop for 11 hours. This was reflected somewhat in my search and the flag answers.

After a quick search I found out the mayor of São Miguel do Guamá is Eduardo Sampaio Gomes Leite. I also learned that the city is located in Brazil.
https://saomigueldoguama.pa.gov.br/o-governo/prefeito/

![Screenshot 2025-06-10 171239](https://github.com/user-attachments/assets/ab3e7b9c-0e9e-480f-9b7b-fab488a2adf5)

Knowing that almost all governments have one or more websites related to officials’ financial information, I asked ChatGPT where to look for Brazil’s financial information. The AI gave me three websites to check.

Local governments in Brazil are required to have a transparency portal where general and financial information are accessible. The portal was linked directly on the local government’s site but the credit card information for 2025 was missing.

https://saomigueldoguama.pa.gov.br/portal-da-transparencia/

The next place I checked was the Portal of Municipal Transparency financial portal. Clicking “Total Expenditure” showed all recorded transactions. I filtered by “January” and “Payments” to see if I could in credit card transactions. I did see the correct transaction while searching though the data, but I did not recognize it at the time.

https://transparencia.tce.sp.gov.br/municipio/guatapara/2025

![Screenshot 2025-06-10 171155](https://github.com/user-attachments/assets/f5b665c6-71e1-49a7-a710-c0082ffd9c5b)

The last place I looked was the Brazil’s national transparency portal. I searched for “Eduardo Sampaio Gomes Leite” but all the results kept coming up as “Eduardo Sampaio Gomes Milk” (I later figured out it was due to translating the page from Portuguese to English). Despite this, clicking the first result gave me the correct person. 

https://portaldatransparencia.gov.br/cartoes/cpdc?portador=605343761&ordenarPor=mesExtrato&direcao=desc

Scrolling though the transactions, I was able to then able to figure out the correct transaction based on the flag question.

![Screenshot 2025-06-10 172046](https://github.com/user-attachments/assets/f0e4d113-1b2c-498f-86b1-161d93f32de4)

### Answer
Looked though the transactions and I found ones that fit the bill:
- Diver25{1.593.081,94} *Correct answer, wrong formatting
- Diver25{350,000.00}
- Diver25{100.482.83}
- Diver25{3.864.760,53}
- Diver25{1593081.94} 
