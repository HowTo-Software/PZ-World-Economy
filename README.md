# PHUNMART ECONOMY OVERRIDES

A configurable Project Zomboid Build 42 economy built around PhunMart 2.

This setup creates functional buying, selling, scavenging, collecting, vehicle recovery, ammunition, medical, tool, pawn, and premium-vehicle economies. The configuration is designed for multiplayer servers and can be adjusted for anything from casual RP to a more deteriorated hardcore survival world.

The supplied JSON files are intended to be copied into:

`Zomboid/Lua`

## REQUIRED MODS

These overrides reference items and vehicles from the following mods. Missing content mods will normally cause the affected item or vehicle entries to fail to resolve.

https://steamcommunity.com/sharedfiles/filedetails/?id=3775133200

### Core Economy and Content

* **PhunMart 2** — Workshop ID `3689006725`
* **More Plushies** — Workshop ID `2795036124`
* **[B42.st] More Mre&Millitary foodV3** — Workshop ID `3488617262`
* **Gunz of Marz** — Workshop ID `3722134990`
* **[B42MP] Frockin Splendor! Vol.3** — Workshop ID `3431256608`
* **Forge Gold and Silver Ingots** — Workshop ID `3542603837`
* **[B42/B41] Mad Max 2 Pursuit Special** — Workshop ID `3017359186`

### KI5 Framework

* **that DAMN Library** — Workshop ID `3171167894`

This is required by KI5 vehicle mods.

### KI5 Vehicles

* **'91 RANGE ROVER Classic** — Workshop ID `2409333430`
* **'69 Dodge Charger** — Workshop ID `3631989559`
* **'87 Ford B700/F700 Trucks** — Workshop ID `3110911330`
* **'82 Oshkosh M911 + Military Semi-Trailers** — Workshop ID `2618213077`
* **'83 AM General M923** — Workshop ID `2811383142`
* **'93 Ford CF8000 Elgin Street Sweeper** — Workshop ID `2969343830`
* **'91 Geo Metro** — Workshop ID `3008795514`
* **'91 Nissan 240SX** — Workshop ID `3504401781`
* **'91 Ford Ranger** — Workshop ID `3539691958`
* **'90 Pierce Arrow Pumper and Ladder Trucks** — Workshop ID `2942793445`
* **'90 Ford F350 Ambulance** — Workshop ID `2952802178`
* **'86 Oshkosh P19A + Military Trailers** — Workshop ID `2566953935`
* **'86 Ford Econoline E-150 + Pop Culture Vans** — Workshop ID `2870394916`
* **'86 Chevrolet CUCVs + M101A2 Trailer** — Workshop ID `3428008364`
* **'85 Chevrolet Step-Van** — Workshop ID `3614034284`
* **'81 DeLorean DMC-12** — Workshop ID `3253385114`
* **'80 MAN KAT1** — Workshop ID `3248388837`
* **'79 Chevrolet Camaro** — Workshop ID `3703948448`
* **'78 Lamborghini Countach** — Workshop ID `3726526329`
* **'78 AM General M35 Series Trucks** — Workshop ID `2799152995`
* **'77 Pontiac Firebird** — Workshop ID `3346905070`
* **'76 Chevrolet K Series** — Workshop ID `3161951724`
* **'73 Nissan Skyline GT-R** — Workshop ID `3743371090`
* **'68 Pontiac Firebird** — Workshop ID `3258343790`
* **'67 Shelby GT500 + Eleanor** — Workshop ID `3026723485`
* **'67 Cadillac Gage Commando** — Workshop ID `2478247379`
* **'66 Pontiac LeMans / GTO** — Workshop ID `3447272250`
* **'65 Pontiac Banshee** — Workshop ID `3566868353`
* **'63 Volkswagen Type 2 Van** — Workshop ID `3041122351`
* **'63 Volkswagen 1300 Beetle** — Workshop ID `3005903549`

---

# IMPLEMENTED SHOPS

The current configuration modifies:

* Prawn Stars
* Pitty The Tool
* CSV Pharmacy
* Final Amendment
* Wrent-A-Wreck
* Collectors / Raven's Collection

`HardWear` is intentionally repurposed as the internal shop key for Raven's Wrecks.

Other PhunMart shops retain their normal definitions unless separately overridden by the supplied JSON files.

---

# PRAWN STARS

Prawn Stars is the cash/change and precious-value trade-in shop.

Configured payouts include:

