# BuildingGrades

Oxide plugin for Rust. Allows players to easily upgrade or downgrade an entire building

This plugin allows admins, and regular players, to easily upgrade or downgrade an entire building by one grade, relative to the current grade of each building block.


## Permissions

- `buildinggrades.use` -- Allows to use commands.
- `buildinggrades.admin` -- Upgrade/Downgrade buildings bypassing entity owner and TC.
- `buildinggrades.nocost` -- Allow players to upgrade buildings for free.
- `buildinggrades.up.all` -- Allow players to upgrade to all grades of buildings.
- `buildinggrades.down.all` -- Allow players to downgrade to all grades of buildings.
- `buildinggrades.down.0` -- Allow players to downgrade to Twigs grade.
- `buildinggrades.down.1` -- Allow players to downgrade to Wood grade.
- `buildinggrades.down.2` -- Allow players to downgrade to Stone grade.
- `buildinggrades.down.3` -- Allow players to downgrade to Metal grade.
- `buildinggrades.up.1` -- Allow players to upgrade to Wood grade.
- `buildinggrades.up.2` -- Allow players to upgrade to Stone grade.
- `buildinggrades.up.3` -- Allow players to upgrade to Metal grade.
- `buildinggrades.up.4` -- Allow players to upgrade to TopTier grade.

## Chat Commands

- `/up [grade] [filter]` or `/up [filter]` -- Upgrade each block which is attached to the building you are looking at by one grade or to selected grade. e.g. `/up` , `/up 2`, `/up 1 wall`, `/up wall`
- `/down [grade] [filter]` or `/down [filter]` -- Downgrade each block which is attached to the building you are looking at by one grade or to selected grade. e.g. `/down`, `/down 1`, `/down 1 wall`,  `/down wall`

- `/up` and `/down`： Upgrade/Downgrade an entire building (won't upgrade buildings that are close to eachother) (VERY fast even on big buildings) . 
- `/upall` and `/downall`: Upgrade/Downgrade everything that touchs each other starting where you are looking at (will upgrade/downgrade multiple buildings if they are too close to each other) (might be slow for big buildings)

## Grades

* Twigs or 0
* Wood or 1
* Stone or 2
* Metal or 3
* TopTier or 4

## Default Filters

* foundation
* wall
* floor
* stair
* roof
* ramp


## Configuration

```json
{
  "Settings": {
    "Use Teams": false,
    "Use Clans": true,
    "Use Friends": true,
    "Use Raid Blocker (Need NoEscape Plugin)": false,
    "Use Combat Blocker (Need NoEscape Plugin)": false,
    "Cooldown Exclude Admins": true,
    "Upgrade/Downgrade Per Frame": 10
  },
  "Chat Settings": {
    "Upgrade Chat Command": "up",
    "Downgrade Chat Command": "down",
    "Upgrade All Chat Command": "upall",
    "Downgrade All Chat Command": "downall",
    "Chat Prefix": "<color=#00FFFF>[BuildingGrades]</color>: ",
    "Chat SteamID Icon": 0
  },
  "Permission Settings": {
    "buildinggrades.use": {
      "Priority": 0,
      "Distance": 10.0,
      "Cooldown": 60.0,
      "Pay": true
    }
  },
  "Building Block Categories": {
    "foundation": [
      "assets/prefabs/building core/foundation/foundation.prefab",
      "assets/prefabs/building core/foundation.steps/foundation.steps.prefab",
      "assets/prefabs/building core/foundation.triangle/foundation.triangle.prefab"
    ],
    "wall": [
      "assets/prefabs/building core/wall/wall.prefab",
      "assets/prefabs/building core/wall.doorway/wall.doorway.prefab",
      "assets/prefabs/building core/wall.frame/wall.frame.prefab",
      "assets/prefabs/building core/wall.half/wall.half.prefab",
      "assets/prefabs/building core/wall.low/wall.low.prefab",
      "assets/prefabs/building core/wall.window/wall.window.prefab"
    ],
    "floor": [
      "assets/prefabs/building core/floor/floor.prefab",
      "assets/prefabs/building core/floor.frame/floor.frame.prefab",
      "assets/prefabs/building core/floor.triangle/floor.triangle.prefab",
      "assets/prefabs/building core/floor.triangle.frame/floor.triangle.frame.prefab"
    ],
    "stair": [
      "assets/prefabs/building core/stairs.l/block.stair.lshape.prefab",
      "assets/prefabs/building core/stairs.spiral/block.stair.spiral.prefab",
      "assets/prefabs/building core/stairs.spiral.triangle/block.stair.spiral.triangle.prefab",
      "assets/prefabs/building core/stairs.u/block.stair.ushape.prefab"
    ],
    "roof": [
      "assets/prefabs/building core/roof/roof.prefab",
      "assets/prefabs/building core/roof.triangle/roof.triangle.prefab"
    ],
    "ramp": [
      "assets/prefabs/building core/ramp/ramp.prefab"
    ]
  }
}
```

## API
```csharp
  private bool IsProcessingBuildingBlock(BuildingBlock buildingBlock) // Used to determine if a building block is processing, in the "OnStructureUpgrade" hook
```

## Hook
```csharp
    void OnStructureGradeUpdated(BuildingBlock buildingBlock, BasePlayer player, BuildingGrade.Enum oldGrade, BuildingGrade.Enum newGrade)
```


## Credits
Credits to bawNg for writing the plugin, and to Nogrod & Arainrr for maintaining it.