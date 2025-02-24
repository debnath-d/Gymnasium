---
title: Asteroids
---

# Asteroids

```{figure} ../../_static/videos/atari/asteroids.gif
:width: 120px
:name: Asteroids
```

This environment is part of the <a href='..'>Atari environments</a>. Please read that page first for general information.

## Description

This is a well-known arcade game: You control a spaceship in an asteroid field and must break up asteroids by shooting them. Once all asteroids are destroyed, you enter a new level and new asteroids will appear. You will occasionally be attacked by a flying saucer.

For a more detailed documentation, see [the AtariAge page](https://atariage.com/manual_html_page.php?SoftwareID=828)

## Actions

Asteroids has the action space `Discrete(14)` with the table below lists the meaning of each action's meanings.
As Asteroids uses a reduced set of actions for `v0`, `v4` and `v5` versions of the environment.
To enable all 18 possible actions that can be performed on an Atari 2600, specify `full_action_space=True` during
initialization or by passing `full_action_space=True` to `gymnasium.make`.

| Value   | Meaning       |
|---------|---------------|
| `0`     | `NOOP`        |
| `1`     | `FIRE`        |
| `2`     | `UP`          |
| `3`     | `RIGHT`       |
| `4`     | `LEFT`        |
| `5`     | `DOWN`        |
| `6`     | `UPRIGHT`     |
| `7`     | `UPLEFT`      |
| `8`     | `UPFIRE`      |
| `9`     | `RIGHTFIRE`   |
| `10`    | `LEFTFIRE`    |
| `11`    | `DOWNFIRE`    |
| `12`    | `UPRIGHTFIRE` |
| `13`    | `UPLEFTFIRE`  |

## Observations

Atari environment have two possible observation types, the observation space is listed below.
See variants section for the type of observation used by each environment id.

- `obs_type="rgb" -> observation_space=Box(0, 255, (210, 160, 3), np.uint8)`
- `obs_type="ram" -> observation_space=Box(0, 255, (128,), np.uint8)`

Additionally, `obs_type="grayscale"` cause the environment return a grayscale version of the rgb array for observations with the observation space being `Box(0, 255, (210, 160), np.uint8)`
### Rewards

You score points for destroying asteroids, satellites and UFOs. The smaller the asteroid, the more points you score
for destroying it.
For a more detailed documentation, see [the AtariAge page](https://atariage.com/manual_html_page.php?SystemID=2600&SoftwareID=828&itemTypeID=HTMLMANUAL).

## Variants

Asteroids has the following variants of the environment id which have the following differences in observation,
the number of frame-skips and the repeat action probability.

| Env-id                        | obs_type=   | frameskip=   | repeat_action_probability=   |
|-------------------------------|-------------|--------------|------------------------------|
| Asteroids-v0                  | `"rgb"`     | `(2, 5)`     | `0.25`                       |
| Asteroids-ram-v0              | `"ram"`     | `(2, 5)`     | `0.25`                       |
| Asteroids-ramDeterministic-v0 | `"ram"`     | `4`          | `0.25`                       |
| Asteroids-ramNoFrameskip-v0   | `"ram"`     | `1`          | `0.25`                       |
| AsteroidsDeterministic-v0     | `"rgb"`     | `4`          | `0.25`                       |
| AsteroidsNoFrameskip-v0       | `"rgb"`     | `1`          | `0.25`                       |
| Asteroids-v4                  | `"rgb"`     | `(2, 5)`     | `0.0`                        |
| Asteroids-ram-v4              | `"ram"`     | `(2, 5)`     | `0.0`                        |
| Asteroids-ramDeterministic-v4 | `"ram"`     | `4`          | `0.0`                        |
| Asteroids-ramNoFrameskip-v4   | `"ram"`     | `1`          | `0.0`                        |
| AsteroidsDeterministic-v4     | `"rgb"`     | `4`          | `0.0`                        |
| AsteroidsNoFrameskip-v4       | `"rgb"`     | `1`          | `0.0`                        |
| ALE/Asteroids-v5              | `"rgb"`     | `4`          | `0.25`                       |
| ALE/Asteroids-ram-v5          | `"ram"`     | `4`          | `0.25`                       |

## Difficulty and modes

It is possible to specify various flavors of the environment via the keyword arguments `difficulty` and `mode`.
A flavor is a combination of a game mode and a difficulty setting. The table below lists the possible difficulty and mode values
along with the default values.

| Available Modes     | Default Mode   | Available Difficulties   | Default Difficulty   |
|---------------------|----------------|--------------------------|----------------------|
| `[0, ..., 31, 128]` | `0`            | `[0, 3]`                 | `0`                  |

## Version History

A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the "ALE" namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release
