# Trivial Flag Transfer Protocol

**Flag:** `picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}`

Received a pcap file and opened it up on wireshark

It displayed a large number of packets

Going by the name of challenge, I exported all the TFTP packets and got the following:

![Screenshot 2024-12-12 235702](https://github.com/user-attachments/assets/8714e133-6a8e-44a8-86b7-938f1ca6397f)


The instructions.txt file contained a large string of characters

`
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
`

I ran it through cyberchef using a ROT13 and got the following

`
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
`

the file 'plan' contained another string with on decrypting with ROT13 gave

`
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
`

Also included in the exported files was a Debian file. 
I used wsl to install the program included in the Debian file, the program is steghide

So, i needed to use steghide to analyse the given images


After taking a while to figure out steghide syntax i used the following on all the bmp files given

`steghide extract -sf picture1.bmp`

and i used the passphrase 'DUEDILIGENCE' as was mentioned in the previous file's message

with the 3rd image, i managed to extract the flag file


What you learned through solving this challenge:

1. using wire shark to analyze pcap files
2. using steghide to perform steganography 





