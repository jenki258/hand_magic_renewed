# Hand Magic: Renewed - Datapack Guide

> This guide shows how to create datapacks that add spells, lost pages, rituals and other modular content for the **Hand Magic: Renewed**.

---

# 1. Quick start

1. Create a datapack folder (name it e.g. `my-magic-datapack`).
2. Inside, follow Minecraft datapack structure:

   ```
   my-magic-datapack/
   ├─ pack.mcmeta
   └─ data/
      └─ hand_magic_renewed/
         ├─ lost_page_hand_magic/
         ├─ mana_filling_recipes_hand_magic/
         ├─ preparations_hand_magic/
         ├─ rituals_hand_magic/
         └─ spells_hand_magic/
   ```
3. Add JSON files described below into the relevant directories.
4. Zip or place `my-magic-datapack` in `.minecraft/saves/<world>/datapacks/` or `server/datapacks/`.
5. Reload the world and test.

---

# 2. Datapack folder structure (recommended)

```
data/hand_magic_renewed/
  lost_page_hand_magic/
    <lost-page-id>.json
  mana_filling_recipes_hand_magic/
    <recipe-id>.json
  preparations_hand_magic/
    <preparation-id>.json
  rituals_hand_magic/
    <ritual-id>.json
  spells_hand_magic/
    <spell-id>.json
pack.mcmeta
```

**Namespace:** use `hand_magic_renewed` or really anything so your datapack is compatible.

---

# 3. Adding a spell (example)

Create `data/hand_magic_renewed/spells_hand_magic/fire_ball.json`.

```json
{
 "Name": "Fireball",
 "Description": "Summons fireball",
 "Spell Scroll Page": 19,
 "Research Symbol": "7",
 "Research Slot 1": "Ignis",
 "Research Slot 2": "Missio",
 "Research Slot 3": "Invocare",
 "First Gesture": 0,
 "Second Gesture": 2,
 "Third Gesture": 2,
 "Previous Spell Requirement 1": "",
 "Previous Spell Requirement 2": "",
 "Previous Spell Requirement 3": "",
 "Add to Previous Spells After Usage": false,
 "Spell Element": 2,
 "Cooldown": 200,
 "Mana Usage": 250,
 "Mastery Enabled": false,
 "No mastery 1": 0,
 "No mastery Text 1": "",
 "Starter 1": 0,
 "Starter Text 1": "",
 "Adept 1": 0, 
 "Adept Text 1": "",
 "Master 1": 0,
 "Master Text 1": "",
 "No mastery 2": 0,
 "No mastery Text 2": "",
 "Starter 2": 0,
 "Starter Text 2": "",
 "Adept 2": 0,
 "Adept Text 2": "",
 "Master 2": 0,
 "Master Text 2": "",
 "No mastery 3": 0,
 "No mastery Text 3": "",
 "Starter 3": 0,
 "Starter Text 3": "",
 "Adept 3": 0,
 "Adept Text 3": "",
 "Master 3": 0,
 "Master Text 3": "",
 "No wand 1": 0,
 "No wand Text 1": "",
 "Adept Wand 1": 1,
 "Adept Wand Text 1": "",
 "Master Wand 1": 2,
 "Master Wand Text 1": "",
 "No wand 2": 0,
 "No wand Text 2": "",
 "Adept Wand 2": 0,
 "Adept Wand Text 2": "",
 "Master Wand 2": 0,
 "Master Wand Text 2": "",
 "No wand 3": 0,
 "No wand Text 3": "",
 "Adept Wand 3": 0,
 "Adept Wand Text 3": "",
 "Master Wand 3": 0,
 "Master Wand Text 3": "",
 "Element Bonus 1": 1,
 "Element Bonus Text 1": "",
 "Element Bonus 2": 0,
 "Element Bonus Text 2": "",
 "Element Bonus 3": 0,
 "Element Bonus Text 3": "",
 "Extra Number 1": 1,
 "Extra Number 2": 0,
 "Extra Number 3": 0,
 "Command": "execute as %executor% at @s anchored eyes run summon minecraft:fireball ^ ^ ^3 {Motion:[0d,0d,0d],ExplosionPower:%extra_number_1+element_bonus_1+wand_usage_1%}"
}
```

**Notes:**

