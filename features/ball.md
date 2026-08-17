# -- Ball --

<img src="../images/ball.png" width="200">
<br><br>

## Setting up the ball

<img src="../images/ball-setup.png">
<br><br>

## Ball movement

To make the ball moving according to player's input, we need to get the humanoid's move direction

	local moveDir = humanoid.MoveDirection

<br>

Then, we manipulate the value for each axis

	moveDir = Vector3.new(moveDir.Z, 0, -moveDir.X)
	
*my case
<br>

Multiply the move direction and apply it to our ball

	ball:ApplyAngularImpulse(moveDir * force)

<br>

(Optional) add some resistor so it will slow down fast

	ball:ApplyAngularImpulse(-ball.AssemblyAngularVelocity / 2)

<br><br>

### Example of usage

	local runService = game:GetService("RunService")
	local replicatedStorage = game:GetService("ReplicatedStorage")
	local uis = game:GetService("UserInputService")
	
	local player = game.Players.LocalPlayer
	local camera = workspace.CurrentCamera
	
	local char = player.Character or player.CharacterAdded:Wait()
	local ball: Part = char:WaitForChild("Head", math.huge)
	local humanoid = char:WaitForChild("Humanoid", math.huge)
	
	local force = 7
	
	runService.Heartbeat:Connect(function()
		
		local moveDir = humanoid.MoveDirection
		moveDir = Vector3.new(moveDir.Z, 0, -moveDir.X)
		
		ball:ApplyAngularImpulse(moveDir * force)
		ball:ApplyAngularImpulse(-ball.AssemblyAngularVelocity / 2)
		
	end)
	
