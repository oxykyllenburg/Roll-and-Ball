# -- Ball --

<img src="../images/ball.png" width="200">
<br><br>

## Setting up the ball

<img src="../images/ball-setup.png">
<br><br>

## Ball movement

To make the ball according to player's input,

	local moveDir = humanoid.MoveDirection
	moveDir = Vector3.new(moveDir.Z, 0, -moveDir.X)
	
	ball:ApplyAngularImpulse(moveDir * force)
	ball:ApplyAngularImpulse(-ball.AssemblyAngularVelocity / 2)
