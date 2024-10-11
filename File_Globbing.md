## Matching with *
ran cd /ch* to challenge directory to /challenge
then ran /challenge/run to get flag

## Matching with ?
ran cd /?ha??enge to change directory
then ran ./run to get flag

## Matching with []
changed directory with cd /challenge/files
then ran /challenge/run file_[bash] to get flag

## Matching paths with []
used challenge/run with mentioned path to files
/challenge/run /challenge/files/file_[bash] to get flag

## Mixing globs
this one was very annoying, knew i had to find some commonality between all three but still something that wasn't too broad, tried *i*,*n*[gal] and a lot of other things
[cep]*n* worked but it was too long
after brainstorming for far too long, [cep]* works, feel dumb
ran /challenge/run [cep]* to get flag

## Exclusionary globbing
navigated to /challenge/files and ran /challenge/run [!pwn]* to get flag
