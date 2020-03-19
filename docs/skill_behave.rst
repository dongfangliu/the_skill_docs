What may a skill behave? (Not essential but helpful)
============================================================

There arebasically two type of skills, active skills and passive skills. The difference iswho triggers the skill , the former is triggered by user, the latter istriggered automatically under certain situations.

Skills can also bedivided into point type and non-point type, the difference between the two isthat the former has the characteristics of tracking objects.

So let's imaginea classic wizard casting a fireball on Goblins to see what a skill involves.

First of all,you can imagine an old Master wielding his staff singing (that is, what we aretalking about singing), maybe the staff will flash, which will last for sometime. If during this time he was attacked, piu~, the fireball went out, theskills were interrupted, so the skills had to end.

Well, aside frombeing interrupted, suppose the singing ended smoothly, we can see a fireballflying from the top of the staff, hit the body of the Goblin, Goblin's body lita flame, And Goblin lost a lot of health. Now is the end of the skill.

Okay, let's sum it up.

First we see that there are 3 subjects, mages, fireballs, and objects to be hit by thefireball (maybe Goblins moved around) throughout the process.

I noticed that the mage himself needs to complete a series of actions (animations) in the release of his skill, his status changes (consuming his mana ?), He needs tofly a fireball and the fireball hits the Goblins, if this is a non-point typeof skills, then the fireball may hit the stone (Goblin moved), the stone will not hurt (this involves the skills that can affect those objects, the enemy?Friendly? Or no difference?) If this is a point-type skills, then the fireball will catch up the target. When a fireball hits a goblin, the goblin can fall or suffer a continuous injuration (damage is settled).

Let's tidy up the whole process.

Cooling StateEnd -> Skill Trigger -> Skill Singing (may be interrupted) -> Emittingan object to a location or an object -> Emission is triggered -> Skill isreleased (may last for a while) - > Skills exit.

What are the elements involved?

Character's own properties (mana amount), character animation, some particle effects (light onthe staff, fireball, goblin flame), skill type (point or not, active or passive), the launch of the object And the extent of its impact, cooldown, as well as the time of each stage. . Oh, quite complicated, right?

In a word we can say that the whole system can be divided into three parts: what happened to the mage (position movement, animation, state change), what happened to the fireball going out (getting smaller?), What happened to the object.

The case of mage is over, what about warriors ? Warriors may emit nothing.It’s okay.

All other final questionscome down to what you want to do at what point throughout the process.

Above is only a single skill, we can imagine a character has a set of skills, Skills that Terran and Mozu can learn are completely different. For developers, we always go through a process of creation to discard. We are not sure which skills a certain character will have. If we wrote it all in one piece of code,it would simply be a nightmire of paste, delete, and prone to bug .

And that's exactly why I wrote this system, to make the creation process of skills tidy ,organized and reusable.

So we have a skill library, similar to a template library, you can create a library, add or delete some skills, change some of the skills of the property or code, you can add an icon for each skill for you to quickly identify it. In addition, we do the first letter sorting on the library.

You can delete this skill library directly, this will not affect any skills node (because we only clone a node into it). This means you can do a lot of trying without worrying about breaking other data.

The template library, of course, does not directly lead to the application, the skill library just said that we may have what skills may be used, but the actual problem is what do the skills tree look like?

What skills are bright, which skills are gray, Which one to learn first to unlock the next skill, what is the level of skills and so on. . .

So in addition to that, I consider a little about the parent-child relations between skills. Because the premise of using the skills is we activated/learned them, and normally the premise of learning a skill is that we learned other skills. So I also simply provide a skill tree used to constrain these relationships, which can be visually constructed.

This is still a step far from the practical application , that is, what’s the status of the skills? Is it cooling or still being cast ? skills are not acquired or just simply do not exist?

I’ve provided completeand automated character skills process management, CoolingDown control, skillstatus querying (Playing, NonExist, NonActived, Free) and acquisition andsetting of skill-dependent variables.

In a word, this is the process for me to mapping out this skill system, hope this can give you a better understanding over this skill system.

