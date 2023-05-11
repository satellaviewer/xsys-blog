<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 1.399 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Wed May 10 2023 20:51:36 GMT-0700 (PDT)
* Source doc: X-Kode
----->



# X-Kode

Kode for the default classes included with XSYS, the Extensible Boss Battle System.


[TOC]



## Introduction {#introduction}

The XSYS Boss Battle System is an RPG combat game that can be hosted over IRC, Discord, or both simultaneously.

In a boss battle, roughly five players join as Heroes, and go up against a single Boss controlled by the Referee (or “Ref”). Only the Ref needs XSYS installed and set up– everyone else plays by entering text commands into the chat, and telling the Ref what they want to do. The Ref enters commands into XSYS to resolve their actions and pilot the Boss.

XSYS is also restricted-open-source. If you’d like access to the source code to run it yourself and become a Referee, talk to the dev team and we’ll provide it to you individually. (At this time, we’re not providing full access to the entire world.)


## Section I: Basic Rules {#section-i-basic-rules}


### Joining {#joining}

When the ref opens entries, pick your loadout. That consists of:



* A class, which gives you your stats and skillset
    * To choose a class, see the [Classes](#section-ii-classes) section.
* A Groove, which controls when you can use your Limit Breaks
    * For beginners, we recommend one of the following:
        * H-Groove, which charges as you deal or take damage
        * L-Groove, which charges as you take damage
        * F-Groove, which randomly awards a Limit Turn
        * V-Groove, which steadily awards weak Limit Breaks every few turns
    * For full information, see the [Grooves](#section-iii-limit-breaks-and-grooves) section.

So, to join as a Profaner with H-Groove, use “!enter Profaner/H-Groove”!


### Skills {#skills}



* The loadout you join battle with determines what skills you have.
* Skills without a tag at the start of the name or a color are **Action Skills.** They’re your bread and butter, the vast majority of what you’ll use. Let’s look at an example, piece by piece:
    * **Shoulder Charge Alpha (Vanguard Pilot):** [75%], R30. _Rush the target and collide face-first, attempting to knock them down._ Reduces target's CT by 5. (1E, 1 TP)
        * **Shoulder Charge Alpha:** Skill name. You can always use “!desc Skill Name” to look up skill info. (This specific skill doesn’t really exist, though.)
        * **(Vanguard Pilot):** Skillset name, representing the class it’s a part of. This one maps to Decider, so you can use either “!class Decider” or “!class Vanguard Pilot” to see the whole class’s info.
        * **[75%]:** Accuracy. Bracketed accuracy is fixed– it’s always exactly a 75% chance.
        * **R30:** Power. The letter here tells you which stats are used for this attack.
            * For offense, P is physical, R is ranged, and M is magic.
            * So, for an R attack, your accuracy is affected by your R-ACC and the target’s R-EVD, and the damage is affected by your R-ATK and their R-DEF.
            * H is healing. Healing always hits, and its power is based on the average of all your defense stats.
            * F is fixed damage, which isn’t affected by stats at all.
        * The italic text is **flavor text**.
        * The non-italic text is **rules text**, which details any special effects.
        * **1E:** Targeting code. E means that many enemies, A means that many allies, T means that many targets (either enemies or allies). A “!S” suffix means “not self”-- you can’t target yourself.
        * **1 TP:** This is the Turn Point cost of this skill. On each turn, you have 3 TP to use. Most skills are 1 TP or 0 TP.
* **[S] Support Skills** are green, and provide passive buffs or abilities.
    * **Mechanic S-Skills** are reverse-green (black text on a green background), and describe the core mechanic of your class.
    * If you read nothing else, read your Mechanic S-Skill!
* **[I] Interrupt Skills** are white/grey, and can be used at the **start** of any other unit’s turn.
* **[R] Reaction Skills** are yellow, and can be used in the middle of another action, when their condition is met. (Normally, you can only react once per action–so reacting to a spell being cast means you can’t _also _react to taking damage from the same spell. The Wrathguard class can break this rule.)
* **[LB] Limit Breaks** are white and red, and are extremely powerful special moves. Your Groove determines when you can use these, and how much TP they cost.


### Ticks and Turns {#ticks-and-turns}



* Every unit has a CT value, between 0 and 100.
    * With each tick that passes, your CT increases by 10.
    * When it hits 100, you get a turn.
* Every Hero turn starts with 3 TP (Turn Points). All actions are 1 TP unless explicitly specified.
* **_Any Action Skill can only be used once per turn._**
* When your HP is reduced to 0, you become Downed.
    * While Downed, heroes can still take turns– but your stats are reduced.
    * If your entire team is either Downed or unable to take any actions at the same time, your team loses!


## Section II: Classes {#section-ii-classes}


### Attack Classes {#attack-classes}


#### [Profaner (Dark Blast)](/system/skills#Profaner) {#profaner-dark-blast}

A simple all-offense class, Profaners channel a connection to the Profound Darkness to single-handedly wipe entire armies off the field with powerful antiphoton techniques. Anyone can use the Profaner effectively, if they’re willing to pay the price for their power. Based on the Phantasy Star Online 2 mechanic “Dark Blast.”

_Class Mechanics: Exhaust and Shadow Photons_



* Some effects give you the Exhaust status as a cost, or allow you to Exhaust yourself to add more bonuses. If you have the Exhaust status, you can’t use any other Exhaust effects until you remove Exhaust.
* The Antiphoton gauge charges based on damage and kills. Each time it charges to full, you gain a Shadow Photon, reset the gauge, and clear Exhaust.
* Shadow Photons power your most powerful skills. If you need one in a pinch, Hunger for Destruction will grant you one at a price…
* Black Hole can open up all sorts of exciting tactical situations, if used creatively!


#### [Bouncer (Jet Pursuit)](/system/skills#Bouncer) {#bouncer-jet-pursuit}

An elegant and stylish offense class, Bouncers use a rocket-polearm to launch wildly after enemies, striking down to propel themselves back up. They soar through the air with stored magic charge streaming behind them, striking stylish poses the whole time. Truly, these are the residents of the sky. Inspired by the traditional Kode class "Dragoon," and a few other things…

_Class Mechanics: Delay and Combo_



* Delay skills consume resources up front and resolve after a number of ticks, making it important to defend yourself while you wind up for a big strike. You can only have one Delay running at a time.
* Bouncer has the unique ability to use Delays defensively– Storm Chaser makes you harder to hit, and Wiredrive Escape lets you cancel a Delay to dodge a hit!
* Combo builds up with weak fast hits, and cashes out with large single hits. There are lots of ways to cash it out, so determine whether you need something right now or if you can afford to wait for the big hit!


#### [Scion (Successor Arts)](/system/skills#Scion) {#scion-successor-arts}

A versatile, agile offensive class that switches fluidly between physical and ranged attacks. Drawing out the Scion’s full potential requires carefully thinking through your combo tree, but a truly skilled one can be both devastating and untouchable. Based on the PSO2 Scion Classes "Hero" and "Luster."

_Class Mechanics: Exhaust and Voltage_



* Some effects give you the Exhaust status as a cost, or allow you to Exhaust yourself to add more bonuses. If you have the Exhaust status, you can’t use any other Exhaust effects until you remove Exhaust.
* Voltage is built up with hits, and consumed entirely when used. It’s up to you to decide whether to cash it out early or save it up to get the free status buff at the cap.


#### [Decider (Vanguard Pilot)](/system/skills#Decider) {#decider-vanguard-pilot}

A powerful and heavy offensive class, Deciders take to the field in a Vanguard, a three-meter-tall mech suit with a shoulder-mounted railgun originally built for military use. Experts at dealing damage and controlling the battlefield, these heavy machines can dance and weave through the front lines, blazing open a path for their forces. Based on the Xbox game “Steel Battalion.”

_Class Mechanics: Battery, Exhaust, Delay, and Clipazines_



* The Battery gauge charges up over time.
* Delay skills consume resources up front and resolve after a number of ticks, making it important to defend yourself while you wind up for a big strike. You can only have one Delay running at a time.
* Exhaust: Some effects give you the Exhaust status as a cost, or allow you to Exhaust yourself to add more bonuses. If you have the Exhaust status, you can’t use any other Exhaust effects until you remove Exhaust.
* Clipazines are used to reload with Magdump (primarily to clear Exhaust). If you need more, you can use Call Supply Drop, but you’ll need to think a few turns ahead.


### Support Classes {#support-classes}


#### [Arcanimist (Lost Arcanima)](/system/skills#Arcanimist) {#arcanimist-lost-arcanima}

A support class that provides buffs, healing, and shielding to their allies, Arcanimists are the last bearers of the art of controlling floating magitek pylons called distaves, thought lost to history during the Seventh Umbral Calamity. Based on what information exists of the unimplemented FFXIV 1.0 class "Arcanist."

_Class Mechanic: Distaves_



* Distaves are created undeployed (floating around you), and can be deployed (planted in the ground near an ally).
* Deploying a distaff to an ally applies a buff to that ally, and other skills can reuse that distaff to reapply that buff, apply new buffs, or heal.


#### [Wrathguard (Four Quadrants)](/system/skills#Wrathguard) {#wrathguard-four-quadrants}

A defensive class, the Wrathguard fights with massive greatsword and fist interchangeably, knocking aside their opponents’ blows. With their powerful reactions, they often fight almost as much outside their turn as they do on their own turn, defending by interrupting and intercepting enemy attacks. Based (loosely) on 14th century German longsword techniques.

_Class Mechanics: Exhaust, Breath, and Readied_



* While Exhausted, you take less damage, and your reaction Rising Strike turns into Pommel Strike. It may end up being to your advantage to not clear Exhaust!
* Breath increases when you take damage, and can be consumed to heal yourself or an ally with Deep Breath, or deal heavy damage with Zornhau.
* By using Prepare Reaction on your turn, you can react more during enemy turns. Use this to chain together multiple reactions into defensive combos!


#### [Arbiter (Calling Card)](/system/skills#Arbiter) {#arbiter-calling-card}

A versatile and highly-tactical support class, the Arbiter is the latest student in a long tradition of RCP technicians. They draw "calling cards" from the callscript, summoning allies from distant worlds and sending them leaping into the fray at just the right moment. A skilled Arbiter always has the perfect card up their sleeve. Based on standard arena classes like "RCP Tech" and "SeeD."

_Class Mechanic: Callcards_



* In-universe, throwing a callcard summons a copy of the character depicted for up to 30 seconds.
* Mechanically, callcards are single-use consumables.
* Character callcards have Selfless, Dangerous, and Tactical ratings, from 0 to 3. Selfless are good at defense and healing, Dangerous are good at damage, and Tactical are good at support and buffs.
* Characters with higher total rank are rarer, divided into several power classes: Normal (0-3), Strong (4-6), Extreme (7-8), and Perfect (9).
* You draw _at the end of your turn_. That means you can go wild throwing out cards during your turn– but carefully consider how many cards you burn on reactions! If you start your turn with no cards, you can slowly catch up with Redraw or Destiny Draw.


#### [Correspondent (Red Science)](/system/skills#Correspondent) {#correspondent-red-science}

An esoteric and strange support class, the Correspondent composes essays of flame in a searing language. Correspondents can twist and tweak skills of both allies and enemies as they're cast, but require careful planning and strategy to make the most of their odd skillset. Don’t think too many sigils at once, or your hair might start to smolder! Based on the Fallen London profession "Correspondent."

_Class Mechanic: Sigils_



* **Sketch** allows you to copy parts of skills (like accuracy or power numbers) as sigils. You can then use **Write** or **Inscribe** to temporarily overwrite the equivalent data on another skill.
* The target skill needs to have corresponding data to replace. For example, you can’t write power onto a skill without power.
* Be careful, for Correspondence sigils are dangerous and volatile things! If you hold too many in your mind at once, you'll start to burn. Either write them down with **Leaden Study** or use more!


## Section III: Limit Breaks and Grooves {#section-iii-limit-breaks-and-grooves}

Limit Breaks become accessible depending on which Groove you’ve selected.

Each of these Grooves is based on a different boss-battle system that came before this one!


### All-Rounder Grooves {#all-rounder-grooves}



* **H-Groove:** Classic combat style, and the default for new fighters. Gain an Adrenaline Gauge, which increases when dealing damage, taking damage, or healing. Consume 50% to boost an attack or 100% to use a Limit Break. (Rate: Medium) (Decay: Slow)
* **L-Groove:** Overwhelming combat style. Gain a Bloobel Gauge, which increases when hit, up to 300%. On your turn, consume 100% and 1 TP to use a Limit Break. Or, consume 200% or 300% all at once for a more powerful LB! (Rate: Medium) (Decay: Slow)
* **F-Groove:** Jackpot combat style. At the start of your turn, based on your HP and overall hero team state, randomly occasionally receive a Limit Turn: gain 2 TP and have the option to use a single Limit Break for 1 TP. (Rate: Random)
* **V-Groove:** Moonlit combat style. Gain a Drive Gauge (max 5). Gain 1 point after each turn not using a Limit Break. Consume 2 Drive and 1 TP to use a Limit Break at half power. (Rate: Fixed)


### Specialized Grooves {#specialized-grooves}



* **A-Groove:** Rushdown combat style. Gain a Rengeki Gauge, which increases when hitting enemies. When full, consume the entire meter to either reduce an attack’s TP cost to 0, or use 1 TP to use a Limit Break at half power. (Rate: Fast) (Decay: Medium)
* **R-Groove:** Tense combat style. Instead of Limit Breaks, gain a Pressure Gauge, which increases when dealing or taking damage, and gain access to Pressure Skills. (Rate: Slow) (Decay: None)
    * **Precise**: 50% Pressure. Attached skill gains 50% accuracy. (Meta)
    * **Powerful**: 50% Pressure. Attached skill gains 50% power. (Meta)
    * **Second Wind**: 100% Pressure. Recover 50% HP and recover from all status ailments.
    * **[R] Clutch Defense**: 100% Pressure. At any time, gain Clutch Defense status until the start of your next turn: all defensive stats raise sharply, and HP cannot drop below 1.
    * **Pressure Break**: 100% Pressure. Use a LB as a 1 TP action.
* **N-Groove:** Valorous combat style. Gain a Valor Meter (max 6). If you gain or spend class-specific resources during a turn, gain one Valor at the end of the turn. Valor can also be directly awarded by the ref for roleplay and creative shenanigans. Spend 6 Valor and 1 TP to use a Limit Break. (Rate: Fixed)
* **W-Groove:** Power-of-friendship combat style. Gain an Overdrive Gauge, which increases with damage and KOs to self and allies, up to 300%. Consume the entire gauge to use a single skill or Limit Break (for 1 TP) with power multiplied by the hundreds digit of the gauge value. Powering up a Limit Break beyond 100% breaks the gauge for the rest of the battle. (Rate: Medium) (Decay: Slow)
* **Z-Groove:** Crescendo combat style. Gain an SP Gauge, which increases when using support or healing moves. Consume 100% to use a Limit Break. (Rate: Fast) (Decay: Medium)

Your Groove will tell you how many TP a Limit Break costs for you. It’s usually 1 TP.

Some Grooves modify the power of a Limit Break.



* Scaling above 100%:
    * Raw power gets multiplied by the scale factor.
    * Multipliers get modified: for “1.5x” at 300%, take the increase over the base rate (0.5x) and multiply it (0.5 * 3 = 1.5), then add the base rate back in (1 + 1.5 = 2.5).
    * LBs that activate modes don’t change their effects, but give Power Up at 200% and Power Up II at 300%.
* Scaling below 100%: LB-generated modes, items, or other persistent effects only last until the end of the turn.


## Section IV: Commands {#section-iv-commands}


### General Commands {#general-commands}

!desc: Show a skill’s description. Use as “!desc Fight”.

!item: Show an item’s description. Use as “!item Shadow Photon”.

!class: Show a class’s description, skills, and stats. Use as “!class Profaner”.

!classes: Show the names of all classes that heroes can join as.


### In-Battle Commands {#in-battle-commands}

!stats, !status: Show an overview of all units (HP, statuses, etc). Specify a unit name to show detailed info about them.

!turnorder, !to: Show a preview of the next few turns.

!preset: Set requested actions for your next turn. (You can’t preset Reaction or Interrupt calls.)


## Appendix I: Statuses {#appendix-i-statuses}

Statuses have levels and duration. Some have duration in clock ticks; others last for a number of turns. Some are “innate,” denoted with a duration of *, and last until an effect removes them.

Higher levels of the same status overwrite lower levels. Lower levels slightly extend the duration of higher levels.

If you apply the same status to someone who already has it, it’ll increase the level of that status (if possible), making the status’s changes more powerful.


### Mechanic Statuses {#mechanic-statuses}



* Exhaust: Used a skill with an “Exhaust” cost. You can’t use other Exhaust skills until you clear Exhaust.
* Delay: Charging up a skill. That skill will go off when the Delay timer expires, before any turns that tick. You can only have one Delay at a time.


### Standard Statuses {#standard-statuses}



* Stat Up: Level 1 increases by X%. Level 2 increases by Y%. Level 3 increases by Z%. Every stat except Speed has one.
* Stat Down
* Power Up/Down: Modifies all offensive stats.
* Defend Up/Down: Modifies all defensive stats.
* Dodge Up/Down: Modifies all evasion/resist stats.
* Hit Up/Down: Modifies all accuracy stats, which also modifies crit chance.
* Haste: Keep more CT when ending your turn. (Roll twice, and take the better one.) Not leveled.
* Slow: Keep less CT when ending your turn. (Roll twice, and take the worse one.) Not leveled.
* Quick: Increases TP by 1, allowing you to take an additional action each turn.
* Burn: Take slow fixed damage over time.


### Original Statuses {#original-statuses}



* Assist: Unit has a callcard-summoned buddy. When you miss, your Assist partner leaps in to give you one more chance. Only consumed if it turns a miss into a hit.


### Guest Statuses {#guest-statuses}



* Barrier&lt;X> (Mega Man Battle Network): Unit is protected by a blue-green spherical shield. Absorbs X HP worth of damage. When a barrier loses its last HP, it’s destroyed, and it has a 50% chance to absorb any excess damage.
* Brace (Mega Man Battle Network): Unit remembered their undershirt. When you’d normally be Downed, remove this status and survive with 1 HP instead.
* Corrupted (Phantasy Star Online 2): Shadow photon energy weakens the target in a cloud of crimson mist. Reduces max HP by 30%.


### Special Statuses {#special-statuses}



* Down: HP depleted to zero. All stats reduced by 50%. If all Hero units are Downed, the fight immediately ends in a loss. To remove, use a skill that can remove Down.
* Limit Mode: Each class has a Limit Break that grants them a class-specific status. These last until the user is Downed.


## Appendix II: Definitions and Edge Cases {#appendix-ii-definitions-and-edge-cases}

If you need to consult this section, something has gone delightfully wrong. Good work.



* If the kode and the in-engine descriptions of a skill differ, the in-engine one takes precedence.
* An **attack** is a skill that has both a listed power and a damage type other than healing. An attack with zero power is still an attack. If an attack would have negative power, it has zero power.
* A status effect with a duration counted in turns always decrements at the _end _of your turn. A duration of **zero turns** lasts until the next time you start or end a turn.
* Certain damage types have special properties.
    * P10 is a 10-power physical attack, representing melee punches and slashes.
    * R10 is a 10-power ranged attack, representing guns and explosions.
    * M10 is a 10-power magical attack, representing magic and metaphysical damage.
    * H10 is 10-power healing. Healing always hits, and can’t crit.
    * F10 is a fixed 10-power attack. Fixed damage always deals exactly that value.
* Quirks of Downed:
    * When Downed, you lose all statuses, including Limit Statuses. Any Delay actions waiting to resolve are also cancelled.
    * While Downed, your stats are reduced by 25%, your base TP is reduced by 1, and your speed is slightly reduced. If your entire team is Downed at the same time (or otherwise unable to take actions), your team loses.
    * While Downed, you can’t be damaged or healed. An ally needs to use a move on you that specifically removes Downed. You also can’t remove Downed from someone while you’re also Downed.
    * Most enemies become KO’d instead: they stop gaining CT and can no longer take actions.
* Quirks of ticks:
    * Each tick, the duration of statuses ticks down by 1, and all CTs increase by the unit’s Speed.
    * When entering battle, your CT is set to a random value between 0 and 100.
    * All hero classes have Boosted CT, which slightly increases CT when completing a turn, and is guaranteed to be fair.
    * If multiple units cross 100 CT on the same tick, the highest CT moves first. (Turn Chains may or may not be implemented in a future update.)