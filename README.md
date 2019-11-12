# Latency Protection
Latency protection mod attempts to prevent players from glitching through protected nodes.    
By either teleporting the player or damaging them.

## Installation
- Unzip the archive, rename the folder to `latency_protection` and
place it in .. minetest/mods/

- GNU/Linux: If you use a system-wide installation place
    it in ~/.minetest/mods/.

- If you only want this to be used in a single world, place
    the folder in .. worldmods/ in your world directory.

For further information or help, see:   
https://wiki.minetest.net/Installing_Mods

## Damage mode
This mode attempts to prevent players from glitching through protected nodes. By damaging players who interact with a protected position too fast.

## Teleport mode
This mode attempts to prevent players from glitching through protected nodes. By recording position every 20 seconds (This can be changed in settings) and teleporting them if the protection interaction happens in a very quick time frame. If a player interacts with a protected node the position will not be recorded for an extra cycle. Before recording a position, the player’s avg_jitter is checked to make sure the player is not lagging out.

The timer for when to record a player position.   
This only works if punishment is set to teleport.

```lua
latency_protection.timer = 20
```

The max jitter a player can have before refusing the position update.    
This only works if punishment is set to teleport.
```lua
latency_protection.jitter_max = 1.5
```

The time limit between is_protected calls.    
If the function is called too fast the player will be teleport or damaged.    
`time_max` is read in microseconds.

```lua
latency_protection.time_max = 2000
```

Damage amount to apply to the player.   
This only works if punishment is set to damage.

```lua
latency_protection.damage = 3
```

Set what type of punishment will be given to a player:
- Teleport the player.
- Damage the player.

```lua
latency_protection.punishment = "damage"
```