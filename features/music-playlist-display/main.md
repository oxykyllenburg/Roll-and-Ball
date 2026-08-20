# Music Playlist Display

## Overview
<img src="./images/music-title-display.png" width=400>
A music playlist player for each world/biome, with a title and artist name visible
<br><br>

## Architecture
<img src="./images/arch1.png"> <img src="./images/arch2.png">
<br><br>

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
<br><br>

## 
