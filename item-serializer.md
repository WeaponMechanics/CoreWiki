---
description: Constructs an item from config
---

# Item Serializer

```yaml
Item:
  Type: <Material>
  Name: <name>
  Lore:
  - <Lore line>
  - <etc.>
  Durability: <durability>
  Unbreakable: <true/false>
  Custom_Model_Data: <custom model data number>
  Hide_Flags: <true/false>
  Enchantments:
  - <Enchantment> <Level>
  Skull_Owning_Player: <UUID of player or name of player>
  Potion_Color: <Color>
  Attributes:
  - <Attribute> <Amount> <Slot>
  Leather_Color: <Color>
  Light_Level: <1-16>
  Firework:
    Power: <firework power>
    Effects:
      - <Firework.Type> <ColorSerializer>
      - <Firework.Type> <ColorSerializer> <Trail> <Flicker>
      - <Firework.Type> <ColorSerializer> <Trail> <Flicker> <fade ColorSerializer>
      - <etc.>
  Deny_Use_In_Crafting: <true/false>
  Recipe:
    Shape:
      - "012"
      - "345"
      - "678"
    Ingredients:
      '0': <ItemSerializer>
      '1': <ItemSerializer>
      <etc.>
    Output_Amount: <Integer>
  Tags:
    - <String> <Integer>
```

{% hint style="info" %}
## Shorthand

