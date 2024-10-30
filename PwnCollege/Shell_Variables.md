## Printing Variables
used echo $FLAG to print variable FLAG

## Setting variables
set variable PWN=COLLEGE to get flag

## Multi-word Variables
set variable PWN="COLEGE YEAH" to get flag

## Exporting Variables
exported variable PWN=COLLEGE but not COLLEGE=PWN and ran program to get flag

## Printing Exported Variables
used env to see every exported variable and found flag variable among them

## Storing Command Output
stored output of program in variable using PWN=$(/challenge/run) and got flag using echo $PWN

## Reading Input
used read to set value of PWN to COLLEGE and got flag

## Reading Files
read /challenge/read_me into PWN using read PWN < /challenge/read_me

