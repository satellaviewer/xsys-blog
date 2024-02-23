# Release Notes

## 1.0.4a

### Gameplay Changes
* Balance changes:
	* Arbiter: When drawing callcards, they now get added to the inventory with the format "[S1/D2/T3]" to make it clearer at a glance what each number means.
	* Arbiter: Call Supporter and Call Striker have had their Dangerous modes switched with their Tactical ones, because I keep resolving them that way anyway.
	* Arbiter: Added alternate firing mode for Gate-Crosser, allowing fusing cards two at a time without consuming them. This results in no mechanical change, it's just for fun.
	* Arbiter: Made Polymerization repeatable, because it's fun and I like writing fusions.
	* Arbiter: Clarified Force Reroll interaction with multi-hit attacks.
	* Profaner: Rephrased Convergent Ray effect and added a "add Delay 6" clause to it. This more accurately reflects the original and makes having to resolve the more complicated effect more rare and deliberate.
	* Profaner: Tyrant Strike now inflicts Defend Down II on a smash.
	* Profaner: Removed Delay from Pure White Darkness, and added "on hit, inflict Stop for 4 ticks and [old effect]". Given how much of Profaner relies on until-end-of-turn buffs, it doesn't feel right that its limit shouldn't get to benefit from those too.
	* Wrathguard: Removed clause "Use only while Exhausted" from Pommel Strike, because it's not really contributing anything.
	* Wrathguard: Removed Prepare Reaction. Removed Time of the Hand, and renamed the old Time of the Foot to Time of the Hand. The connecting idea of "be able to violate the rule about reacting multiple times to the same skill" hasn't been particularly interesting in practice.
	* Wrathguard: Added experimental new reaction, Rally the Rearguard.
	* F-Groove: Reduced Limit Turn award to +1 TP (down from +2 TP). This is purely so turns don't take too long-- and with most skills non-repeatable, an extra TP past the fourth isn't usually that good anyway.
* Added Haste and Slow: opposed three-rank statuses that increase or decrease speed by one point per rank.
	* There are no current sources of these. There might never be. But they're in the engine now.

### Misc
* Fixed a known issue where if Stop has a duration in ticks, the affected unit disappears from turn orders.
* Fixed a design oversight where some commands, like !stats, echoed their output locally, disrupting lines being typed.
* Fixed various minor formatting issues.
* Fixed a known issue where when extremely long clusters of lines happen, the affected message may be rejected by Discord for being too long.
* Added a test mitigation for a known issue where Javacord would periodically warn about a full message cache on the prod environment.
* Fixed an esoteric issue where Poison opposed (and could clear) Poison.
* Timers now only message every 60 seconds until the 30-second mark.

## 1.0.4

### Gameplay Changes
* Correspondent makes its triumphant return as a playable class!
	* Use "!sigil Bee and Rose" to view specific sigils, "!sigil Accuracy 4" to search for sigils by type, and "!sigil Fight" to see what sigils a skill breaks down into!
