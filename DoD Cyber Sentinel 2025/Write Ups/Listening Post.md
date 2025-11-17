# Listening Post 
Category: Forensics

Points: 150

[Question](#Question)

[Solve](#Solve)

[Flag](#Flag)

# Question 
We've intercepted a radio broadcast being bounced off a satellite likely intended for the North Torbian cells located around the world. Do you think you can unravel what they are transmitting?

Provided Files: radio.wav, radio.mp3

Hint

Maybe the beeping isn't just noise but actually has some meaning. Truthfully, it sounds a bit like those blue boxes.

# Solve
I had to consult Chatgpt heavily on this one from the very start as I have never done an audio based challenge.

Before starting any analysis, I did take a moment to listen to the .mp3 file before starting. My first thought was that it sounded like a dial up tone like the ones that old computers used to connect to the internet. 

I wrote a prompt to ChatGPT asking what tools could run on Kali that would analyze the audio files. It suggested Audacity as its first chose. 

Downloading Audacity and inputting the file did not produce any immediately usable results except for a visual of the audio. However, I needed an output that gave me a list of numbers or visual highs and lows so I could manually type out 1s and 0s. Looking online for Audacity settings that would do this did not help ether, so I bought a hint. 

---

Hint

Maybe the beeping isn't just noise but actually has some meaning. Truthfully, it sounds a bit like those blue boxes.

---

Inputting the hint into ChatGPT confirmed that the sound was a Dual-Tone Multi-Frequency (DTMF) which are tones that represent numbers on a phone keypad. This time it had me try multimon-ng and provided a command to try and decode the file.

> multimon-ng -t wav -a DTMF radio.wav

Running this command threw the error:

Enabled demodulators: DTMF 
execlp: No such file or directory

I headed back to ChatGPT and inputted the error. It explained that the error was due to multimon-ng not being able to use the .wav format of the file. The file needed to be coverted to raw then inputted to multimon-ng. 

In order to do this, it had me download SoX (Sound eXchange) and run a new command. 

> sox radio.wav -t raw -r 22050 -e signed -b 16 -c 1 - | multimon-ng -t raw -a DTMF -

The output of this command was lines of:

DTMF: 1

DTMF: 0

Typing out the 1s and 0s by hand:

0100001100110001011110110111001000110100011001000011000101101111010111110110101100110001011011000110110000110011011001000101111101110100011010000011001101011111011101000011000001110010011000100011000101100001010111110111001101110100001101000111001001111101

Note for string above: This is the correct binary string that will give the correct flag. 

My first attempt had an error near the end. I ended up with something that looked like the flag in the beginning but the end included what appeared to extended ASCII characters which I know was wrong. 

Not wanting to spend time typing out the 1s and 0s again, I asked ChatGPT to try and decode the text. I first prompted it to create a Python code that would take the input and remove the DTMF leaving only a string of 1s and 0s. At the time I did not chose to use any of the given scripts.

Why? The output of SoX and multimon-ng resulted in the 1s and 0s each being on their own line. The provided scripts had me insert the output of 1s and 0s into the code and then run it. While I have coded in Python before I do not have experience using input that is hard coded to each be on their own line. I did not want to spend time changing the code or taking the output of SoX and multimon-ng and reformatting it. 

Example taken from ChatGPT:

```
# Paste your DTMF input text below
dtmf_input = """
DTMF: 0
DTMF: 1
DTMF: 0
DTMF: 0
DTMF: 0
DTMF: 0
DTMF: 1
DTMF: 1
... (continue your input here)
"""

# Step 1: Extract all 0s and 1s
binary = ''.join(line.strip()[-1] for line in dtmf_input.splitlines() if line.strip().startswith("DTMF:"))

# Step 2: Group into 8-bit chunks and convert to ASCII
ascii_output = ''.join(
    chr(int(binary[i:i+8], 2)) for i in range(0, len(binary), 8) if len(binary[i:i+8]) == 8
)

print("Decoded ASCII message:")
print(ascii_output)
```

Moving on from the Python scripts idea, I asked ChatGPT to decode the output of SoX and multimon-ng and give me the flag. This resulted in 2 or 3 wrong flags (Flag 2-4) as it hallucinated badly. I ran the SoX and multimon-ng command again in Kali. I then typed out the 1s and 0s and took the output to CyberChef. Translating it from binary gave the correct flag.

# Flag
Flag 2: C1{r4d1o_k1ll3d_th3_t0rb1a^st4r}

Flag 3: C1{r4d1o_f_k1ll3d_d4_th3_t0rb1a}

Flag 4: C1{r4d1o_k1ll3d_th3_t0rb1a}

Flag 5 (Correct): C1{r4d1o_k1ll3d_th3_t0rb1a_st4r}


