---
title: Skiing
---

# Skiing

```{figure} ../../_static/videos/atari/skiing.gif
:width: 120px
:name: Skiing
```

This environment is part of the <a href='..'>Atari environments</a>. Please read that page first for general information.

## Description

You control a skier who can move sideways.The goal is to run through all gates (between the poles) in the fastest time.You are penalized five seconds for each gate you miss.If you hit a gate or a tree, your skier will jump back up and keep going.

For a more detailed documentation, see [the AtariAge page](https://atariage.com/manual_html_page.php?SoftwareLabelID=434)

## Actions

Skiing has the action space `Discrete(3)` with the table below lists the meaning of each action's meanings.
As Skiing uses a reduced set of actions for `v0`, `v4` and `v5` versions of the environment.
To enable all 18 possible actions that can be performed on an Atari 2600, specify `full_action_space=True` during
initialization or by passing `full_action_space=True` to `gymnasium.make`.

| Value   | Meaning   |
|---------|-----------|
| `0`     | `NOOP`    |
| `1`     | `RIGHT`   |
| `2`     | `LEFT`    |

## Observations

Atari environment have two possible observation types, the observation space is listed below.
See variants section for the type of observation used by each environment id.

- `obs_type="rgb" -> observation_space=Box(0, 255, (210, 160, 3), np.uint8)`
- `obs_type="ram" -> observation_space=Box(0, 255, (128,), np.uint8)`

Additionally, `obs_type="grayscale"` cause the environment return a grayscale version of the rgb array for observations with the observation space being `Box(0, 255, (210, 160), np.uint8)`
### Rewards

Seconds are your only rewards - negative rewards and penalties (e.g. missing a gate) are assigned as additional seconds.

For a more detailed documentation, see [the AtariAge page [SLALOM RACING section]](https://atariage.com/manual_html_page.php?SoftwareLabelID=434).

## Variants

Skiing has the following variants of the environment id which have the following differences in observation,
the number of frame-skips and the repeat action probability.

| Env-id                     | obs_type=   | frameskip=   | repeat_action_probability=   |
|----------------------------|-------------|--------------|------------------------------|
| Skiing-v0                  | `"rgb"`     | `(2, 5)`     | `0.25`                       |
| Skiing-ram-v0              | `"ram"`     | `(2, 5)`     | `0.25`                       |
| Skiing-ramDeterministic-v0 | `"ram"`     | `4`          | `0.25`                       |
| Skiing-ramNoFrameskip-v0   | `"ram"`     | `1`          | `0.25`                       |
| SkiingDeterministic-v0     | `"rgb"`     | `4`          | `0.25`                       |
| SkiingNoFrameskip-v0       | `"rgb"`     | `1`          | `0.25`                       |
| Skiing-v4                  | `"rgb"`     | `(2, 5)`     | `0.0`                        |
| Skiing-ram-v4              | `"ram"`     | `(2, 5)`     | `0.0`                        |
| Skiing-ramDeterministic-v4 | `"ram"`     | `4`          | `0.0`                        |
| Skiing-ramNoFrameskip-v4   | `"ram"`     | `1`          | `0.0`                        |
| SkiingDeterministic-v4     | `"rgb"`     | `4`          | `0.0`                        |
| SkiingNoFrameskip-v4       | `"rgb"`     | `1`          | `0.0`                        |
| ALE/Skiing-v5              | `"rgb"`     | `4`          | `0.25`                       |
| ALE/Skiing-ram-v5          | `"ram"`     | `4`          | `0.25`                       |

## Difficulty and modes

It is possible to specify various flavors of the environment via the keyword arguments `difficulty` and `mode`.
A flavor is a combination of a game mode and a difficulty setting. The table below lists the possible difficulty and mode values
along with the default values.

| Available Modes   | Default Mode   | Available Difficulties   | Default Difficulty   |
|-------------------|----------------|--------------------------|----------------------|
| `[0]`             | `0`            | `[0]`                    | `0`                  |

## Version History

A thorough discussion of the intricate differences between the versions and configurations can be found in the general article on Atari environments.

* v5: Stickiness was added back and stochastic frameskipping was removed. The environments are now in the "ALE" namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release
