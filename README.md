local PositionTorso = script.Parent.Torso.Position

function findNearestTorso(pos)
	local list = game.Workspace:children()
	local torso = nil
	local dist = 100000000
	local temp = nil
	local human = nil
	local temp2 = nil
	for x = 1, #list do
		temp2 = list[x]
		if (temp2.className == "Model") and (temp2 ~= script.Parent) then
			temp = temp2:findFirstChild("UpperTorso")
			human = temp2:findFirstChild("Humanoid")
			if (temp ~= nil) and (human ~= nil) and (human.Health > 0) then
				if (temp.Position - pos).magnitude < dist then
					torso = temp
					dist = (temp.Position - pos).magnitude
				end
			end
		end
	end
	return torso
end

while wait(0.15) do
	local target = findNearestTorso(PositionTorso)
	if target ~= nil then
		script.Parent.Humanoid:MoveTo(target.Position)
	end
	PositionTorso = script.Parent.Torso.Position
end
hey copy everything on top
