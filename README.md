if not game:IsLoaded() then game.Loaded:Wait() end

function missing(t, f, fallback)
    if type(f) == t then return f end
    return fallback
end

local queueteleport =  missing("function", queue_on_teleport or (syn and syn.queue_on_teleport) or (fluxus and fluxus.queue_on_teleport))

delay(120,function()
local TeleportService = game:GetService("TeleportService")
local Players = game.Players
PlaceId, JobId = game.PlaceId, game.JobId
	if #Players:GetPlayers() <= 1 then
		Players.LocalPlayer:Kick("\nRejoining...")
		wait()
		TeleportService:Teleport(PlaceId, Players.LocalPlayer)
	else
		TeleportService:TeleportToPlaceInstance(PlaceId, JobId, Players.LocalPlayer)
	end
end)

local TeleportCheck = false
game.Players.LocalPlayer.OnTeleport:Connect(function(State)
if TeleportCheck == true then return end
		TeleportCheck = true
    	queueteleport("loadstring(game:HttpGet('https://raw.githubusercontent.com/nguyenquang2006tin-rgb/Star-slime-farming/refs/heads/main/README.md'))()")

end)
repeat wait() until game.Players.LocalPlayer.PlayerGui:FindFirstChild("MainMenu")
repeat wait() until game.Players.LocalPlayer.PlayerGui.MainMenu.Enabled == true
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Play"):InvokeServer()
game:GetService("ReplicatedStorage"):WaitForChild("Constants"):WaitForChild("Transfer"):InvokeServer()


local chr = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
repeat wait() until chr:FindFirstChild("Humanoid")
spawn(function()
while wait() do
  chr:WaitForChild("Humanoid"):Move(Vector3.new(1,0,0))
end
end)


---------------
spawn(function()
while wait(.1) do
game:GetService("ReplicatedStorage").Remotes.Information.RemoteFunction:FireServer({true,true},"DodgeMinigame")
end
end)
---------------

_G.Farm = true

while _G.Farm == true do
wait(.5)

if game.Players.LocalPlayer.Character:FindFirstChild("FightInProgress") == nil then continue end

--pcall(function()
local enemy 

for _,v in pairs(workspace.Living:GetChildren()) do
if v:FindFirstChild("FightInProgress") and v ~= game.Players.LocalPlayer.Character then
if v.FightInProgress.Value == game.Players.LocalPlayer.Character.FightInProgress.Value and v.Name == "Star Slime" then
enemy = v 
break
end
end
end

if enemy == nil then _G.Farm = false end

repeat wait(.5) until game.Players.LocalPlayer.PlayerGui.Combat.ActionBG.Visible == true


wait(.5)
local args = {
	"Attack",
	"Strike",
	{
		Attacking = enemy
	}
}
game:GetService("ReplicatedStorage"):WaitForChild("PlayerTurnInput"):InvokeServer(unpack(args))


end



--------------------------
print("A")

local TeleportService = game:GetService("TeleportService")
local Players = game.Players
PlaceId, JobId = game.PlaceId, game.JobId

	if #Players:GetPlayers() <= 1 then
		Players.LocalPlayer:Kick("\nRejoining...")
		wait()
		TeleportService:Teleport(PlaceId, Players.LocalPlayer)
	else
		TeleportService:TeleportToPlaceInstance(PlaceId, JobId, Players.LocalPlayer)
	end
