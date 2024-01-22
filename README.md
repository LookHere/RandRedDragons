# RandRedDragons
Table top role-playing is all about statistics.  Why not have R manage a campaign? 


## Adventure Spirit in Code

If there is one thing that table top games teach us, it's that exploration can lead to great things.  I want to explore how to integrate the amazing statistical capabilities of the R coding language with the dice rolling mechanics of table top games.  I’m also using this opportunity to explore how Ai can help me write code and text.  

I’m always looking to build a party, so if you’re interested in joining the adventure let me know, all skill levels accepted!


## Rolling Rocks Engine

### What’s in an Engine?

In table top gaming role-playing there seems to be a spectrum between modern rules heavy games (that could be challenging to run) and “rules-light” systems that lean into more acting and negotiation.  Both ends of this are intriguing and have their own values.  My quest is to create something that allows for as many rules as the players want, but removes the administration (at least as much as they want).  To do this I want to abstract a system that is flexible, but lends itself to running the work that no one wants to do.  It’s functionally the “hierling” of an adventure party (someone you pay to carry your stuff and do the things you’d rather not).  I call this engine “Rolling Rocks”.

The basic idea of rolling rocks is that we want to minimize the administration of table top games so that they're easier for people to enjoy, which leads to better stories.  You should be less mentally exhausted at the end, and more emotional exhausted.

At the time of this creation there is a similar movement to use Large Language Models (LLMs) like ChatGPT to entirely run quests.  That doesn’t seem to make a lot of sense to me, since LLMs currently struggle with keeping track of a lot of user specific data over long periods of time and aren’t good with large overarching plot lines.  

In this project we’re using R to do data (inventory) management and statistics, which it’s great at.  The humans will do the human interaction stuff (even if an LLM can produce more flowery language) and the over arching structure.  We’ll use the Ai to help write the R code and pull together details and phrases for the story line.  Hopefully this will use each stakeholder (human, R and Ai) in the area of their strengths.

### Structure

To build an engine we need a structure.  We could just copy the rule set of something like Pathfinder or Dungeons and Dragons, but in the hopes of being flexible and creative we’re trying to abstract the rules to a higher level, and then let the players decide what pieces they want and which don’t work for their table.  The Game Master (GM) will pull in (or create) universes and will tune the physics so that it’s right for the players at their unique table.




#### Actions

There is no difference between taking an action and hitting in combat. 
Picking a lock or swinging a greatsword use the same mechanic.

Actions are assumed to be successful, and the dice are just used to work out the details.
There is no attack roll, just a damage role.

State what action you'd like to do, the GM will add your modifiers, and then you roll.
(The GM decides if they want to tell you the modifiers before the roll, or just tell you the success/failure after).  Rolling can be done with physical dice or by the computer, whatever the players would like.

This table describes what happens on the role after the modifiers are added.

