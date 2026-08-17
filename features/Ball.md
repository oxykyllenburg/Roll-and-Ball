# -- Ball Movement --

<img src="../images/ball.png" width="200">
<br><br>

## Setting up the ball
`
	local moveDir = humanoid.MoveDirection
	moveDir = Vector3.new(moveDir.Z, 0, -moveDir.X)
	
	ball:ApplyAngularImpulse(moveDir * force)
	ball:ApplyAngularImpulse(-ball.AssemblyAngularVelocity / 2)
`
