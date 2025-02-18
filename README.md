# DFreds Pocket Change

[![Become a patron](https://github.com/codebard/patron-button-and-widgets-by-codebard/blob/master/images/become_a_patron_button.png?raw=true)](https://www.patreon.com/dfreds) 
<a href="https://www.buymeacoffee.com/dfreds" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

![Foundry Version](https://img.shields.io/badge/Foundry-v10-informational)
![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https://forge-vtt.com/api/bazaar/package/dfreds-pocket-change&colorB=4aa94a)
![Latest Release Download Count](https://img.shields.io/github/downloads/dfreds/dfreds-pocket-change/latest/dfreds-pocket-change.zip)
![All Downloads](https://img.shields.io/github/downloads/dfreds/dfreds-pocket-change/total)

__DFreds Pocket Change__ is a FoundryVTT module which automatically adds currency to actors based on the DMG Individual Treasure Tables by Challenge Rating.

## CURRENTLY DOES NOT WORK FOR v11

## Let Me Sell You This

Have you ever watched as the peaceful NPCs of the town you've lovingly crafted get slaughtered by your players, only for them to ask how much money was in their pockets so they could loot them afterwards? Well, now you can automate that part. The money part. Not the slaughter. That would be weird.

Oh yeah. This module is useless without [Loot Sheet NPC 5e](https://foundryvtt.com/packages/lootsheetnpc5e/) by ChalkOne. So get that bad boy.

## What This Module Does

On the drop of a token onto a scene, Pocket Change generates currency for the token based on its challenge rating.

Pocket Change also adds a currency row onto the NPC sheet. From there, you can do the following:

- Convert All Currency: Changes all coins to the highest possible denomination (like in the PC sheet)
- Generate Currency: This replaces all their currency with new values. These values will be kept for all linked tokens and potentially overridden for non-linked tokens (see When it Automatically Generates Currency).
- Convert to Lootable - This changes the actor sheet to a LootSheet5eNPC, deletes all the Feat and Spell items, applies damage to the rest of the items based on your settings, sets token privileges to Observer for players, and add a treasure overlay icon to the bodies. This allows players to steal that sweet cash and loot straight from the dead dude. Note that this only works on NPC actor sheets for tokens on the canvas.

See here:

![Currency row](docs/currency-row.png)

You can configure some stuff:

![Module Configuration](docs/settings.png)

### Friggin' Cool Macros

This module also includes sweet macros. Basically, we got three of these bangers that work for selected tokens:

1. __Generate Currency for Selected Tokens__ - Useful for when you want to disable the automatic generation and do it all on demand (you overachiever you). This can't generate currency for player owned tokens, non-npc actors, and actors that are already loot sheets.
1. __Convert Selected Tokens to Loot__ - This macro takes each token and changes their actor sheet to LootSheetNPC, deletes all their Feat items, applies damage to items based on your settings, sets token privileges to Observer for players, and adds a treasure overlay icon to the bodies. This allows players to steal that sweet cash and loot straight from the dead dude. This can't generate currency for player owned tokens, non-npc actors, and actors that are already loot sheets.
1. __Convert Selected Tokens to Loot - Custom Damaged Items__ - This macro does the same as the other convert to loot macro, but this one lets you customize the chance of damaged items right in the macro. Rad.
1. __Convert Selected Tokens from Loot__ - This macro takes each token and converts them back to the default actor sheet. Note that this does not add any previously deleted spells and features back to the actor.

## When it Automatically Generates Currency

It only generates currency if all of the following are true:

- The module is enabled (configurable).
  
  > Sort of the whole point of this thing but hey, now you can temporarily turn it off.

- It passes the configurable percent threshold. This allows currency to be generated for only a certain percentage of actors.

  > Not every random acolyte should have money you know!

- The actor is not a loot sheet provided by Loot Sheet NPC 5e. This avoids any conflicts for loot sheet actors that have manually entered currency.

  >  I wouldn't want to mess up your perfectly balanced loot chests!

- The actor is not a linked actor. This avoids situations with modifying important NPCs data.

  > Now the big bad evil guy won't be randomly receiving cash! I bet he would be less evil if he did, though.

- The actor is an NPC. This avoids messing with any data related to player characters.

  > I'm sure you have cooler ways to mess with player characters anyway.

- The actor has a type that matches the configuration provided in the settings.

  > It would be a bit weird if that wolf your players slew had some coins shoved up its nether regions. But hey, maybe that sounds fun, too. Go nuts!

- The actor does not have a player owner. This avoids situations where we're generating currency for NPCs that players can actively control and drag onto the scenes.

  > We wouldn't that silly sidekick the party controls that you forgot to turn into a linked character for some reason to start having his pockets generate money.

- The user is a GM. The final catch-all to make sure only GMs are generating currency.

  > Take that you pesky players!

## What This Module Doesn't Do

Stops your players from being murder hobos. Also, it doesn't actually provide anyway for you to actually let the players steal that lovable NPC's life savings. That's what [Loot Sheet NPC 5e](https://foundryvtt.com/packages/lootsheetnpc5e/) does for you in conjunction with my included macros.

## My Philosophy

I've noticed over the months that a lot of FoundryVTT modules lack focus and good coding practice. A user should never be in a situation where they forget what any given module does. Additionally, a power user should never be totally lost on what's going on in a module if they dive into it.

In case anyone out there in the void is curious, this is my philosophy when it comes to implementing modules.

- Code should be easy to read, self-documenting, and contain JSDocs for any public functions
- Modules should do one thing, and one thing only. No "Quality of Life" catchalls from me. NO SIREE BOB.
- That thing the module does should do it well, with a minimum amount of initial configuration. It should "[Just Work](https://upload.wikimedia.org/wikipedia/commons/b/bf/ToddHoward2010sm_%28cropped%29.jpg)".
- Additional configuration should only be added if it really makes sense. If the configuration starts to change the thing the module does well, it shouldn't be there.
- Readmes (like this) should be funny AND informative. Please create a pull request if you think it could be funnier or informativer.