| Field               | Description                  |
| ------------------- | ---------------------------- |
| `Name`              | Display name of the spell    |
| `Description`       | Short description            |
| `Spell Scroll Page` | Page number in the spell scroll(If it's hidden spell then set it to -1) |
| `Research Symbol` | Symbol that will be used in mod to determine if it's researched or not(If it's going to be empty it's going to be always researched and it needs to be different from other symbols, as if they are the same then it's going to unlock other spells with same symbol) |
| `Research Slot 1, 2, 3` | What preparation spells needed to research it with research spell |
| `First, Second, Third Gesture` | Gesture symbol id that's needed to cast this spell(from 1 to 9) |
| `Previous Spell Requirement 1, 2, 3` | Previous spells/preparations needed to cast this spell |
| `Add to Previous Spells After Usage`       | If true will add this spell to preparations and if false it will just clear preparations after this spell is executed |
| `Spell Element`       | Spell Element id(from 1 to 9) |
| `Cooldown`       | How long will be cooldown after this spell executed |
| `Mana Usage`       | How much mana will this spell drain |
| `Mastery Enabled`       | Will spell gain mastery xp when used |
| `No mastery 1, 2, 3`       | Number used in placeholder when mastery xp is lower than 10 |
| `Starter 1, 2, 3`       | Number used in placeholder when mastery xp is higher than 10 |
| `Adept 1, 2, 3`       | Number used in placeholder when mastery xp is higher than 25 |
| `Master 1, 2, 3`       | Number used in placeholder when mastery xp is higher than 50 |
| `No mastery Text 1, 2, 3`       | Text used in placeholder when mastery xp is lower than 10 |
| `Starter Text 1, 2, 3`       | Text used in placeholder when mastery xp is higher than 10 |
| `Adept Text 1, 2, 3`       | Text used in placeholder when mastery xp is higher than 25 |
| `Master Text 1, 2, 3`       | Text used in placeholder when mastery xp is higher than 50 |
| `No wand 1, 2, 3`       | Number used in placeholder when caster is not holding any wand |
| `Adept wand 1, 2, 3`       | Number used in placeholder when caster is holding adept wand |
| `Master wand 1, 2, 3`       | Number used in placeholder when caster is holding master wand |
| `No wand Text 1, 2, 3`       | Text used in placeholder when caster is not holding any wand |
| `Adept wand Text 1, 2, 3`       | Text used in placeholder when caster is holding adept wand |
| `Master wand Text 1, 2, 3`       | Text used in placeholder when caster is holding master wand |
| `Element Bonus 1, 2, 3`       | Number used in placeholder when caster is holding wand with same element as spell element|
| `Element Bonus Text 1, 2, 3`       | Text used in placeholder when caster is holding wand with same element as spell element|
| `Extra Number 1, 2, 3`       | Just a number that's used in placeholder |
| `Command`       | Normal place for minecraft command but it can change special placeholders into this file or game info|

---

# 4. Adding a lost page

Create `data/hand_magic_renewed/lost_page_hand_magic/missio.json`:

```json
{
 "Spell info": "§3Preparation Spell | Missio: 0 - 0 - 2",
 "Page Number": 1
}
```

