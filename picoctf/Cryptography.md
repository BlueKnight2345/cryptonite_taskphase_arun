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









