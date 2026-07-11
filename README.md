# Casualties-Chained-Together
Mod for Casualties Unknown that lets you chain people together

## Installation instructions
Download the mod from the [Nexus](https://www.nexusmods.com/scavprototype/mods/422?tab=files) or the releases tab. Unzip and copy the BepInEx folder and paste it directly into the folder that opens from browse local files.

## Usage

```
chaintogether [player] [player] [length]
```
Chains two players together. Length is optional and defaults to 12. You can specify a player by name or id, same conventions as the multiplayer mod.


```
deletechain [player|all] [player]
```
Deletes a chain between two players, or deletes all chains with `deletechain all`



```
setchainphysics [setting] [value]
```
Lets you change chain physics settings at runtime. Changes are not persisted.


## Chain physics settings
Once you first load up the game, a settings.json file is generated in the same directory as the mod .dll, `BepInEx\plugins\ChainedTogether\settings.json`.

| Property                  | Description                                                                                                                                                          |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PullAcceleration          | How much the pull force increases with distance                                                                                                                      |
| InitialTautForce          | How much inital pull force is applied when chain is taut                                                                                                             |
| MaxPullAcceleration       | Maximum acceleration from chain pull                                                                                                                                 |
| MassPullMultiplier        | How much different weights effect physics. 0 means all players are identical, with greater numbers meaning heavier players (body weight & items) pull harder         |
| TautRagdollThreshold      | If in the air and the chain is stretched by more than this value, then count down RagdollGracePeriodSeconds until force player ragdoll and decrease respiratory rate |
| RagdollGracePeriodSeconds | How many seconds before a player ragdoll is forced when dangling in the air                                                                                          |

Force applied by the chain is `0` when the `distance < chain_length`, and roughly `Min(InitalTautForce + excess * PullAcceleration, MaxPullAcceleration)` otherwise.
