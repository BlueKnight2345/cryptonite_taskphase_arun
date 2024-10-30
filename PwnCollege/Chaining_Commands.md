## Chaining with Semicolons

have to chain two commands together to get flag
executed commands: 

`/challenge/pwn;/challenge/college`

got flag: pwn.college{4ZgnZro24xWYbxfzyh1T1L09RCm.dVTN4QDL5EDM2czW}

## Your First Shell Script

This challenge required I write a shell script

first made a file using:

`touch bash.sh` (the challenge specified I had to use x.sh but I forgot and it doesn't appear to have made a difference)

then added commands to script file using

`nano bash.sh`

`/challenge/pwn`

`/challenge/college`

then ran file using 

`bash bash.sh`

and got the flag pwn.college{Q7BoLArSu4xuyx5GXr-2rqaYjYu.dFzN4QDL5EDM2czW}

## Redirecting Script Output

as in previous challenge made a script file using

`touch script.sh`

then added commands using

`nano script.sh`

`/challenge/pwn`
`/challenge/college`

then piped output of script file into required command using

`bash script.sh | /challenge/solve`

and got the flag pwn.college{khLO8ggJfV2zrSXmZPmkYwz3fbt.dhTM5QDL5EDM2czW}

## Executable Shell Scripts

Challenge required I execute a shell script without using bash command

made a script file using same process as previous questions

`touch exec.sh`

`nano touch.sh`

`/challenge/solve`

then added execute permissions for the fule

`chmod ugo+x exec.sh`  

then executed file using

`./exec.sh`

and got the flag pwn.college{MZsZLrGIs5w_9VaryLQ2Ka_qQvA.dRzNyUDL5EDM2czW}
