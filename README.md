# BluParticleSystem - ROA

## Getting Started 🚩

Spawning particles can be done in only two lines!

```jsx
///// init.gml /////

// Particle Creation (init.gml)
particle = bps_make("particle_group", sprite_get("water_drop"))
particle_2 = bps_make("particle_group", sprite_get("water_drop_2"))

bps_set_particle_value(particle, BPS_PT_WEIGHT, 0.25)
bps_set_particle_value(particle, BPS_PT_AMOUNT, 4)
bps_set_particle_value(particle, BPS_PT_MIN_SPEED, 5)
bps_set_particle_value(particle, BPS_PT_MAX_SPEED, 10)
bps_set_particle_value(particle, BPS_PT_MIN_ANGLE, 30)
bps_set_particle_value(particle, BPS_PT_MAX_ANGLE, 120)

bps_set_particle_value(particle_2, BPS_PT_WEIGHT, 0.25)
bps_set_particle_value(particle_2, BPS_PT_AMOUNT, 4)
bps_set_particle_value(particle_2, BPS_PT_MIN_SPEED, 5)
bps_set_particle_value(particle_2, BPS_PT_MAX_SPEED, 10)
bps_set_particle_value(particle_2, BPS_PT_MIN_ANGLE, 30)
bps_set_particle_value(particle_2, BPS_PT_MAX_ANGLE, 120)

///// hit_player.gml /////

// Particle Spawning
bps_spawn("particle_group", hit_player_obj.x, hit_player_obj.y, false, spr_dir)
// Particle Destroying
bps_remove_particle(particle_2)
bps_remove_group("particle_group")
```

## Function ⚙

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

## Indexes 🔎

|  | Index | Type | Default Value | Desctiption |
| --- | --- | --- | --- | --- |
| 0 | BPS_PT_WEIGHT | Real | 0.1 | How fast the particle will fall. Setting to a negative will cause particles to rise. Setting to 0 will cause particles to not be affected by gravity and float and a linear path |
| 1 | BPS_PT_AMOUNT | Real | 3 | Number of particles to spawn with called with bps_spawn |
| 2 | BPS_PT_MIN_ANGLE | Real | -45 | Minimum angle that particle can spawn with. Angle decides velocity of particle and sprite angle if angle_type = BPS_AT_FOLLOW.Setting equal to max_angle will ensure particle will be the same angle each time |
| 3 | BPS_PT_MAX_ANGLE | Real | 45 | Maximum angle that particle can spawn with. Angle decides velocity of particle and sprite angle if angle_type = BPS_AT_FOLLOW. Setting equal to min_angle will ensure particle will be the same angle each time |
| 4 | BPS_PT_ANGLE_TYPE | Real | 0 | This function has constants that it works with (defined with the init.gml block you pasted in). Angle Types are defined in the Angle Types section |
| 5 | BPS_PT_AT_SPIN_SPEED | Real | 10 | • Speed at which particle spins
• Only works after BPS_PT_ANGLE_TYPE = BPS_AT_SPIN (1) |
| 6 | BPS_PT_MIN_SPEED | Real | 4 | The minimum amount of speed a particle can spawn. Setting the same as BPS_PT_MAX_SPEED will make the particle spawn at the same speed |
| 7 | BPS_PT_MAX_SPEED | Real | 8 | The maximum amount of speed a particle can spawn. Setting the same as BPS_PT_MIN_SPEED will make the particle spawn at the same speed |
| 8 | BPS_PT_SHADER | Boolean | true | Whether the sprite is affected by the characters current color or not |
| 9 | BPS_PT_LIFETIME | Real | 100 | The amount frames the particle is drawn |

## Angle Types 📐

|  | Index | Description |
| --- | --- | --- |
| -1 | BPS_AT_STILL | Particle will not rotate at all |
| 0 | BPS_AT_FOLLOW | Particle sprite angle will change depending on velocity of sprite |
| 1 | BPS_AT_SPIN | Particle will spin at the speed set by BPS_PT_AT_SPIN_SPEED |
