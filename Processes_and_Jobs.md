## Listing Processes 
used ps -ef to find all processes to find /challenge program which i needed

## Killing Processes
used ps -ef | grep "challenge" to find process to be killed then ran /challenge/run to get flag

## Interrupting Processes 
used ctrl + C to interrupt /challenge/run and got flag

## Suspending Processes
ran /challenge/run then used ctrl + Z to interrupt then ran /challenge/run again to get flag

## Resuming Processes
ran /challenge/run then suspended it using ctrl + Z then resumed using command fg

## Background Processes
ran /challenge/run then suspended it using ctrl + Z then resumed in background using bg then ran /challenge/run again to get flag

## Foregrounding Processes
first ran program using /challenge/run then suspended it using ctrl + z then resumed in background using bg then foregrounded it using fg

## Starting Backgrounded Processes
started a backgrounded process by appending & using /challenge/run &

## Process Exit Codes
first ran program /challenge/get-code then used echo $? to find exit code then ran /challenge/submit-code with found exit code as an argument
