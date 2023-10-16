# Release Notes

## Known Issues
* If Stop has a duration in ticks, the affected unit disappears from turn orders.

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
