## Changing File Ownership
used chown to change ownership of /flag file to user hacker then used cat /flag to get flag

## Groups and Files
changed group of flag file using chgrp hacker /flag and read flag using cat /flag

## Fun with Groups Names
used id to find out what group the hacker user was in then used chgrp to change flag file to that group and read the file

## Changing Permissions
changed permissions for flag file making it readable, writable and executable by all users using chmod go+rwx /flag then reading using cat

## Executable Files
i was meant to give execute permissions to all other users but it only worked when i gave perms to all possible users, so had to use chmod ugo+x /challenge/run, not really sure why as this wasn't specified in the question

## Permissions Tweaking Practice
solver 8 rounds of changing rwx permissions of ugo to get flag

## Permissions Setting Practice
set permission instead of change using u/g/o=rwx 8 times as required and did same on /flag to get flag

## The SUID Bit
added Set user id bit to required file so that anyone with execute permissions can run file as owner then read flag file to get file
