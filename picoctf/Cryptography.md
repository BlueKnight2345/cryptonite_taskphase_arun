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





