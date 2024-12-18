# Flight Risk

On seeing the writeup this challenge was quite simple but i wasn't really able to get it the first time

I assumed the flag would be somewhere within the gamefiles but this was very far off, so I spent my entire time going through the decompiled exe file on IDA but this yielded nothing

The solution was to alter the game files on ida, specifically those which prevented us from winning the game, which is a hint i should've gotten.

So to get the flag, after opening up the game on IDA, the missile and terraingenerator classes are modified to essentially nullify them.