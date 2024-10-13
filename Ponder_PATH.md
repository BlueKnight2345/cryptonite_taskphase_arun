## The PATH Variable

have to get rid of default path variable so that flag is not deleted

eliminated default path variable using

`PATH=""`

then ran program

`/challenge/run`

in order to get the flag pwn.college{coFKW-ia4qeT4Pg7yaxvgjwuOuD.dZzNwUDL5EDM2czW}

## Setting PATH

challenge required i change default path so challenge program could ran bare command without specifying a path

changed path variable using 

`PATH=/challenge/more-commands`

then ran

`/challenge/run`

and got the flag pwn.college{4Hj7x7S8gdAk7RweNhVB6mim6RF.dVzNyUDL5EDM2czW}

## Adding Commands

this one took me many tried but the final solution was very simple

initially i thought the path variable only had to contain the locations of the win script file and the cat command
so i tried doing that but kept bumping into errors
then i realised i could just add on the directory i need to the path variable

so i used

`echo $PATH` to find all the directories in the path variable

and got `/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`

and i added on the home directory 

`PATH=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker`

then i created the needed script file

`touch win`
`nano win`
`cat /flag`

then i rad the command `/challenge/run`

and got the flag pwn.college{8-QR3DPWfFB2C3v9pp9ZXMYdxh_.dZzNyUDL5EDM2czW}

## Hijacking Commands

This one also took me quite a while as i wasn't quite able to wrap my head around the logic
i first found out where the rm command was in the path and deleted those directories but found those deleted some pretty important commands
after getting a hint from the help tab i found i could just create another file named rm earlier on in the path

first i added the home directory to path using 

`PATH=/home/hacker:/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`

then i created file rm and win (i wasn't sure if i needed both are not and was too tired to try and find out)

i created both and added `cat /flag` to them
then added execute permissions

`chmod +x rm`

then ran `/challenge/run` to get the flag pwn.college{ALZuaD5SGF2gtnm4smU1LNTaWyC.ddzNyUDL5EDM2czW}