Just looking for a simple vanilla item (no lore, no display, etc.)? Then, use a shorthand by specifying the [#material](references.md#material "mention") without any other config options.&#x20;

```yaml
Item: DIRT # Shorthand for dirt
```
{% endhint %}

#### Type

The [#material](references.md#material "mention") used for the item. For example, `feather`.

#### Name

The display name of the item.

<details>

<summary>Color Codes</summary>

We use[ MiniMessage](https://docs.advntr.dev/minimessage/format.html) to parse messages, a text format that allows colors, links, hoverables, and many other features. MiniMessage also provides an [editor](https://webui.advntr.dev/) for you to build your messages! Check out the default colors below:

<img src=".gitbook/assets/181638380-921e157d-15d2-46ab-abe6-189ce1795b9b (1).png" alt="Default color codes" data-size="original">

</details>

#### Lore

A list of strings to use as the lore of the item.&#x20;

<details>

<summary>Color Codes</summary>

We use[ MiniMessage](https://docs.advntr.dev/minimessage/format.html) to parse messages, a text format that allows colors, links, hoverables, and many other features. MiniMessage also provides an [editor](https://webui.advntr.dev/) for you to build your messages! Check out the default colors below:

<img src=".gitbook/assets/181638380-921e157d-15d2-46ab-abe6-189ce1795b9b (1).png" alt="Default color codes" data-size="original">

</details>

#### Durability

Set the damage of the item for damageable items (Like fishing rods, and armor).

#### Unbreakable

Use `true` for the item to be unbreakable. Unbreakable items do not show their durability bar, and can never be broken by durability.&#x20;

#### Custom\_Model\_Data

The [custom model data](https://www.planetminecraft.com/forums/communities/texturing/new-1-14-custom-item-models-tuto-578834/) of the item. Your server must be in MC 1.14.4 or higher.&#x20;

#### Hide\_Flags

Hides all item flags (Enchantments, Attributes, Unbreakable, Destroys, Placed on, Potion effects, Dye color).

#### Enchantments

Adds a list of enchantments with specified levels. Use the [#enchantment](references.md#enchantment "mention") list.&#x20;

The following example gives sharpness 5 and smite 5:

```yaml
  Item:
    # Other args...
    Enchantments:
      - sharpness 5
      - smite 5
```

#### Skull\_Owning\_Player

The name of the player to use if `Type: PLAYER_HEAD`. Want to use custom player heads? Use the format `"UUID URL"`.&#x20;

{% embed url="https://youtu.be/16XfZm3xqPs" %}
Custom player head tutorial
{% endembed %}

#### Potion\_Color

The color of the potion bottle if `Type: POTION`. Uses [.](./ "mention").&#x20;

For example, `Potion_Color: "255-0-0"` is red.&#x20;

#### Attributes

List of attributes to apply to the item. Follows the format `attribute value slot`. The "slot" argument is optional; leaving it blank will let all slots work for the attribute.&#x20;

| Attribute                      | Description                                                                                                            |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| `GENERIC_MOVEMENT_SPEED`       | A value of `0.10` increases speed by 10%.                                                                              |
| `GENERIC_MAX_HEALTH`           | A value of 20 adds 20 health to the entity (a second row of hearts).                                                   |
| `GENERIC_ATTACK_DAMAGE`        | A value of `7.0` will be as strong as a diamond sword.                                                                 |
| `GENERIC_ATTACK_SPEED`         | A value of `4.0` will allow 4 full strength attacks every second.                                                      |
| `GENERIC_KNOCKBACK_RESISTANCE` | A value of `0.25` is 25% less knockback taken.                                                                         |
| `GENERIC_ARMOR`                | A value of 2 provides 1 full armor point.                                                                              |
| `GENERIC_ARMOR_TOUGHNESS`      | Higher values prevent stronger attacks from dealing high damage. [More info](https://minecraft.fandom.com/wiki/Armor). |

Attributes can be added to the following slots:

1. `MAIN_HAND`
2. `OFF_HAND`
3. `HEAD`
4. `CHEST`
5. `LEGS`
6. `FEET`

Example:

```yaml
  Attributes:
  - GENERIC_MAX_HEALTH 5 feet               # gain 2.5 hearts
  - GENERIC_KNOCKBACK_RESISTANCE 0.25 feet  # take 25% less knockback
  - GENERIC_MOVEMENT_SPEED -0.07 feet       # go very slow
```

#### Leather\_Color

The color of your leather armor (Make sure your `Type` is a leather armor). Uses [.](./ "mention").

#### Light\_Level

The light level used if you are using `LIGHT` as your material. This is usually used in [Particle](https://app.gitbook.com/s/hz7yMxlL81NxAT44nraH/mechanics/particle "mention") to spawn custom `BLOCK_MARKER` particles. This can be used for smoke grenades. Notice how in the example below for the [Particle](https://app.gitbook.com/s/hz7yMxlL81NxAT44nraH/mechanics/particle "mention") mechanic, instead of just using `materialData=LIGHT`, we used `materialData={type=LIGHT, lightLevel=0}`.&#x20;

```yaml
      - "Particle{particle=block_marker, materialData={type=LIGHT, lightLevel=0}, count=20, noise=3 2 3, repeatInterval=1, repeatAmount=580}"
```

#### Firework

Sets the firework data of the firework. Make sure to use `Type: firework_rocket` or `Type: firework` with this depending on your server version.

* `Power`: \<Integer>
  * Defines the power of firework
* `Effects`: \<String List>
  * Format: `<shape> <color> <trail> <flicker> <fadeColor>`
  * `shape`:
    * Required value which defines firework type
    * Available values: `BALL`, `BALL_LARGE`, `STAR`, `BURST`, `CREEPER`
  * `color`:
    * Required value which defines firework color
    * For example, `#ff0000` is red.
    * Uses [.](./ "mention")
  * `trail`:
    * true or false
    * Optional value which defines whether firework has [trail](https://minecraft.fandom.com/wiki/Firework\_Star#Additional\_effects)
  * `flicker`:
    * true or false
    * Optional value which defines whether firework has [flicker](https://minecraft.fandom.com/wiki/Firework\_Star#Additional\_effects) (twinkle).
  * `fadeColor`:
    * Optional value which defines firework fade color
    * For example, `#ffff00` is yellow.
    * Uses [.](./ "mention")

#### Deny\_Use\_In\_Crafting

Use `true` to prevent this item from being used in crafting.

{% hint style="warning" %}
This option also disables shift-clicking items. To let players shift-click items, use `Deny_Use_In_Crafting: false` or delete the option from your config (Defaults to false).&#x20;
{% endhint %}

#### Recipe

{% hint style="info" %}
When modifying your recipe config, you **must restart your server.** Recipes are only refreshed on restarts.
{% endhint %}

* `Shape` -> The shape of the crafting recipe. Use single letters.
* `Ingredients` -> The items required to craft.
* `Output_Amount` -> How many items to output (Like 4 arrows). Defaults to 1.&#x20;

{% embed url="https://www.youtube.com/watch?v=OUhRLyh1mAg" %}
Item crafting recipe tutorial
{% endembed %}

For example, the following recipe creates a recipe like an emerald sword:

![](.gitbook/assets/151718278-4619f84c-072c-46dc-958d-6c11db10534c.png)

```yaml
  Recipe:
    Shape:
      - "e"
      - "e"
      - "s"
    Ingredients:
      'e': EMERALD
      's': STICK
```

#### Tags

These are custom NBT tags given to your item that have **NO EFFECT** on the behavior of the item. This is useful for commands, like: `/minecraft:clear @p feather{"PublicBukkitValues":{"custom:<your_tag_here>":<your number here>}}`.
