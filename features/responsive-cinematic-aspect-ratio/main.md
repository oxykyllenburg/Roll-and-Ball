# -- Responsive Cinematic Aspect Ratio --
<img src="./images/cinematic-aspect-ratio.png" width="400">
<br><br>

## Setting up
<img src="./images/setup-1.png">  <img src="./images/setup-2.png">
<br><br>

## Making it responsive

Calculating each bar height depends on the screen height
```lua
local screenSize = screenGui.AbsoluteSize
local gameplayHeight = screenSize.X / screenGui:GetAttribute("AspectRatio")
local barHeight = (screenSize.Y - gameplayHeight) / 2
```

<br>

Apply the result to each bar
```lua
barTop.Size = UDim2.new(1, 0, 0 barHeight)
barBottom.Size = UDim2.new(1, 0, 0, barHright)
```

<br><br>
