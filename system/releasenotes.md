# Release Notes

## 1.0.1

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
	* Decider: Chaingun now no longer inflicts CT damage (down from "CT damage equal to damage").
	* Wrathguard: Because damage is now rolled on resolve, Pommel Strike now also applies its Power Down to the triggering attack.
	* Arbiter: Cross-Summon is now an attack, because Arbiter didn't actually have one.
	* Arbiter: Call Spirit's wait is now 4x the total rank (up from 2x).
	* Arbiter: Explicitly excluded Polymerized cards from Call Spirit.
	* Arbiter: Generally nerfed the drop table for Calling Cards, making high-value cards less likely.
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
