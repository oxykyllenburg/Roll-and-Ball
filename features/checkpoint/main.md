# - Checkpoint
<br>

## Overview
<img src="./images/checkpoint.png" width=300>
Basically a checkpoint system
---
<br><br>

## Architecture
<img src="./images/checkpoint-arch1.png" width=200>
---
<br><br>

## Implementation
### Player leaderstats
<img src="./images/checkpoint2.png">

To show current player's checkpoint, setting up the leaderstats is mandatory
```lua
local leaderstats = Instance.new("Folder")
leaderstats.Name = "leaderstats"
leaderstats.Parent = player

local checkpoint = Instance.new("IntValue")
checkpoint.Name = "Checkpoint"
checkpoint.Value = 0
checkpoint.Parent = leaderstats
```
---
<br>

#### Checkpoint system


