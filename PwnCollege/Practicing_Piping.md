## Redirecting output
used > to redirect text PWN into file COLLEGE

## Redirecting more output
used > to redirect output of /challenge/run to file myflag then used cat on file myflag to get flag

## Appending output
used /challenge/run /~/the-flag to create file the-flag and first part of flag to it, then used /challenge/run >> /~/the-flag to append second part of flag to it

## Redirecting errors
directed standard output and started error respectively using /challenge/run > myflag 2> instructions

## Redirecting input
directed output COLLEGE to PWN using echo COLLEGE > PWN then directed input to /challenge/run using /challenge/run < PWN

## Grepping stored results
redirected output using /challenge/run > /tmp/data.txt then found flag using grep "pwn.college" /tmp/data.txt

## Grepping live output
'piped' output directly into grep using /challenge/run | grep "pwn.college" and found flag

## Grepping errors
first redirected standard error to standard output then piped it into grep
/challenge/run 2>&1 | grep "pwn.college" to find flag

## Duplicating piped data with tee
used too to run output of /challenge/pwn into a fill so i could read 
/challenge/pwn | tee test | /challenge/college then used cat test to find hidden argument
then ran again using argument to find flag

## writing to multiple programs
it took me a while to wrap my head around this but eventually figured out and piped output of first program into two programs treating them as files input using /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )

## Split-piping stderr and stdout
wrote stdout and stderr into required programs using /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )

