# BluParticleSystem - ROA

## 🔹 Getting Started 🔹

Spawning particles can be done in only two lines!

```jsx
///// init.gml /////

// Particle Creation (init.gml)
var particle = bps_make("particle_group", sprite_get("particle"))
bps_set_particle_value(particle, BPS_DEEZ_NUTS, "dintroller")
var particle_2 = bps_make("particle_group", sprite_get("particle_2"), 0.2, 3, -50, 50, "FOLLOW", 4, 8, true, 100)

///// hit_player.gml /////

// Particle Spawning
bps_spawn("particle_group", hit_player_obj.x, hit_player_obj.y, false, spr_dir)
// Particle Destroying
bps_remove_particle(particle_2)
bps_remove_group("particle_group")
```

## 🔹 Function🔹

### `bps_make( group, sprite )`

**Returns: `Particle` ( Lightweight Object )**

- `group [ String ]`
    - The name of the group to make and/or add the particle to
- `sprite [ Sprite ID ]`
    - The sprite of the particle. Accounts for `small sprites` (so no need to upscale).

### `bps_set_particle_value( particle, index, value )`

**Returns: `Void` ( Nothing )**

- `particle [ Particle ]`
    - Particle object returned by `bps_make` function
- `index [ Real ]`
    - The index of the property to set
    - The block pasted in `init.gml` defines constants that are easier to remember instead of numbers (listed in the `Indexes` section)
- `value [ Any ]`
    - Value to set the index to
    - This can be different depending on the index
    - Check out the `Indexes` section for more info

### `bps_spawn( group, x, y, front, dir )`

### `bps_remove_particle( particle )`

### `bps_remove_group( group )`

## 🔹 Indexes🔹

| Index | Type | Desctiption |
| --- | --- | --- |
| BPS_PT_WEIGHT | Real | •How fast the particle will fall

•Setting to a negative will cause particles to rise 

•Setting to 0 will cause particles to not be affected by gravity and float and a linear path |
|  |  |  |

---

- `weight [ Real ]`
    - How fast the particle will fall.
    - Setting to a negative will cause particles to rise.
    - Setting to 0 will cause particles to not be affected by gravity and float and a linear path
- `amount [ Real ]`
    - Number of particles to spawn with called with `bps_spawn`
- `min_angle [ Real ]`
    - Minimum angle that particle can spawn with
    - Angle decides velocity of particle and sprite angle if `angle_type` = `“FOLLOW”`
    - Setting equal to `max_angle` will ensure particle will be the same angle each time
- `max_angle [ Real ]`
    - Maximum angle that particle can spawn with
    - Angle decides velocity of particle and sprite angle if `angle_type` = `“FOLLOW”`
    - Setting equal to `min_angle` will ensure particle will be the same angle each time
- `angle_type [ Real ]`
    - This function has constants that it works with (defined with the `init.gml` block you pasted in)
        - `(-1) BPS_STILL`⇒ Particle will not rotate at all
        - `(0) BPS_FOLLOW` ⇒ Particle sprite angle will change depending on velocity of sprite
        - `(1) BPS_SPIN` ⇒ Particle will spin at the speed set by the `angle_type_property` argument
