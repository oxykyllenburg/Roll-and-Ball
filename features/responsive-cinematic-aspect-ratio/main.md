# -- Responsive Cinematic Aspect Ratio --
<img src="./images/cinematic-aspect-ratio.png" width="400">
<br><br>

## Setting up
<img src="./images/setup-1.png">  <img src="./images/setup-2.png">
<br><br>

## Making it responsive
Adjust the bar size according to current screen size

  `local screenSize = screenGui.AbsoluteSize
    local gameplayHeight = screenSize.X / screenGui:GetAttribute("AspectRatio")
    local barSize = (screenSize.Y - gameplayHeight) / 2`
