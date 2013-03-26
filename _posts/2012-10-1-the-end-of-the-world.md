---
layout: post
post-title: The End of the World
synopsis: when my site died and I lost everything
---      

# The End of the World        

Not too long ago something terrible happened. I'm not sure exactly what caused it, but I have my theories. Maybe a tiny meteor managed to make it through our atmosphere, and hit land at just the right spot. Maybe it was a that group of ex-KGB agents I had a run-in with; they have a very particular set of skills. Maybe it a server upgrade. Maybe it was ninjas. Probably it was ninjas.

Nobody knows for sure, but whatever it was (it was ninjas!), this site was down. For weeks. I kind of decided to just let it go until I had the time and energy to go through the process of bringing it back online. I don't get a lot of readers, and I don't post that often so no biggie, right? When the time finally came, I just assumed it would be fairly simple; how much damage could be done, after all? Enough.

## The Resurrection

I decided to start the process yesterday. Honestly, I wasn't sure where to begin beyond the database. So step 1: back that bad-boy up!. My host has a simple 1 click method to backup your DB and download the .bak locally. They also have a simple restore process (maybe they all do, I don't know), so I figured I was golden. 

With backup in hand I began the process of upgrading the site. I made my first mistake right away: I tried to do this from a computer with a metric ton of restrictions on internet use (shhh... don't tell my employer). The orchard in-place upgrade is actually pretty simple. Delete everything in /bin, delete stuff from App_Data, get newest version locally, move it to your server. TA-DAH! 

Right. Well, my restrictions completely prohibited that. On to plan B: full-on reinstall of Orchard via the Web Apps gallery from my host. No big deal if I lose my settings or theme. I wrote the theme; packaging and install is "mad simple, yo." Plus, I have have my DB backed up so I can install Orchard, restore the DB and VOILA!

Wrong again. The only thing that went as planned was the vanilla install of Orchard.

**Problem 1:** Turns out I don't actually have my theme packaged up. That's OK, because I can just package it up, right? Well, yeah, sure if I have Orchard installed locally. Now, when I say installed, I mean **INSTALLED**, not downloaded and unzipped. Orchard.exe has a packaging command, but it's dependent on the packaging module which only exists if you've got a running instance of Orchard. Once that was done, packaging and installing the theme was also "mad simple, yo!"

Honestly, problem 1 was easy to fix. It was just an unexpected pain, but we learn from pain.

OK, quick status check:

1. DB backed up
2. Orchard installed
3. Theme packaged
4. Theme installed
5. Time to restore that DB, son!


The restore function provided by my host worked as you would expect and I had my DB. 

**Problem 2:** Ruh-roh! My site no longer works? Yep. Something was rotten in the state of Denmark and it clearly had to do with the DB (right?) I should have known when I looked at the size of the DB after I restored. It was significantly smaller that the pre-restore DB. Still, I couldn't let the idea that I had lost my data seap into my head, so I set off to restore it locally. I won't bore you with the details of the string of calamities that occurred next. Suffice to say I don't have my data.

## A Clean Slate

Frustrating, don't you think? Luckily, as I said before, I don't post much. We're not talking about huge amounts of data going lost, but still, I had people actually reading my posts! That really sucks. Don't think I'm giving up though. One way or another, I'm getting my posts back. I don't care if I have to copy them from Google's cached version of my pages. I'm going to get them back, and I'm going to finish up my series on Composable View Models (really!).

And the next time those ninjas come around, I'll be ready. I've been practicing. I have serious nunchuck skills.