* Money Bundle: **$50**
* Payday Money Pile: **$500**
* Gold Ingot: **1 bound token**
* Silver Ingots: **3 ingots for 1 bound token**
* Gem payouts 10-13 bucks
* Leather Harness Panties payout $1
* TRANSMUTED Vehicle Claim Key

The Gold and Silver Ingots are part of Build 42's precious-metal system. **Forge Gold and Silver Ingots** provides an additional crafting path for turning collected precious-metal material into ingots.

The cash economy is intentionally separate from the premium vehicle token economy.

---

# PITTY THE TOOL

The normal tool stock and pricing are retained.

`Base.Generator` is added as a dedicated sticky offer for:

**$100**

Generator variants are blacklisted from the normal randomized tool/electronics pools so they do not also appear elsewhere.

Custom group:

`generator_sticky`

Custom pool:

`pool_pittythetool_generator_sticky`

---

# RADIO HACKS

The following generator variants are excluded from its normal electronics inventory:

* `Base.Generator`
* `Base.Generator_Yellow`
* `Base.Generator_Blue`
* `Base.Generator_Old`

Existing battery-box and lightbulb-box exclusions remain intact.

---

# CSV PHARMACY

Uses:

`pool_csv_med_sticky`

Sticky medical inventory includes:
* Phun Cure!
* Suture Needle
* Forged Forceps
* Sterilized Bandage
* Tweezers
* Painkillers
* Antibiotics
* Medical Shears
* Configured combat/energy consumables

Current configured standard-medical prices range from **$2 to $4** per item.

Configured combat/energy consumables are **$1 each**.

The custom stock is isolated to CSV Pharmacy.

---

# FINAL AMENDMENT

Final Amendment now uses only:

`pool_finalamendment_marz_ammo`

The normal Final Amendment melee, firearm, explosive, and vanilla-ammunition pools are removed.

All configured Gunz of Marz ammunition boxes are supplied through:

`marz_ammo_all`

The ammunition pool is sticky, so every configured ammunition type remains available.

## Weight-Based Ammunition Pricing

Ammo is no longer assigned a blanket price.

Each ammunition box is priced from its actual item weight:

`Price in dollars = item weight × 10`

Internally, PhunMart stores currency in cents:

`Price amount = item weight × 1000`

Examples:

* 5.45×39 box, weight `0.126` → **$1.26**
* 5.56×45 / .223 box, weight `0.153` → **$1.53**
* 7.62×39 box, weight `0.216` → **$2.16**
* .308 box, weight `0.315` → **$3.15**
* 9×19 box, weight `0.405` → **$4.05**
* .45 ACP box, weight `0.653` → **$6.53**
* 12ga box, weight `0.698` → **$6.98**
* 40mm box, weight `1.440` → **$14.40**

This keeps the overall ammunition economy near the previous average while allowing the actual weight of each ammunition type to determine its price.

The per-item mappings are defined in `PhunMart_Items.json`.

The reusable price definitions are defined in `PhunMart_Prices.json`.

---

# WRENT-A-WRECK — RAVEN'S SPECIALTY VEHICLES

Wrent-A-Wreck is the premium vehicle dealership.

Custom group:

`vehicles_raven`

Custom pool:

`pool_wrent_raven_core`

Standard vehicle price:

**100 bound tokens**

Street Sweeper price:

**24 bound tokens**

Purchased vehicles are configured to spawn at 100% condition with 90–100% fuel.

## Dealership Vehicles

Current specialty entries include:

* `fhqPursuitSpecialII` — Pursuit Special
* `81deloreanDMC12BTTF` — DeLorean time machine
* `69chargerDemon` — Charger Demon
* `93fordElginSpec` — Special Street Sweeper
* `79camaroGhost` — Camaro Ghost
* `78lamboCountachLP400Scb` — Special Countach
* `73nissanGTR` — Skyline GT-R
* `63beetleHP` — High-performance Beetle
* `91range` — 1991 Range Rover Classic, 4-door

The premium dealership exists as an alternative to hunting down and repairing naturally spawned vehicles. This becomes increasingly valuable when the server world is configured with more deteriorated vehicle starting conditions.

---

## Vehicle Payout

Every eligible vehicle pays:

**2 bound tokens**

Vehicle value, rarity, condition, livery, occupation, or configuration does not alter the payout.

This is deliberately a **server-cleanup economy**, not a realistic used-car appraisal system.

## Economy Loop

1 recovered eligible vehicle:

**2 tokens**

50 recovered vehicles:

**100 tokens**

100 tokens:

**1 standard premium Wrent-A-Wreck vehicle**

