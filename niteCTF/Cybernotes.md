# Cybernotes

This one really threw me off as I had no idea what to do

Initially I tried entering someone common-ish usernames and passwords and then moved on to inspecting the webpage and trying to find anything useful, this also did not yield anything useful. I moved on to trying to figure out the forgot password page and trying to analyze that as well but I realised it was a genuine comic with many editions so it was unlikely that there would be anything of note there

After seeing the writeup i have a pretty decent idea of what's to be done

the solution is python script which tries to exploit a vulnerability in the site's JSON token authentication system

first we create a login request with a fake JSON token to get a response from the site

then we decode the fake token and reencode it with the secret key from earlier in the program

then we send the token back with the valid key to get another response from the site which now prints the flag
