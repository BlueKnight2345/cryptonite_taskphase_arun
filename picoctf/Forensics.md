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

# tunn3l v1s10n

**Flag:** `picoCTF{qu1t3_a_v13w_2020}`

Recieved a file which when i tried opening up on wsl spewed a large amount of data and couldn't be executed, so as a similar program was encountered on OASIS i decided to open it up using a hex editor

On analyzing what i saw on the hex editor, I found it was a BMP file with some corrupted parts with the bytes removed on replaced with 'BAD'

So i did some research on how the bytes in a bmp file are meant to look

After looking into it, I found out the two 'BADs' were meant to be the file's pixel data offset and header size, standard hex values for both appeared to be 36 and 38, on modifying this i obtained an image

![Screenshot 2024-12-13 002411](https://github.com/user-attachments/assets/14ab6794-834f-4c09-ac80-1b24939a620c)

So, some more adjustments were needed

I thought perhaps the image was cropped, so i could vary the image size parameters in the bitmap and try some things

After some fiddling around with the values for the height of the bmp image and more research on what values could be accepted, i ended up with this 

![Screenshot 2024-12-13 003013](https://github.com/user-attachments/assets/4ea89d1d-5731-4945-9ace-18dd757c17ea)


1. using a hexeditor to analyze and modify the hexdump of files
2. analyzing hexdump files

# m00nwalk

**Flag:** `picoCTF{beep_boop_im_in_space}`

this challenge gave me a .wav audio file. i tried various things such as using an audio analyzer and a morse code decoder but these did not yield any results.

I read the hints on the challenge which said 'How did pictures from the moon landing get sent back to Earth?'. After a bit of research, i found the answer to the hint was SSTV. i found out SSTV could be used to convert audio to images.

So i went about finding an app to do this. i tried both RXSSTV as well as QSSSTV however I had trouble using both of these and turned to an android app called Robot36 to decode the audio and i got the flag.

![Screenshot 2024-12-18 221320](https://github.com/user-attachments/assets/9120622d-9b0b-485f-889d-3a4be1486856)



Things I learnt from this challenge: 

1. usage of SSTV













