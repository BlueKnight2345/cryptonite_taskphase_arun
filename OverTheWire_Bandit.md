## Level 0

logged into the game using ssh

`ssh bandit0@bandit.labs.overthewire.org -p 2220`

## Level 0->1

read the readme file to find the password 

`cat readme`

password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1->2

had to read a file named '-', found out this isn't straightforward as '-' is an argument for cat

so used 

'cat ./-'

and got password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2->3

had to read file name with spaces in it

used

`cat "spaces in this filename"`

password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3->4

found hidden file in mentioned directory using `ls inhere -la`

then changed directory `cd inhere`

and read using `cat ...Hiding-From-You`

password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4->5

multiple human readable files were present, had to identify which were human readable

found out `file` command could used for the so decided to go ahead with it using globbing

all files began with '-file....' this was an issue as '-f' has other meanings in Linux apparently 

so used path instead

so globbed `file ./-file*` and found which file had ASCII text and read with `cat`

password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5->6

