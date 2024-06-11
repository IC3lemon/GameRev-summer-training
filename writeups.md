***
<br><br><br>
# `dicequest`

The player is a red dice who can kill other small blue dices. \
There is a big blue dice which is a shop. \
If you stay alive long enough bunch of dragons spawn and the player dies. \

This is what the shop looks like : \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/9392904e-a0f0-4ec0-8511-94df8ff3e582)

So I figured we have to somehow buy the dragon taming thing \
I figured why not just make bro rich so he can buy it all. \
the idea was mainly inspired from : https://gamehacking.academy/pages/1/05/

But wesnoth (the game shown in the link)was a Windows game on which Cheat Engine worked \
I went looking for something like cheat engine for linux \

And that's when I found my bro PINCE \
https://github.com/korcankaraokcu/PINCE

So I ran PINCE, first scanned for 0 \
killed a few cubes my money changed to 20 \
then next scanned for 20 \
found the variable that changed from 0 - 20 \
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
<br><br><br>
***
<br><br><br>

# `Lost In the dungeon 1`


unity chall again because I cant get enough \
This is a two parter, it got 2 flags 

### Part-1

so on playing the game, its a 2d game where \
the player is in a lobby kinda place with a bnuch of npcs, \
there's a mage and a portal, theres an old guy by the tree, \
and theres a guy by the stairs. \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/fac42bc8-3b0a-405d-a2c3-fe802901e9c6)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/4dd76fb1-99fc-4d79-abaa-c2f29967b875)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/469702ae-d909-431a-ab4f-97644b16dbe5)


Stairs go into a long aah hallway. \
hallway was long af, too long \
So first thing we need is speed

Opened the thing with dnspy \
and found the player class. but that wasn't handling movement, althought it was taking input for it \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/a2f8c33b-65c0-4ef5-9b1d-b05280e3c722)

the input was being sent into a function `o` as a vector3 that was in Mover script

In `o` the inputs were being multipled by float variables `br` and `bq`  and stored into `bo` \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/50ab350c-f516-4b38-afc0-1e88b09cf58a)

and then the movement was given to the player based on this bo \
i.e. we increase bo, speed increases, how to increase bo ? increase br and bq \
So i set em to 5 from their default value 0.5 \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/b8291a9f-5ceb-416a-93b8-f5a298dc741e)

speed hack on

then when I reached the end of the hallway there were a bunch of skeletons who stick to u, \
get in ur way and dont let ur ass move at all. \
I figured I gotta make them stop doing that.


I went to the enemy script \
and in the start method, \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/e4bbbe0f-a541-49ff-995f-cd2bc7fefa12)

I saw it was taking in the Player's transform \
this was probably being used to detect where player is and stick to them \
so what If I just set player transform to their own transform ? \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/3f5bf8af-6444-4c1c-9ed3-f01fd89d358c)

and yes, they didnt move

![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/a593b41d-1a41-4d36-bb9c-82a3f1f1a49b)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/afac0112-57eb-4dd2-93c5-ef13a45f8e7e)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/ff0277b6-1ba9-46c8-9870-362bfbf9e7e1)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/7e1522e0-88db-4332-923b-26c3f08543b5)

```
nite{Eb1c_9aM3R}
```

<br><br><br>


### Part 2


Now the next flag. \
My first thought was it was off the map \
I gotta remove the collider.

But that was no good, there was only oblivion outside the walls, \
I then found the Portal script \
There it was checking if ur nametag was Wizard, \
If yes, It starts a scene at random out of all scenes. \
I removed the check and decided to go through each scene, \
but luckily, on scene 0 \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/4b021673-1e5f-4102-9ad9-20115d09319b)


So I gotta respawn in here \
I looked through the code to find anything related to respawning \
and sure enough \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/9ac57572-b4a2-408a-a8b1-ca442a83f942)


this function `l` set the players location to that of the respawn point. \
So I made a function to respawn when u press l. \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/bbc0fdcf-bb53-4315-9659-0c52ecd8ae3d)

and yes
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/f29891a7-59b9-4872-a22e-c275b81fa7ce)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/b26a20d2-686a-485d-aee9-3bbf09181ce7)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/e38f7377-5c4b-4a57-91fd-cc6b963923f0)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/8e5016c0-086a-4cad-8b57-a79a71de84cd)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/1c62031c-e822-4cf3-936e-16290ad7fc71)

```
nite{L3vel_100_Mafia_b055}
```


<br><br><br>
***
<br><br><br>

# `FPS Frenzy`

Like the name, the game was a basic fps shooter game. \
A pretty good game actually. Fortunately its a Unity game.\
Initially had no idea where flag was, I increased the health and killed all enemies. \
but no flag on winning. \
there was something prominent on the map tho. \
and harshith also said this : \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/40ad7f8d-a332-451d-a48d-b24959b66a36)

So to get up there somehow, my first thought was to increase jump. \
So I opened up fps_Gameplay.dll in dnspy, found the Player Controller Script and did this : \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/37fa39b6-58fa-41f3-b283-0441295ca6c6)

then I got on top of there and yes : \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/0c74c9ca-8169-41ad-b6d7-05ba5f10e116)
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/7f6b7ae4-af36-41e9-b650-2e5340400809)

```
bcactf{7H3_14w_of_c0S1nEs_4b723470334e}
```


<br><br><br>
***
<br><br><br>

# `pwnadventure 3 : Unbearable Revenge`


the game was op, this was insane. \
Couldn't set up server because some issues I faced when setting up server host \
So I cracked the game on local and decided to exploit it like that as much as I could. 

So in the cave u spawn in, there's the fireball u can get \
and it uses a decent amount of mana, So i instantly booted up CheatEngine \
foung the mana's variable and set it to an unholy amount \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/ba386849-f4cb-45c3-b2c0-73fa0a1d2ede)

![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/3ea2580e-7d0d-42e1-9fc4-15e8ec3b41a6)

I tried bumping up health, it was a hard task, because too many variables kept track of health \
but then managed to boost it. \
afterwards, reached the shop where I made my boi rich and bought a revolver \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/b0dd914e-716c-4927-b8b7-5754fff76a09)

Then I felt a problem with the revolver, it needed to reload \
that made it annoying honestly \
I then increased the revolver bullets to an insane amount the same way \
![image](https://github.com/IC3lemon/GameRev-summer-training/assets/150153966/a354e80d-6d08-4b1b-936c-1085f414168e)

then I found the bears, it was a cakewalk, shoot them, and the health don't let them kill u either \
then I roamed around until I found the bears and the quest started, \
you had to survive for 5 minutes inside the zone while they tried to kill you \
the bears did insane damage, but the health boost tanked it \
after the the timer, killed the rest of the bears and got the flag from the chest \
`they couldn't bear the sight of you`