* Added !rhero/!rboss commands for selecting random heroes and bosses.
* Balance changes:
	* Sharker: Properly added Boosted CT, like all other player classes.
	* Scion: "Successor" limit status now only provides buffs to Scion Time and Scion Gear. Removing the Exhaust mechanic entirely isn't interesting, and Scion is a powerful enough class to not need particularly powerful limits.
	* Scion: Fomel Blast now consumes 1 Voltage per extra target. This prevents Voltage gain getting completely out of control on multiple enemies.
	* Decider: Forecast Shot System is now repeatable, but doesn't stack with itself. (Someone asked last fight, and it sounds reasonable enough.)
	* Decider: Chaingun now hits minimum five times (up from a fixed one hit to every enemy). This gives it an actual use in single-target fights, now that it no longer has CT damage.
	* Wrathguard: Pommel Strike now costs 10 Breath, but inflicts extra debuffs on crits and smashes. This gives a reason to not just call it for every single attack, and interacts with how Wrathguard tends to get crit fairly often under the new accuracy rules.
	* Wrathguard: Zornhau heavily reworked. Now 80% accuracy (down from 100%), and "While Delaying, no reactions" clause replaced with "On use, gain Defend Up for 4 ticks. Add another TP to make this target all enemies."
	* Wrathguard: Added new skill Alberhuten (a weak attack that gains a small amount of Breath).
	* Arcanimist: Gear Bloom is now a fixed 75 healing that does not take stats into account. (This is to fix a design issue where later skills can't easily resolve before earlier ones.)
	* Arcanimist: Added Pyroxene costs (which will only matter when shops eventually open).
	* Arbiter: Added "Can affect multiple targets on request" clause to Summon Assist.
	* Arbiter: Clarified that Force Reroll can react to reaction rolls, and increased minimum rolls by one.
	* F-Groove buffed even more (curve increases to max more quickly, removed two-roll RNG).
	* Mook CT influence increased to 6, 5, 4, 3, 2, 1 (up from 5, 5, 2, 2, 2, 1).

### Misc
* Fixed a critical bug where nonstandard IRC name colors (above 16) would cause Discord output containing that name to crash and not display.
* Fixed a bug where turn-order preview sort for multiple units on a single tick incorrectly added Boosted CT, forcing heroes before bosses on the same tick.
* Fixed small formatting issues with Barrier editing.
* Added more ref quality-of-life commands (/note, /noteclear, /hp, /maxhp).
* Several small internal bug fixes.

## 1.0.3a

### Gameplay Changes
* Decider: Replaced AS-MIS with Volcanic Howitzer. (To be blunt, AS-MIS is not interesting enough to be that complicated. Also, I get enough [Warmonger's Diplomacy](https://fabdb2.imgix.net/cards/printings/DTD230.png) as it is, thanks.)

### Development Changes
* Added internal support for arena changes.
* Added internal support for secondaries and auxes.

## 1.0.3

### New Features
* Added L-Groove and A-Groove!
* ANSI color support on Discord! Many thanks to Amara for letting me know this exists, and Herringway for pointing me at the 39/49 "color-reset" codes.
	* Discord only supports seven colors, so it's definitely not as pretty as IRC text.
	* For the moment, bold and italic aren't supported. This is because Discord actually only supports a subset of ANSI, and that means the only way to remove bold or italic is to reset formatting entirely-- and *that* means a substantially more complex parser that can reach back and get the last valid color-code, and I'm not willing to write that right now.
	* Discord's ANSI formatting parser is also fairly buggy, especially around underlines; sometimes an underline or color will just appear out of nowhere. I don't think there's anything I can do about this, but swapping to another server tab for a sec will usually fix it.
* Engine support for hazard sets and hazards!
	* There's no content in this yet, but soon...
* Engine support fØmÛ:ïÝé(±é-dÍà²8Ñzx9¦v {CÄP2V)#óO¤É0vYÔg[#öh£çwßOÍ{ÀnÐ ¨ï0ÔaãþÂ#[ö7kâñµ]oÜ!
	* &ÿ#YuõìæMõ¤È7}ÏàMÂ(õØéÛàFý÷2Ô`Wx­ôê¸µ1h §Hu8F`¼ôzpÌk?dØPb82Ð bî[8|®õä t}æ­»a nFØÈÔ7ÃÔî³¹¦xsWõI'aÇZC<>O³ 'óKÎêÓÂöß¢?n²å

### Major Changes
* Added "block" mechanic.
	* If you roll too high on an accuracy roll against a boss, instead of missing, bosses will *block* your attack. You'll inflict 50% damage, but get no bonus effects or meter gain.
		* For rules text that specifies "on hit," even though it inflicts damage, a block is not a hit.
	* Attacks against heroes are unaffected; bosses can still miss you.
* Adjusted accuracy formula.
	* Global accuracy multiplier now 90%, down from 98%. Blocks and misses will now be slightly more frequent, hopefully making Hit and Evade statuses more interesting.
	* Sharply boosted strength of statuses affecting ACC and EVD stats (Submerge, Hit Up, Evade Up, stat ups, etc); now roughly 10% modifier per level.

### Gameplay Changes
* H-Groove: Spending Adrenaline now reduces Adrenaline gain by 50% until the end of your turn.
	* Once you had a full limit charge, it was easy to spend it, deal a ton of damage, and regenerate almost your entire limit gauge in a single turn.
* Wrathguard: Changed Salute to Hit Up for 30 ticks (changed from Power Up for 5 ticks).
	* Now that accuracy is more important, this might be more interesting.
* Arbiter: Call Striker TP reduction chance now 15% per rank (down from 20%). This has been a liiiiittle too consistent with only base cards.
* Arcanimist: Starting Anima is now 7 (up from 3).
	* This is intended to evoke the "healer who runs out of mana" feeling that many MMOs have, encourage more intense and elaborate play of the class... and ease TP economy issues near the start of the fight, when you need to be doing lots of distaff crafting. It's also turned out pretty impractical to take an Anima-positive turn. Plus, it's lore-compliant with FFXIV 1.0!
* Arcanimist: All skills other than Arcane Needle are now repeatable.
	* This class was designed before the unique-skills rule anyway (as you might guess from the impossible "first time you cast this each turn" clause that still hung around on Arcane Needle). Hopefully, removing this restriction will make the class a little more smooth.
* Sharker: Major class rework.
	* Paint now decays every 1-3 ticks (down from a fixed 5 ticks).
	* Super Jump is now Slosher Skirmish. Rather than consuming Paint, base healing power is based on Paint value, with an extra target at 8.
	* A new skill named Super Jump is now available, which restores Ink.
	* Charger is now Anchor Charge. Rather than consuming Paint, it's a two-hit attack with variable delay.
	* Zimmis is now Zimmis Ambush: accuracy down (90% to 80%), hits up (3 to 5), now repeatable for 10 Ink.
	* Clash Blaster now targets 3 enemies (up from 2).
	* Splashdown cost is now 25 Ink (up from 20).
	* Cruisin' Cooler is now Cruzin' Cooler, for accuracy. No mechanical change.
* Sharker: Adding multiple ranks of Paint at once now applies all, rather than just the max of both sides plus one (3+4=7, rather than 3+4=5).
	* This was leftover code from pre-production, when buffs could be up to rank 10, instead of rank 3. (It made sense back then.)

### Misc
* Fixed a critical bug where Sharker's Submerge set all EVD stats to single-digits.
* Added a safety check for skills with power but no accuracy, to prevent the "roll against zero" situation.
* Templating: Magdump and a few other skills now specifically use the keyword "repeatable."
* Templating: Narrowed Gear Bloom's activation from "at any time" to "when an action is declared or finishes resolving," to prevent potential rules issues.
* Fixed a bug where Paint stack count wasn't visible in !status.
* !status format expanded to multiple lines because its existing form is just unreadable.


## 1.0.2a

### Gameplay Changes
* Revised Arcanimist.
	* Split Deploy Distaff into Deploy Distaff and Imbue Distaff.
		* Deploy Distaff only applies the Distaff status. It's also gained "1 Anima: Make this 0 TP."
		* Imbue Distaff only applies the boost statuses.
		* This fixes a *lot* of design problems and clarity issues around how distaff-applied statuses work.
		* I'll be watching the TP economy of this class to see if it can still accomplish what it needs to.
	* Animate Distaff now consumes the distaff, and is now only the healing firing mode.
		* Imbue Distaff covers the rest of the old version's firing modes, so the class's tactical options stay the same.
	* Recall Distaff now explicitly specifies that it resets upgrades.
	* Spindle Winding power slightly reduced (Barrier<30> down from Barrier<50>).
	* Upgrade Distaff wording clarified.
	* Arcane Needle now defaults to the higher power, for ease of resolution.
	* Arcanimist skill text now does not specify that a distaff must be yours.
* New command: !distaves (!distaff, !distaffs) lists all distaves in play and their rank.
* Added Pyroxene cost values to all skills for classes except Arcanimist and Correspondent (both classes not quite finalized yet).
	* Purchasing isn't implemented yet.

## 1.0.2

### Gameplay Changes
* New Features:
	* **Supporters**. More information will become available soon.
	* New Kode class: **Sharker**.
* Statuses:
	* **Profaner**: Corrupted is now a ranked status (10% HP reduction per rank, up to 5).
		* Regen now counteracts Corrupted, Poison, and Burn, and vice versa. Regen, Poison and Burn statuses are not normally ranked.
	* **Profaner**: Corrupted starting duration is now 10 ticks (down from 30).
	* **Profaner**: White-Gold Rose is now a status that boosts PACC and MATK by 10 (changed from fixed +10% physical accuracy and +10 magical power).
		* This change should be more or less the same, and require substantially fewer command entries from the ref.
	* **Wrathguard**: Added the "Cover" status, which redirects all damage to a specific ally, and reduces it by a small amount (currently 3%).
	* Barrier's chance of absorbing all extra damage on break is now 30%, down from 50%.
	* Fixed Note status clearing at end of turn.
* Balance changes:
	* **Arbiter**: Call Spirit now can target Polymerized cards.
	* **Arbiter**: Cross-Summon and Polymerize now allow using one card from your hand and a randomly-drawn one.
	* **Arbiter**: Summon Supporter CT damage decreased (5/rank with cap of 30; down from 10/rank up to 3 then 5/rank past that, and uncapped).
	* **Arbiter**: Clarified that Summon Assist and Summon Defender are the summon's choice, not the caster's.
	* **Profaner**: Red Queen Arrival is now a fixed-damage effect (changed from "same damage type as your first attack"), to reduce manual resolution work.
	* **Profaner**: Paying a cost with Hunger for Destruction now inflicts a stack of Corrupted (previously Defend Down).
	* **Profaner**: Reworked clearing Exhaust.
		* Now: "Black-Gold Thorn" kode skill added, consuming two Shadow Photons to clear Exhaust.
		* Previously: Shadow Photon item consumed to clear Exhaust, but inflict Corrupted.
		* Combined with the changes to Hunger for Destruction, this is mostly the same, with more tactical options. (Also, all class-critical rules text is now in the kode, not obscured in the item description.)
	* **Wrathguard**: Removed alternate firing mode on Zornhau.
		* Now: "Delay 4. While Delaying with this, you can't use Reactions."
		* Previously: "Exhaust, or consume Breath and add Breath/4 power"
		* Choosing between these firing modes was not particularly interesting, and really, it's not that appealing to expend these kinds of resources on offense anyway. This has only one firing mode, so it's faster to resolve, and should help bring out the "commit to the attack" mega-greatsword theming a little better.
	* **Wrathguard**: Salute now gives Power Up (from Hit Up), because nobody used it.
	* **Wrathguard**: Deep Breath now has base power Breath/3 (down from Breath/2).
		* The new DEF-based healing-power scaling was causing this move to wind up way more powerful than intended-- which is a big problem when it essentially acts as a rebate on damage taken!
	* **Wrathguard**: Completely revised Guard Chase.
		* Now: When an enemy attacks, choose a target who's been hit, and grant them the Cover status. Until the end of the turn, you take all damage for that unit, slightly reduced.
		* Previously: [50%]. When an enemy attacks, choose a target who's been hit. On success, the hit is cancelled; on failure, you take the damage instead.
		* Even a 50% chance to nullify one hit on each attack turned out to be much more of a balance problem than I expected-- I figured bosses swinging three-target two-hit attacks would make that not particularly threatening. This new version doesn't reduce damage; it just moves it around. That also means Rising Strike's identity as the big "defensive cancel" move becomes more separate and clear, and be another source of that "commit to your decisions" mega-greatsword theming.
	* F-Groove now collects four times more Aura on each failed roll, charging substantially faster.

### Development Changes
* New abstract Gimmick class: "AbstractRankedStatusGimmick," which has the ability to rank up or down.
	* This more clearly separates the hierarchy:
		* Gimmick
		* AbstractStatusGimmick (containing a duration)
		* AbstractRankedStatusGimmick (containing a duration and a rank)
		* AbstractStatModStatusGimmick (containing a duration, rank, and list of affected stats)
		* PowerUp (a specific implementation of AbstractStatModStatusGimmick)
	* The upshot of all of this: if you work with XSYS code, it's easier to make ranked statuses now.

### Misc
* Fixed a bug where healing or being healed in certain contexts would expend H-Groove adrenaline.
* Refined and improved logic around finding partial skill names.
* All player input/output on script commands now always transfers across, per player feedback.
* Tequila Sunset's description now no longer clips onto a second line on IRC.

## 1.0.1c
A couple new features designed to make the ref interface a little bit smoother.

### Gameplay Changes
* Speed is now visible in class data.
	* I didn't actually realize this wasn't already the case until someone mentioned it.
* The resolve queue now caches both power and damage type, which fixes a design flaw where Reactions that interject a single hit (like Gear Bloom) might overwrite the triggering attack's power or damage type, if not very carefully resolved.
	* Thanks to Lana for asking questions which made me realize this could happen!

### Ref Changes
* Added /meter [player] [modifier], as a shorthand for /gedit [player] [gimmick name] [modifier].
	* If the player only has one gimmick that's a subtype of AbstractMeterGimmick, it'll pass its arguments to that gimmick.
	* ...Which means, if you only have your class's meter, this is easy shorthand to edit your meter value.
* Added advanced meter parsing.
	* Rather than only being able to set a new value, you can now use syntax like +30 to add, -30 to subtract, or =30 to set a fixed value.

## 1.0.1b
The second half of all the changes that shook out of the test battle-- these took a little more work and thought to put together.

### Gameplay Changes
* Temporarily disabled Correspondent due to design issues identified in the channel.
* Smash rate changed to 5% (up from 1%).
* Single-stat statuses now correctly do not merge with multi-stat statuses (like P-ATK Up with Power Up). These bonuses stack multiplicatively.
* Balance changes:
	* **Arbiter**: Added more callcards, and added a kode page to view them (see top navigation).
	* **Arbiter**: Cross-Summon is now repeatable.
	* **Wrathguard**: Salute's duration is now five ticks (up from two).
	* **Profaner**: Infinity Rush buffed: accuracy 95% (up from 80%) and added the property "if you Down your target, you can choose another target".
	* **Bouncer**: Fixed a design oversight preventing Rebound from activating when dodging attacks.

### Ref Changes
* Improved backend handling of multiple identical items: stacks of items can now be autocompleted.
* Added /dt to manually select a damage type.
* Fixed several issues related to multi-word class names.

### Misc
* Multiple items now show as a stack.
* Statuses now properly show their durations in "!status Player".
* Boss hidden HP now properly rounds to showing "1%" when between 1 and 5%.
* Fixed an issue with basic accuracy showing up on non-attack skills.

## 1.0.1
The first half of changes that shook out of the first test battle! Big thanks to everyone who played and gave feedback, particularly about the accuracy and damage calculations.

### Gameplay Changes
* Completely revised the accuracy and damage calculations. Big thanks to Amara for a lot of help on both the design and implementation!
	* Accuracy has been changed from additive (a smash is 99 lower than a hit) to multiplicative (a smash is lower than 1/100 of a hit). This makes smashes and crits less guaranteed, especially during Overtime.
	* Similarly, attack and defense are now multiplicative: multiply by attack and divide by defense.
	* Stats now have a lower cap at 1, to prevent divide-by-zero or negative-healing shenanigans.
	* This also completely changes the math on stat buffs: rather than being +/-5 raw points per rank, they are now +/-3.5% of your class's base stat per rank. These stack multiplicatively with each other.
	* This implicitly fixes the "fist aid" bug, where attacking with a low attack stat against a high defense stat could actually flip the power negative and *heal* the target.
	* Damage is now rolled on resolve, rather than on accuracy roll, which fixes several design issues with having multiple units' entries in the resolve queue.
* Fixed a critical bug where the ref couldn't modify Wrathguard's Breath gauge, and thus couldn't deduct Breath for skills which require spending it.
* Fixed an issue with Arcane Needle where it had no default accuracy.
* Balance changes:
	* Added basic action "Dab" to consume TP if necessary.
	* Updated Boosted CT gimmick: technically, it's not actually possible to roll 20 CT, so it now reads "between 1 and 19." No mechanical change.
	* Explicitly clarified that "once per turn cycle" mechanics reset at the start of your turn.
	* **Decider:** Chaingun now no longer inflicts CT damage (down from "CT damage equal to damage").
	* **Wrathguard:** Because damage is now rolled on resolve, Pommel Strike now also applies its Power Down to the triggering attack.
	* **Arbiter:** Cross-Summon is now an attack, because Arbiter didn't actually have one.
	* **Arbiter:** Call Spirit's wait is now 4x the total rank (up from 2x).
	* **Arbiter:** Explicitly excluded Polymerized cards from Call Spirit.
	* **Arbiter:** Generally nerfed the drop table for Calling Cards, making high-value cards less likely.
	
### Ref Changes
* Added /resetqueue (to clear the queue), /queuetarget (to change the target of an existing hit), and /queueadd (to add a hit without a roll)
* Added /targetasuser (/tu) to temporarily assume a new skill-user without having to /turn.

### Misc
* Added support for image attachments in Discord; they now post as image-links on other connections.
* Fixed inconsistent naming: "Dodge Up/Down" was also called "Evade Up/Down" in some places. Since "Dodge Up/Down" and the already-existing "Defend Up/Down" look similar at a glance, unified this as "Evade Up/Down" for clarity.
* Fixed many small formatting issues (CT not having style, counteract messages not having style, italic tags from IRC not getting stripped or parsed, error messages for certain internal commands being public, etc).

## 1.0-RC3
* Added formal definition for a skill being "canceled," as seen in one of Wrathguard's reactions.
* After testing, nerfed the *hell* out of stat-mod statuses, both in raw power (0.5 shifts / 5 points per level, down from 3 shifts / 30 points per level) and calculation (now additive rather than ratio based on defense). ...Look, this let someone in an optimal situation deal *ten times base damage*. It was clearly gonna be a problem.

## 1.0-RC2 (June 28, 2023)
* The basic skill *Wait* is now always 50 CT, to patch a potential rules issue involving repeated turn-start events.
* The basic skill *Brace* has been added.
* The Profaner now gains 90 Antiphoton on kill, down from 250 (a full gauge).

## 1.0-RC1 (June 17, 2023)
Patch 1.0-RC1, "A Ref Reborn," is now live! This patch introduces the eight starting classes: the attack classes Profaner, Bouncer, Scion, and Decider, and the support classes Arcanimist, Wrathguard, Arbiter, and Correspondent.

This patch is just focused on core battling. Things not in this patch include: spending currency, secondaries/auxiliaries, item inventories, hazards, surges. (There's a !slots machine, though.)
