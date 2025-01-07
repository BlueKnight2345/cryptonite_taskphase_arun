# C3

**Flag:** `picoCTF{adlibs}`

Received a python program which encrypted text based on its index values and a file of encrypted text, so I had to reverse the program to decipher the text

The given program (modified a little to make it easier to run for me) is:

```
chars = ""
chars=input("enter your string: ")
lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

print(out)
```

So i had to reverse the steps taken by this program.

I started off by making some basic changes by swapping variables and operations 

```
for char in chars:
  cur = lookup2.index(char)
  out += lookup1[(cur + prev) % 40]
  prev = cur
```

But this didn't really yield results.

So I went through this a few more times

I realised I couldn't just change stuff and needed to backtrack each character within the string.

After accounting for needing to check index values for each character, I ended up with these modifications which worked

```
for char in chars:
  cur = lookup2.index(char)
  test = lookup1[(cur + prev) % 40]
  out += test
  prev = lookup1.index(test)
```

on passing the ciphertext into this program i got this

```
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1
```

using the comments on top i figured i had to input the program into itself

i figured out how to use python with bash but still ran into problems

i finally realised by looking at the 4th comment that i needed python2 while i was using python3

after solving this i was able to get the flag

What you learned through solving this challenge:

1. reverse engineering python programs
2. using python with bash

# Custom encryption

**Flag:** `picoCTF{custom_d2cr0pt6d_66778b34}`

this challenge was definitely much more troublesome than the previous one. We were presented with an encryption script which used two levels of encryption, first an XOR based on a premutation of a known key in the script then conversion of the string to ascii values multiplied by some other values.

The two levels of encryption:

![Screenshot 2024-12-19 144122](https://github.com/user-attachments/assets/111825af-96f6-485c-bf72-1eb9379ebd01)


unlike the previous challenge where i just modified the given script, i decided to start a new script from scratch utilizing the parts of the given script i already had

first i copied the parts which would be needed, mainly the encrypted text, and some key values, then i proceeded to reverse the script.

the first part was fairly simple, needing just some arithmetic:

![Screenshot 2024-12-19 144517](https://github.com/user-attachments/assets/e29db6c3-c25c-41e9-a5fa-fe25c45d9aed)

based on my research on XOR ciphers, i knew they deciphering it wouldn't be hard as if A XOR B = C then A XOR C = B, so the same encryption script could be used to get the plaintext, i just had to feed it the cipher text and make a slight modifciation to when the text is reversed.

![Screenshot 2024-12-19 145942](https://github.com/user-attachments/assets/f632ef15-1185-4255-8d8c-177ae4b9b7a8)

Following these steps i constructed a program to decrypt the given ciphertext and obtained the flag

The entire program:

![Screenshot 2024-12-19 145949](https://github.com/user-attachments/assets/16c1c8ce-93e0-40f5-a0de-cab83992cf8b)

Things I learnt from this challenge: 

1. constructing programs to decrypt messages
2. XOR cipher basics

# miniRSA

**Flag:** `picoCTF{n33d_a_lArg3r_e_d0cd6eae}`

this challenge required the most research to finish. I learnt how the RSA encryption algorithm functions and it's vulnerabilities.

I was given both the public key and the ciphertext and had to decrypt it to obtain the flag.

I knew that the public key, N = P*Q where P and Q were two prime numbers, so i first attempted to use online tools such as factordb.com to find the values of P and Q but this did not work. 

I read the hint given in the challenge 'How could having too small an e affect the security of this 2048 bit key?'. I did some more research and figured out what this hint was trying to convey. in RSA encryption:

c = m^e mod n

where:

c = ciphertext
m = plaintext
(e,n) public key

So the plaintext is raised to the power of e and it's modulus is taken with respect to n.

But, if the value of m^e < n, then the modulus operator would return the value of m^e itself, the mod n would be circumvented.

so:

c = m^e mod n => c = m^e => m = c^(1/e)

so I just needed to find the e'th root of c to get the plaintext.

the only difficulty was python struggled to compute the root of such a large number, so i obtained a function to do this from stack overflow

Using all this i obtained the integer value of plaintext m, which i converted to byte format using python functions from pycryptodome.

The entire decryption program:

![Screenshot 2024-12-20 142024](https://github.com/user-attachments/assets/bf923fcf-75b0-4bc5-9b65-12ccff861f16)


Things I learnt from this challenge: 

1. constructing programs to decrypt messages
2. XOR cipher basics

Other incorrect methods you tried:

- trying to factorise the public key into primes

References

- https://stackoverflow.com/questions/356090/how-to-compute-the-nth-root-of-a-very-big-integer
- https://www.youtube.com/watch?v=wcbH4t5SJpg
- https://www.youtube.com/watch?v=_lg2AEqRTjg&t=206s

# Vigenere

**Flag:** `picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_2951a89h}`

very straightforward vigener decoding with the keyword already given, used cyberchef to decode it

# transposition-trial

**Flag:** `picoCTF{7R4N5P051N6_15_3XP3N51V3_109AB02E}`

This challenge involved a transposition cipher. After doing some reading i understood a transposition cipher involved changing the locations of characters without changing the characters themselves by reordering blocks of specific size of the plantext. Using the hint in the challenge i realised the blocks here were of size three, and as the first word of the plaintext was "the", i could easily figure how the blocks were changed

the ciphertext:

`heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V091B0AE}2`

as "the" = "het"

the changes in location were:

1 => 3

2 => 1

3 => 2

so, i made a python script to decipher the ciphertext

the python script i made:

![Screenshot 2025-01-07 183301](https://github.com/user-attachments/assets/82e31b22-bbe3-412d-9c4f-a6c0d12bfdf0)

the output:

![Screenshot 2025-01-07 183305](https://github.com/user-attachments/assets/d4aea8ab-675d-444d-97bb-d27ccdd02857)

Things I learnt from this challenge: 

1. transposition ciphers











