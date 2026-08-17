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
