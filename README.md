local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Script Hub | Pressure Wash Simulator", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})


--Values
_G.autoComplete = true
_G.autoRefill = true
_G.infiniteMoney = true




--Functions
function autoComplete()
	while _G.autoComplete == true do		
		local args = {[1] = 37500238418579.1,[2] = 624}
		game:GetService("ReplicatedStorage").Remotes.SurfaceCompleted:FireServer(unpack(args))
		wait()
	end
end

function autoRefill()
	while _G.autoRefill == true do
		local args = {[1] = true}
		game:GetService("ReplicatedStorage").Remotes.RefillRemote:FireServer(unpack(args))
		wait(0.1)		
	end	
end

function infiniteMoney()
	while _G.infiniteMoney == true do
		local args = {[1] = 45060753822326.66,[2] = math.huge}
		game:GetService("ReplicatedStorage").Remotes.SurfaceCompleted:FireServer(unpack(args))
		wait()	
	end	
end

--Tabs
local Clean = Window:MakeTab({
	Name = "Farm",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Misc = 
Window:MakeTab({
	Name = "Misc",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--Toggles
Clean:AddToggle({
	Name = "Auto Farm",
	Default = false,
	Callback = function(Value)
		_G.autoComplete = Value
		autoComplete()
	end    
})


Clean:AddToggle({
	Name = "Infinite Money",
	Default = false,
	Callback = function(Value)
		_G.infiniteMoney = Value
		infiniteMoney()
	end    
})





--Buttons
Clean:AddButton({
	Name = "Auto Refill!",
	Callback = function()
      		autoRefill()
  	end    
})








--Sliders
Misc:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 100,
	Default = 16,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "WalkSpeed",
	Callback = function(Value)
		game.Players.localPlayer.Character.Humanoid.WalkSpeed = Value
	end    
})












OrionLib:Init()