Fields: `Spell info` (Just info about something it can be anything), `Page Number` (Id of page (it can't be same with any other page!)).

---

# 5. Adding a ritual

Create `data/hand_magic_renewed/rituals_hand_magic/amethyst_apple.json`:

```json
{
 "result_item": "hand_magic_renewed:amethyst_apple",
 "result_command": "",
 "main_hand_item": "hand_magic_renewed:mana_amethyst_cluster",
 "offhand_item": "minecraft:apple",
 "Left Block": "minecraft:amethyst_block",
 "Right Block": "minecraft:amethyst_block",
 "Back Block": "minecraft:amethyst_block",
 "Straight Block": "minecraft:amethyst_block",
 "Left-Straight Block": "minecraft:bone_block",
 "Right-Straight Block": "minecraft:diamond_ore",
 "Left-Back Block": "minecraft:diamond_ore",
 "Right-Back Block": "minecraft:bone_block",
 "main_hand_item_particles": "hand_magic_renewed:light_blue_glitter",
 "offhand_item_particles": "hand_magic_renewed:redglitter",
 "result_item_particles": "hand_magic_renewed:purpleglitter",
 "result_particle_boom": "hand_magic_renewed:light_blue_glitter ~ ~ ~ 0.2 0.2 0.2 0.5 100 normal",
 "starting_sound": "hand_magic_renewed:ritual_start",
 "ending_sound": "hand_magic_renewed:ritual_end",
 "item_spawn_distance": 2.5,
 "item_distance_decrease_speed": 0.01,
 "result_item_spin_time": 60,
 "Ritual Name": "Fruit???...",
 "Ritual Locked" : true,
 "Ritual Research Symbol": "*",
 "Scroll Page Number": 30,
 "Can be found in Ritual Scroll Piece": true,
 "Ritual Info": "Allow you to make special fruit..."
}
```

**Notes:**
| Field               | Description                  |
| ------------------- | ---------------------------- |
| `result_item`              | Item that's going to be given to ritual executor after performing this ritual    |
| `result_command`       | Command that's going to be executed after performing this ritual            |
| `main_hand_item`       | Item in main hand that needed for performing this ritual           |
| `offhand_item`       | Item in off hand that needed for performing this ritual            |
| `Left, Right, Back, Straight, Left-Straight, Right-Straight, Left-Back, Right-Back Block`       | Blocks that needed for performing this ritual            |
| `main_hand,offhand,result_item_particles`       | Particles that will follow items that spawn around centre when ritual is performed(It's just an particle command so you can make it more like `hand_magic_renewed:light_blue_glitter ~ ~ ~ 0.2 0.2 0.2 0.5 100 normal` if needed)            |
| `result_particle_boom`       | the same as with *_item_particles but it's played only once after ritual ending on result item position           |
| `starting_sound`       | sound that's going to be played when ritual starts           |
| `ending_sound`       | sound that's going to be played when ritual ends           |
| `item_spawn_distance`       | How far items spawn from centre           |
| `item_distance_decrease_speed`       | speed of items decreasing distance to centre(Basically when it hit's 0.1 after item spawn or less it's going to end ritual)           |
| `result_item_spin_time`       | How many ticks result item will hover above center           |
| `Ritual Name`       | Name of ritual that's going to be shown in Ritual scroll           |
| `Ritual Locked`       | True if this rituals needs to be unlocked first with Lost Ritual Page or Command           |
| `Ritual Research Symbol`       | Symbol that will be used in mod to determine if it's researched or not(If it's going to be empty it's going to be always researched and it needs to be different from other symbols, as if they are the same then it's going to unlock other rituals with same symbol)           |
| `Scroll Page Number`       | Page number in Ritual Scroll it's also -1 from real pages(So if you see it in Scroll like 31 it's 30 in json file)(If it's hidden ritual then set it to -1)           |
| `Can be found in Ritual Scroll Piece`       | If true then it's possible to find it in Ritual Scroll Piece when clicked with an empty one           |
| `Ritual Info`       | Just a small description that's going to be in Ritual Scroll           |


---

# 6. Adding a Preparation

Create `data/hand_magic_renewed/preparations_hand_magic/auris.json`:

```json
{
 "Name": "Auris",
 "Research Symbol": "",
 "First Gesture": 2,
 "Second Gesture": 0,
 "Third Gesture": 2
}
```

Fields: `Name` (Just name/id that's used in other json files and shown in the game), `Research Symbol` (If it's empty then it's always researched and if it has something it will be locked till you unlock it with `/hand_magic_renewed:unlockpreparation_debug` command(Some item's like element crystals just execute this command)), `First, Second, Third Gesture` (Just a Gesture id's that's needed to prepare this spell)).

---

# 7. Mana filling recipes

Create `data/hand_magic_renewed/mana_filling_recipes_hand_magic/mana_filled_crystal.json`:

```json
{
 "required_item": "hand_magic_renewed:element_crystal",
 "result_item": "hand_magic_renewed:mana_filled_element_crystal"
}
```

