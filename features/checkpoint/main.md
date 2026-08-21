# - Checkpoint
<br>

## Overview
<img src="./images/checkpoint.png" width=300>
Basically a checkpoint system
<br> --- <br><br>

## Architecture
<img src="./images/checkpoint-arch1.png" width=200>
---
<br><br>

## Implementation
<br>

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
<br><br>

### Check and update player's checkpoint when a checkpoint touched
```lua
local playerCheckpoint = leaderstats:FindFirstChild("Checkpoint")
if playerCheckpoint.Value ~= touchedCheckpointPosition - 1 then return end
playerCheckpoint.Value = touchedCheckpointPosition
```
Ensure that players pass through the correct checkpoints in the correct order
<br><br>

### Set player's respawn location to checkpoint's position
```lua
playerCheckpoint.Changed:Connect(function(position)

    local checkpoint = checkpointFolder:FindFirstChild(tostring(position))
    if checkpoint then player.RespawnLocation = checkpoint end

end)
```
--- <br><br>

## Usage
<br>

### OnPlayerAdded
```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player

    local checkpoint = Instance.new("IntValue")
    checkpoint.Name = "Checkpoint"
    checkpoint.Value = 0 --or saved player's checkpoint data value
    checkpoint.Parent = player

end)
```
<br>

### Checkpoint ServerScript
Loop through every single checkpoint to verify and update player's checkpoint
```lua
local Players = game:GetService("Players")

local checkpointFolder = workspace:FindFirstChild("CheckpointFolder")

for _, checkpoint in checkpointFolder:GetChildren() do

    local checkpointPosition = tonumber(checkpoint.Name)
    checkpoint.Touched:Connect(function(other)

        if other.Name ~= "Head" then return end
        local player = Players:GetPlayerFromCharacter(other.Parent)
        if not player then return end

        local leaderstats = player:FindFirstChild("leaderstats")
        if not leaderstats then return end

        local playerCheckpoint = leaderstats:FindFirstChild("Checkpoint")
        if not playerCheckpoint or playerCheckpoint.Value ~= checkpointPosition - 1 then return end

        playerCheckpoint.Value = checkpointPosition
        
    end)

end
```
