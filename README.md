# Magic Circle
MSCH-C220 Final Project
## Theme
In Magic Circle, you play as a wizard trying to hit a ball to the edge of the circle. You can do this yourself, sure, or you can get help from one of your spells - you could throw a fireball at the ball, blast it with a delayed lightning bolt, grow gigantic to hit it with ease, or warp it across the playing field.
The caveat to all of these options, however, and the crux of the theme in this game, is that all of these options are bound to one button. You can cast a spell every few seconds, but the spell you'll cast is randomized. Because the use-case of each spell is slightly different (Fireballs track the ball but don't have the disruption of Lightning Bolts, and Giant Growth is useful up close while Wormhole is best at a distance), it can be a mad dash to follow up on Whatever You Just Did while reacting to your opponent doing the same. 

## Game Play
In Magic Circle, you are placed inside a circle spanning the height of the screen with a ball in the center. You are competing against a (computer-controlled) enemy to knock the ball out of the circle. Neither of you can leave the circle, nor can you cross the center line.
You can move with the arrow keys to hit the ball, similar to pong or air hockey, or cast a spell by pressing Left Shift. The spell you cast will be one of four - you will cast all four in a random order before getting a new order of spells.
- Fireball: Creates a fireball that flies towards the ball's position at its creation faster than you could run. Reliable from almost anywhere.
- Giant Growth: Vastly increases your scale and hitbox to make hitting the ball much easier.
- Lightning Bolt: Create a cloud in front of you that charges up over 3 seconds. After charging, it fires a lightning bolt straight ahead that blasts the ball backwards and stuns anyone (including you!) caught in the area, stopping them from moving for a few seconds. Hard to aim but very powerful.
- Wormhole: Inverts the ball's position, but keeps its momentum. Situational and odd - useful for getting the ball away the your enemy or out of your half of the court, though it's easy to backfire and make things worse.

## What did you 
Magic Circle was an idea I worked on at the IU Game Development Camp two years ago. It was really fun to work on, and I learned a lot about the game development process from it. However, we made our prototypes in a different game engine, and I don't know that I still have access to that original game. My goal starting out was to take the concept from the original idea, port it into Unity, and then add enough new spells that it was impossible to learn all of them in one session.
Very early on, I realized that was completely out of the scope of this project. Instead, I tried to make the most out of the core system, and create things that would be scalable if I decided to revisit this later. I've learned a lot about Rigidbodies and Unity's 2D physics system through this project as well, which was something I struggled to understand in the past. 

## Implementation
Features:
- Art: I drew all of the art for this project in MS Paint. It's not... amazing, but it helps the player understand both mechanically and thematically what they are doing with their spells and their character.
- Animation: I used animator controllers for the stun animation on the player and enemy, switched between sprite renderers for the Lightning Bolt cloud, and used tweening both on the Lightning Bolt as it disappeared and the player to signify that their spell cooldown had worn off.
- Sound: I used Chiptone to make sounds that play when the ball is hit. There are 8 clips, played in order and then cycled again, and each clip is a note climbing the A minor scale.
- UI and menus: The score and streak menus are laid on top of the circle but UNDER the player, ball, enemy, and spells. This is supposed to be a way to communicate the score without forcing the player to look away from the center of the scren, where all of the action was happening. All of the menus in the game occur in the same scene, and they feature a little narrative tidbit on each.
Assets, or resources used:
- [Schoolbell from Google Open Fonts](https://fonts.google.com/specimen/Schoolbell/license?categoryFilters=Feeling:%2FExpressive%2FChildlike)

## Special Focus: Mechanics - 3/5
I designed a lot of the systems in this game to be scalable with more spells and more ideas. I also tried a few things out that we didn't cover in class! However, the end product is still pretty simple, and a lot of what I did didn't get the chance to be shown off. I'm being kind of optimistic with this 3/5. 
- Spells aren't completely random - you cast each one in a randomized order before the list is shuffled again. Mechanically, this meant creating a List of spells and then using the Fisher-Yates shuffle algorithm to shuffle it. I learned about that algorithm while making this!
- The spell system is done through an Enum and a graph that receives a spell enum and the spell's caster as input and matches the enum to a subgraph that instantiates any objects or changes any values necessary for the spell to be made. This means it's easy to modify spells - if the player and enemy both cast a fireball but I want them to cast two instead of one, I only have to modify one subgraph. It's also easy to add spells, because I only have to change an enum and add a subgraph to the spell-selecting graph.
- This graph also means that the enemy can cast any spell exactly how the player would. I was hoping to be able to turn this game into split-keyboard multiplayer, and this system means I can get very close.
- The start menu has branching choices which impact the length of the game, and the start, win, and loss menus appear in the same scene instead of separate scenes.
- I got the chance to mess with and learn about Unity's 2d physics system a lot in this project, and I used a 2d Physics Material, which was something I don't think we covered in class.

## References

## Future Development
- Add! More! Spells! This game _needs_ a big variety of spells in order to work.
- Look into split-keyboard multiplayer? I have most of the work done for it already.


# Created by: Graham Baker