- worse or equal to -10 :       you fail at your attempt and the thing you're using has a major break reversal
(ex. sword cracks in two and stabs the wielder in their foot, spell is reflected back at its caster at 2x power, etc.)
- between -9 and -5   you fail at your attempt and the thing you're using has a minor break
(lockpick set is bent and needs a expert to repair, a page in a spell book is smudged and can't be used again until a library repairs the page)
- between -2 and 0    you fail (you miss or target, the lock is too hard for you to pick, etc.)
- between 1 and 5     you succeed, but your attack is divided by 4 (round down, minimum 1)
- between 6 and 10    you succeed, but your attack is divided by 2 (round down, minimum 1)
- between 11 and 15   you succeed
- between 16 and 20   you succeed, and your attack is doubled
- between 21 and 30   you succeed, and your attack is tripled
- rolls over 40 are quadrupled, over 50 are quintupled, over 60 are sextupled, etc.

The scale of this is designed to have high variability between positive and negative actions.  Every attempt has a real risk of failure, which encuraging them to find creative ways around problems.  That quickness also helps keep combat quick and light (which is both more realistic and exciting), and make sure it doesn't weigh down the story.


#### Naturals

If you roll a 20 sided dice and it comes up 1, you automatically fail and subtract 5 points on the above table

If you roll a 20 sided dice and it comes up 20, add 7 to your roll and the GM may give a new modifier.  


#### Opposition Rolls

There may be cases where there is opposition, such as if two characters want to arm wrestle.
They both roll their dice, add the modifiers, and subtract the rolls from each other.  
The difference is given to the player with the higher roll.
If both players roll negatives, then don't combine the rolls, just give each player a negative.
(For example, if on an arm wrestling opposition, one player rolled a -2 and the other rolled a -6
you could say the table breaks and injures the second player.)


#### Modifiers

In a lot of systems the modifiers are inherently part of the rules.  Things like class and race have inherent modifiers and/or characters can add points to Dexterity or Wisdom.  To make this system as flexible as possible, all of these are abstracted into the idea of modifiers.  That way things like race could be used on a D&D style adventure and omitted for a space horror game.  It also allows the GM decide how many modifiers they want to be dealing with, so the game is always
manageable no matter the GMs skill level.

Modifiers can be either strait math (ex. +2 or -5) but it's more fun if they are dice rolls (subtract 2d12 from what you roll).  This make GMing easier because it adds in complexity without adding in administration.  For example, instead a GM deciding the difficulty of every lock in a compound,
they can decide that lock checks have a subtract 1d6 from all picking attempts, making some rooms 
easier or harder to break into.  Doors in a more affluent part of town could have a negative 2d8 lock modifier.

Spending more time on gathering modifiers lets the players be more creative in trying to stack
the deck in their favor with what's around them (instead of grinding or waiting to get to a higher level).

Each universe will have a core set of modifiers decided by the GM, but it's encouraged for players
to use their surroundings and wits to develop modifiers on the fly.

#### Health is wealth

Health is a scale of existence.  When help drops to zero, then the thing no longer exists.  

But health can always be improved over its current state.  For example, a standard chair might have 5 health.  If a Giant Himalayan Yeti sits on it, the chair takes damage.  If its health drops to zero then it breaks into multiple pieces and is no longer usable.  But if an engineer welds metal reinforcement on the chair beforehand, it raises the chair's health to 20, which means it's strong enough to support the Tibetan ape-like creature to sit on it.

Instead of leveling up, a character has more health added to them, which represents an increase in
their physical strength or mental will power.  Just like reinforcing the chair, increasing the character health raises their quality.

Everything has a Standard Health and a Current Health.  

The Standard Health is just the health they'll come back to after a good night's rest, a trip to the doctor, or a repair (depending on your universe).  This only changes when the GM needs to reward to take away from a character based on the rules of the universe.

The Current Health can be decreased (through falling off a cliff, being attacked, etc.) or increased (through a healing spell, taking prescription drugs, etc.).  

Current Health can go above Standard Health when explicitly stated on the modifier (acting like temporary hitpoints).

When the Current Health hits zero the item is broken (or the character dies).
Chairs can be re-built, but humans can not come back from the dead...unless your GM allows it.
Each universe can have different rules on how permanent death is but we'd suggest something that encourages a respectful, but not surprising exit.  An honest risk of death makes the game more exciting and also encourages the players to think twice about their action.

One common mechanic for decreasing the bite of death is when a character hits zero points they are
just knocked out, and then are allowed to roll again each time their turn comes up.  If they have
reach 3 failures, they die; if they reach 3 successes, they are stabilized.  If another player reaches
them, that player can help stabilize them.


#### Specialties 

Some people are better at things than others.  The GM can modify the feel of the game greatly by deciding how easy it is to specialize.  

If a GM wants a classic D&D style game, they would give heavy modifiers for specialties (for example a barbarian could have a +2d8 rolls when using heavy weapons).

If the GM wanted a more modern feel like Kids on Bikes, they would only use light modifiers for specialties (for example the history nerd would have +1d4 roll on town lore insight check).

We'd suggest going really light on specialization at the start, and then adding them over time based on 
the actions the player makes so it feels like character growth is more organic .  If they use their cross bow a lot, reward them with a crossbow specialty modifier after an especially impressive natural 20 roll.

Specialties are really useful to balance if you're using extreme character types.  You may give your 
fighter some big increases to their health maximum, however you'd give your wizard a smaller health
increase and instead give them a specialty increase of 1d8 when casting spells.


#### Universes

The tone of the game will be dependent on the universe the GM creates.  
Part of the tone will depend on the actual story telling features (location, characters, factions, etc.) but a larger part will depend on how formalized the universe is and how harsh the rules are.  Some GMs enjoy building a very formalized universe, where they write pages of backstory that players might never see.  Some like harsh rules, where permanent death is common for their players, pushing
them to create new and interesting characters.  Tweaking these universe settings is the best way to 
develop the right style game for your players.

We recommend you start small and build on it.  It's better to develop complexity and risk over time.

The pre-built universes are mainly collections of things and their modifiers, that a GM can reference
to make their life easier as they develop their own universe.


#### Stories

Every adventure needs some conflict.  A GM should have at least some loose story points or ideas that lead the players onto an epic adventure, but the actual story telling is done by everyone's actions and different perspectives.  

Pre-built stories bring in concepts from other writers that the GM can use to add excitement.  However a GM adds the most value by bringing in their own creativity by mashing other ideas together.

An easy way for a GM to develop a story is to base characters on something the GM knows in real life 
(friends, movie characters, countries, etc.).  Why not have your Lich King's secret plot based on what
Christopher Columbus did in North America or have your Ship's Captain act like your math teacher?

Similarly, when building a world map, you can just trace a copy of a map of your own town, and then 
turn it upside down before you put fictional locations on it.  That way you always know your way
around, but it's a magical realm for your players.

Why not pull in mini-games for your players that affect their role playing.  If your players love look, bring them to a casino and then have the players interact with an online blackjack game. If you’ve got a short board-game on the shelf, weave it into the story and have the players compete in that to decide what happens in their roleplaying.  If a barbarian character needs a few extra points for an important roll, have give the player one point for every 5 push-ups they can do.  The great thing about these adventures are that we decide our own limits (as a character or DM), not a book or computer game.



#### Why did we make these choices?

There are a lot of amazing table top platforms out there, so why not add another? Adding one more to infinity doesn’t make things any more complicated.  

But we found a lot of platforms had elements of the story ingrained in them, and we felt that discouraged creativity and ingenuity.  The goal of this system is to get to a level of abstraction where the GM and players can very easily add in or remove any part of it, and the rest should (generally) work.   

For example, if you love the classic D&D setting, but hate the concept of race affecting characters, you can just remove that modifier and the rest of the game just works.  More importantly it allows the GM to tune the game difficulty, flexibility, and risk to fit the mood of the table or even though different parts of the campaign.

Having everything based on modifiers creates a level playing field that should help the GM more intuitively set up balanced settings and the players more easily undersatnd the risks.  If you've established that riding a horse is a negative 1d6 modifier, it's easier to decide on the fly that something like a negative 2d10 is reasonable for riding a shield down a sand dune like a snowboard.  We can create a sense of how hard all things are in comparison to each other if they’re all using the same system.

At a more advanced level, this really helps us use our dice more effectively.  Rolling a 1d6 gives equal 
odds between 1 and 6.  But rolling 2d6 increases the odds to the center.  By putting positive or negative modifiers we can shift or manipulate the chance curve.  That creates a lot of opportunity for the GM to balance (or unbalance) the game in ways that support the story, while still leaving a wide opportunity for unlikely surprises.

It also helps create one system for managing everything (working a lot more like a video game) and
it strengthens everyone's fundamental understanding of how statistics works.


# Roadmap

- [X] Develop a structure
- [] Create something where your health modifies certain actions
- [] Develop a prompt creator that takes the actions in the game and uses Ai to express them in fun ways. Take the universe and character descriptions, add the items they hold, and the actions they took to develop a prompt for Ai to create a story or image.