Fields: `required_item` (Required Item id in main hand for this recipe), `result_item` (Result Item id that's going to be given to executor).


---

# 8. Placeholders (Used in the Command field)

Ritual json placeholders(They can be used only in ritual json files):
  * %executor% - Executes as who pressed to start ritual

Spell json placeholders(They can be used only in spell json files):
  * %mastery_text_X% (`X` = 1,2,3) - Replaced with text coresponding to mastery level
  * %wand_text_X% (`X` = 1,2,3) - Replaced with text coresponding to wand level
  * %element_bonus_text_X% (`X` = 1,2,3) - Replaced with text coresponding to correct element
  * %executor% - ID of who executed the spell
  * %executor_x% - X coordinate of executor
  * %executor_y% - Y coordinate of executor
  * %executor_z% - Z coordinate of executor
  * %mastery_X% (`X` = 1,2,3) - Replaced with number coresponding to mastery level
  * %element_bonus_X% (`X` = 1,2,3) - Replaced with number coresponding to correct element
  * %wand_usage_X% (`X` = 1,2,3) - Replaced with number coresponding to wand level
  * %extra_number_X% (`X` = 1,2,3) - Replaced with number coresponding to extra number

`Simple two placeholder math functions`
  * %mastery_number_X # Y_X%
  * %wand_usage_X # Y_X%
  * %element_bonus_X # Y_X%
  * %extra_number_X # Y_X%
  * %executor_pos_X # Y_X%

`Replace symbols with:`
* `X` = 1,2,3 (For executor pos numbers = 1=X ,2=Y ,3=Z)
* `Y` = mastery_number , wand_usage, element_bonus, extra_number, executor_pos (Can't calculate two exact name things!(Even with different number))
* `#` = +, -, *, /

`Example: %element_bonus_1 + mastery_number_1%`

`Simple three placeholder math functions`
  * %X_S#X_S#X_S%

`Replace symbols with:`
* `X` = mastery_number, element_bonus, wand_usage, extra_number, executor_pos
* `S` = 1, 2, 3 (For executor pos numbers = 1=X ,2=Y ,3=Z)
* `#` = +, -, *, /

`Example: %mastery_number_1+element_bonus_1+extra_number%`

---

# 9. Testing locally

1. Place datapack in `world/datapacks/`.
2. Use `/reload` in world (or restart server).
3. Use debug commands:

   * `/hand_magic_renewed:unlockpreparation_debug <entity> <preparation_spell_name>` → just unlocks preparation spell.
   * `/hand_magic_renewed:lockpreparation_debug <entity> <preparation_spell_name>` → just locks preparation spell.
   * `/hand_magic_renewed:researchspell_debug <entity> <spell_name>` → researches spell or forgets if it was already researched.
   * `/hand_magic_renewed:givelostscroll_debug <entity> <page_number>` → gives lost page with page number.
   * `/hand_magic_renewed:givelostscroll_debug <entity> <page_number>` → gives lost page with page number.
   * `hand_magic_renewed:research_all_spells_debug <entity>` → researches all spells.
   * `hand_magic_renewed:forget_all_spells_debug <entity>` → forgets all spells.
   * `hand_magic_renewed:unlock_all_preparations_debug <entity>` → researches all preparations.
   * `hand_magic_renewed:lock_all_preparations_debug <entity>` → locks all preparations.
   * `hand_magic_renewed:give_research_scroll_debug <entity> <spell_name>` → gives research spell scroll with spell in it.
   * `hand_magic_renewed:setmaxmanausage_debug <entity> <max_mana>` → sets max mana.
   * `hand_magic_renewed:setmanaused_debug <entity> <mana_amount>` → sets mana amount.
   * `hand_magic_renewed:setspellcooldown_debug <entity> <cooldown_ticks_per_tick>` → sets how much ticks of cooldown are counted per tick.
   * `hand_magic_renewed:setmanaamethystclusterconsumed_debug <entity> <how_much_amethysts_consumed>` → sets how much amethysts clusters been consumed.
   * `hand_magic_renewed:setmaxmanausage_default_debug <entity>` → sets max mana to default.
   * `hand_magic_renewed:give_ritual_scroll_piece_debug <entity> <ritual_name>` → gives ritual scroll piece with ritual in it.
   * `hand_magic_renewed:researchritual_debug <entity> <ritual_name>` → researches ritual or forgets if it was already researched.
   * `hand_magic_renewed:forget_all_rituals_debug <entity>` → forgets all rituals.
   * `hand_magic_renewed:research_all_ritual_debug <entity>` → researches all rituals.
4. For rituals: just make them as normal rituals(If it's hidden one just make it not hidden one for testing).

---

## Legal

**All Rights Reserved** © *JenkiMods*  
Unauthorized use, modification, or distribution of any part of this project is strictly prohibited. (Only making datapacks are allowed and if needed extra changes msg me on curseforge so i will give you authorization!)
