## All that for a drop of blood
this challenge gave me a bit of trouble. After seeing the hint on the discord server i used the modheader extension and set a header User-Agent = OASISPlayer.
this finished the first part, next part required me to add the parameter 'name' with value Cryptonite
third part asked me to add another parameter with cryptonite's rank = 4

## Heads up, tails down
recieved a corrupted png file, which i opened up in a hex editor and saw the png magic bytes and ihdr weren't there
added both of these and uncorrupted the png

## I have been falling for 30 minutes!
got 5 pages with userid values from 1-5, changed value to 6 and got flag

## Stairway to Heaven
ran the file using wsl and got bunch of coloured blocks, copy pasted this into text file but didn't look carefuly enough to find the hexadecimal string in there
tried matching rgb values or colours to find some patters
tried analying a screenshot of colours on fotoforensics
after all this i had another look at the copy pasted text and found what i needed

## Git Gud
recived folder .git
used gitbash to check commit log and found flag