A player earning a standard premium dealership vehicle entirely through Raven's Wrecks has therefore removed approximately **50 unwanted vehicles from the server world**.

## Exclusions

NONE. All vehicles should be transmutable and sellable. Please try to grab a console.txt and throw it at me somewhere either on steam or the github if something happens!

---

# RAVEN'S COLLECTION

The normal Collectors shop is overridden with a custom curated collector economy.

Shop key:

`Collectors`

Custom pool:

`pool_raven_collection`

Custom group:

`raven_collection`

The pool is sticky.

All configured Collector trade-ins currently pay:

**1 bound token per item**

This intentionally creates another path toward premium vehicles without tying collectibles to the cash economy.

## Collector Content

The collection includes:

* Vanilla plushies
* Vanilla toys
* Cap guns and novelty toys
* More Plushies items
* EyeOfCthulhu
* PotScrubberFrog
* StockCertificate
* Hominid skull fossils and fragments
* Preserved specimen jars
* Mineral, insect, and butterfly specimens
* Tarot cards
* Ouija board
* Crystals
* Gold and silver collectible coins
* Trophies
* Military medal
* Rat King
* Suspicious Package
* Pocketwatch
* Other configured curios and mementos

More Plushies contributes more than 80 additional collectible plushies to the shop.

The Collector shop is intended for strange, decorative, rare, museum-like, or otherwise non-essential items rather than general-purpose loot.

---

# CASH VS. TOKEN ECONOMY

The configuration intentionally separates routine survival spending from premium progression.

## Cash / Change

Cash is used for ordinary survival purchases such as:

* Ammunition
* Medical supplies
* Consumables
* Tools
* Other routine shop purchases

Gems and other pawnable valuables provide cash for normal day-to-day spending.

## Bound Tokens

Bound tokens are used for premium progression such as:

* Specialty vehicles
* Collector rewards
* Precious-metal trade-ins
* Vehicle recovery

This prevents high-value vehicle purchases from directly competing with everyday food, medical, and ammunition spending.

---

# STICKY POOLS

Sticky offers:

* Always appear
* Are not randomly rolled
* Have unlimited shop stock
* Ignore normal stock minimum/maximum values

`PhunMart.MaxStickyItems` controls only the oversized-pool compiler warning.

It does **not** limit the number of sticky offers.

Raven's Collection contains a large number of collectibles, a value of at least:

`250`

is recommended.

Increase it further if additional sticky inventory is added.

---

# INSTALLATION

1. Install and enable all content mods referenced by the configuration.
2. Back up the existing `Zomboid/Lua/PhunMart_*.json` files.
3. Copy the supplied override JSON files into `Zomboid/Lua`.
4. Confirm the required Workshop IDs and Mod IDs are present in the server INI.
5. Restart the server so PhunMart recompiles the definitions.
6. Force-restock modified machines through the PhunMart admin tools.
7. Confirm that referenced item and vehicle script names resolve during startup.
8. Test purchases and trade-ins before promoting configuration changes to a production server.

Existing machines may retain previously generated inventory until they are restocked.

For production use, testing changes on a certification/staging server before copying the final INI, Sandbox, and Lua changes to production is strongly recommended.

---

# CUSTOM CONFIGURATION FILES

The economy uses modifications to:

`PhunMart_Shops.json`

`PhunMart_Pools.json`

`PhunMart_Groups.json`

`PhunMart_Specials.json`

`PhunMart_Prices.json`

`PhunMart_Items.json`

Each file has a separate role:

* **Shops** selects the pools used by each vending-machine front.
* **Pools** controls pool behavior and group sources.
* **Groups** contains item and vehicle membership.
* **Specials** defines special payouts/actions.
* **Prices** contains reusable cash/token price definitions.
* **Items** applies item-specific price and reward overrides.

---

# IMPORTANT NOTES

`Collectors` is intentionally retained as the internal shop key for Raven's Collection.

Vehicle groups use bare vehicle script names unless another subsystem specifically requires a module prefix.

Item IDs use their actual module prefix, for example:

`Base.StockCertificate`

`MorePlushies.PigPlushie`

VEHICLES DO NOT!

PhunMart definition keys and Project Zomboid script IDs are case-sensitive.

A valid JSON file can still contain an invalid item or vehicle script ID. In that situation the JSON may load normally while only the unresolved entry fails.

Malformed JSON can prevent the relevant override file from loading.

If a content mod changes an internal item or vehicle script name, the corresponding JSON definition must also be updated.

Back up known-working configuration files before editing them.
