# macrocraft — design

Status: concept. Nothing here is settled beyond the pillars; open questions are listed at the end.

## Premise

An RTS where unit behavior in combat is the core of the game, and where that behavior can be **fully automated and pre-customized** before the battle starts.

A lot of what RTS players call *micro* (fine-grained control of individual units in a fight) is really just carrying out known attack patterns by hand: retreat while the weapon reloads, turn and fire, keep retreating; swap targets to the low-health unit; pull a damaged unit back. Those patterns can be written down. macrocraft packages them so that units can reach their full potential without the player having to perform each pattern by hand every time.

## Pillars

1. **Preparation replaces execution.** If a player wants to prepare, nothing should *require* mechanical execution. Build orders, opening moves and unit micro can all be run from preset patterns or scripts.
2. **Reaction still matters.** Sooner or later you have to respond to what the opponent actually does. That takes some live control: choosing which pattern to run, retargeting, committing or pulling back. Preparation lowers the execution ceiling; it doesn't remove decision-making.
3. **Both styles are valid.** A player can micro by hand, program their units, or mix the two from one fight to the next. Neither should be strictly better.

## Behavior patterns

The central system. A **behavior** is a reusable program attached to a unit or group that decides moment to moment what the unit does.

### (a) Packaged patterns

Units come with (or can be given) built-in patterns that cover standard micro, so a unit can use its full ability without the player's hands. Examples:

- **Kite**: walk away, stop to shoot when the weapon's cooldown ends, then continue walking. (A *cooldown* is the delay before a weapon can fire again; *kiting* is attacking a slower enemy while keeping your distance.)
- **Stutter-step / flicker-shot while retreating**: the same move cycle tuned to fire on the exact frame the cooldown is ready, wasting as little movement time as possible.
- **Focus fire**: all units in a group target the same enemy, chosen by a rule (lowest health, highest threat, closest).
- **Retarget on condition**: switch targets when the current one dies, goes out of range, or a higher-priority target appears.
- **Pull back when hurt**: a damaged unit retreats behind the line and rejoins once it has recovered.

These go beyond the usual "move" and "attack" orders. They're compound orders with conditions in them.

### (b) Player-customized patterns

Players can author and edit their own patterns before battle: change target priorities, timings, ranges and conditions, or compose new patterns from smaller pieces. The authoring model (visual blocks, a rule list, a small scripting language, or some mix) is an open question.

### Campaign hook

Customizing patterns can be part of the campaign itself: each battle can be won by micro, by programming, or by both. Programming your units is a way to progress, not just a settings menu.

## Live control

During a battle the player can still:

- issue direct orders (which override or pause a unit's behavior),
- switch which behavior a unit or group is running,
- set or adjust behavior parameters on the fly (e.g. the target priority).

How direct orders and running behaviors interact (does an order interrupt the behavior, queue inside it, or replace it?) is a key design decision.

## Macro automation

The same idea applies outside fights: build orders and economy can be run from presets or scripts, so a prepared player can play the opening without executing it by hand.

## Open questions

- Authoring model for behaviors: visual node graph, ordered rule list, a restricted script language, or layered (rules for most players, script for power users).
- How behaviors are represented at runtime so they're deterministic. This matters for replays and fairness, and for lockstep multiplayer if we add it.
- What limits automation: does running complex behaviors cost anything (supply, a per-unit "doctrine" budget, research), or is it free?
- Single player only at first, or is versus multiplayer in scope early?
- Art direction and scale (unit counts per battle).
- Simulation tick rate, and whether game logic is decoupled from Godot's physics.
