---
layout: post
title:  "Flying Monsters"
date:   2020-11-09 19:47:00 -0400
categories: [gamedev, danmakui]
---
# Flying Monsters

So, it has been a time since I worked in the game, as always after some months the first problem was to get accustomed to whatever the hell I wrote back then and I noticed that on my last day of messing around with the code I left a lot of errors so I started working on that.

After The Seger and the Chaotic Hounds were done it was time to fix the Flying monsters.

In their current state the current monsters would detect the player from any place in the map but that wasn't the worst part, that would be their infinite shooting range.

Their code is pretty simple, They have 
Rate of Fire
Speed
Stopping Distance
Retreat Distance

Rate of fire is of course how much time there is between each shoot, speed is self-explanatory, Stopping Distance is how far away/close from the player they get to start shooting and Retreat distance is how close they let the player get to them before they start retreating a little bit.

This is all well and good but now I had to implement their behavior and change it if there was a Seger moving around and that code gets pretty messy having to move variables around between different scripts, this is specially bad after just coming back and not knowing what was what as I said before.

So much so that I really couldn't figure out a way to do this so I used desesperate methods.
I used the same Movement Script that I used for the Chaotic Hounds for the Flying Monsters, This code was already prepared to deal with both the Seger and the Player just needed some activations and deactivations of scripts based on the Layer the monster was in (Flying Layer) and done!
Except not.

The Chaotic Hounds use the wonderful "Seeker" Script from the A* Project for Pathfinding this is the most basic follow script that thakes into account the Walls that  the A* uses and rushes to get close to the target.
Messing around with some extra conditions to allow for the behavior of the Flying monsters allowed me to use the same Script while they still accomplished their function of range shooters except for a little thing, they respected walls.
That's awful! bad! bad! bad! They are the flying units they are not supposed to respect the walls and thus make paths that traveled between them! They are supposed to fly through them like the flying monsters they are!
So I started to search for ways that allowed them to Ignore the walls while still using the Seeker script I wasted a couple of days with that. And I say wasted because I couldn't find what I wanted, the Seeker Script was useless for a flying Monster, The Pathfinding was unecesary for a monster that doesn't has any obstacles to traverse.

So I went back, made a Flying monster from the start using only what worked for the basic one I mentioned before and started adding conditions.
The most important ones being: 
Is there a Seger Around?
Is there a Player Around?
Is the Seger Playing with my mind?

If there was a player the monster goes to attack the player.
If there was a Seger around the Monster would recognize it but do nothing about it But if there was a Seger around the monster would be susceptible to becoming obsessed with the Seger and rush to it, that would be the "Having his mind played with" condition.

Now there is a division between the types of the Flying Monster.
The Vigilant one and the Obsessive one.
The Vigilant one is found around the Seger, but as soon as it sees a player it will attack it and follow it around.
The Obsessive one will stay with the Seger and attack the player only from where it is, it will only move around if the Seger moves around.
It finally works properly.

So, what is the big lesson from this? Well, I think it is mostly that often you will find branching decisions on how to approach a problem, you will have to choose and you don't know if that decision will bring you to the solution or if It is just going to eat 3 days of development only to fall back and go the other route, I think this is a quite precious lesson, while you can consider your options sometimes both ways will look sensible enough to follow, you will just end up taking the one that you can't solve and that can't be helped.

I made some effects for the impact for the bullet against the floor too in FX designer and added some SFX from all those humble bundle packages.
Now I need to go and take one big step. 
Finally make my player killable, which probably should have been something I had to do way way earlier.
 

