# - Music Playlist Display

## Overview
<img src="./images/music-title-display.png" width=400>
A music playlist player for each world/biome, with a title and artist name visible
<br> --- <br><br>

## Architecture
<img src="./images/arch1.png"> <img src="./images/arch2.png">
<br> --- <br><br>

## Playlist Configuration
Playlists are stored in a dictionary inside the module ('GetPlaylist')
```lua
local list = {
    ["Biome1"] = "Happy song", "Happy song2",
    ["Biome2"] = "Sad song", "Sad song2",
}
```
<br>

A function to return the requested playlist
```lua
return function(biomeName)
    return list[biomeName]
end
```
<br>

## Music player
Set a few empty variables
```lua
local thread
local currentSong
local previousBiome
```
<br>

Check the current biome every time the player spawn/respawn
```lua
local leaderstats = player:WaitForChild("leaderstats")
local checkpoint = leaderstats:WaitForChild("Checkpoint")

local biome = GetBiomeName(checkpoint.Value)
if biome == previousBiome then return end
```
If it's the same biome as before, do nothing
<br>

If current biome is different, change to new playlist
```lua
local list = GetPlaylist(biome)
thread = coroutine.create(playlist)
coroutine.resume(thread, list)
```
