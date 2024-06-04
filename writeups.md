# `dicequest`

The player is a red dice who can kill other small blue dices. \
There is a big blue dice which is a shop. \
If you stay alive long enough bunch of dragons spawn and the player dies. \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/ff9052d0-ad64-4a78-b75f-2592c2e625c2)

This is what the shop looks like : \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/9392904e-a0f0-4ec0-8511-94df8ff3e582)


So I figured we have to somehow buy these items \
I figured why not just make bro rich so he can buy it all.

Had a hard time finding where the player's money was stored, since it was just 0 by default. \
Too many search instances with the value 0.

I went looking for something like cheat engine for linux \
where I could look up the binary's status as I was playing \
To maybe searchup, not 0 but any value that changes to say 30 \
(the money i would have after I kill a few cubes)

And that's when I found my bro PINCE \
https://github.com/korcankaraokcu/PINCE

So I ran PINCE, killed a few cubes my money changed to 20
I searched up instances and there was only one \
I then set its value to an insane phone number \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/3519af27-d5f3-4b24-a46a-f0b0db6a38d5)

my boi rich \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/393a6ff2-e347-48aa-a46e-fce225086e3d)

Then I bought everything in the store, waited for the dragons, and the dragons did not kill me \
they started arranging in a pattern and yes \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/9f73d6b3-684f-4a65-9623-c6be36d83a8b)

```
DICE{YOUR_FLAG_IS_NOT_IN_ANOTHER_CASTLE}
```
<br><br><br>
***
<br><br><br>

# `no way out`

UNITY CHALL LESGO \
game was op honestly, well made. \
The player has an inventory with a bunch of weapons, \
he is in an enclosed place, outside of which there is a huge aah flag \
The objective is clear and on top of the screen, \
*escape and get the flag* \
ok 

Immediately opened AssemblyCSharp.dll with dnspy \
And set the jump value to 50 \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/62ef15b2-2198-4c1d-90eb-7edbb9411c44)

*(I set it to 1k first, but realised thats too high when I launched into oblivion)*

Then I compiled, launched the game, and jumped tf outta that place \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/52e95225-cefb-47f4-b7db-405000674da3)

```
picoCTF{WELCOME_TO_UNITY!!}
```
