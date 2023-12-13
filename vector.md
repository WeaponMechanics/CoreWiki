# Vector

Vectors are used in [Mechanics](https://app.gitbook.com/o/MgHAZkcfIhs3YcmBjk2r/s/hz7yMxlL81NxAT44nraH/ "mention") and in other config options. A vector can follow a few different formats; make sure to choose the format that works for you:

## Direct

The direct vector format lets you specify the _exact_ x y z coordinates. Here are some examples:

```yaml
0 1 0    # 0 blocks east, 1 block up, 0 blocks north
-10 5 1  # 10 blocks west, 5 blocks up, 1 block north  
```

## Relative

The relative format takes the current entity's direction and uses its forward direction. This lets you specify forward, backward, left, and right instead of north, south, east, and west.&#x20;

Relative vectors start with the `~` character.&#x20;

```yaml
~0 0 1  # 0 blocks left, 0 blocks up, 1 block forward 
~0 5 0  # 0 blocks left, 5 blocks up, 0 blocks forward 
```

## Simple

The simple format is just like the [#relative](vector.md#relative "mention") format, but in 1-block increments:

```yaml
UP        # 1 block up
DOWN      # 1 block down
LEFT      # 1 block left
RIGHT     # 1 block right
FORWARD   # 1 block forward
BACKWARD  # 1 block backward
```

## Random

Chooses a random direction with a given length. Random vectors start with the `r` character:

```yaml
r1.0  # 1 block in a random direction
r25   # 25 blocks in a random direction
```
