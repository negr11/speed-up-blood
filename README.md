local Blood_gui = Instance.new("ScreenGui")
Blood_gui.Name = "Blood_gui"
Blood_gui.Parent = game.StarterGui

local Frame = Instance.new("Frame")
Frame.Visible = false
Frame.Position = UDim2.new(0.09873834252357483, 334, 0.1548442542552948, 161)
Frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
Frame.Size = UDim2.new(0, 513, 0, 336)
Frame.BorderSizePixel = 0
Frame.BackgroundColor3 = Color3.fromRGB(22, 22, 22)
Frame.Parent = Blood_gui

local FlyButton = Instance.new("TextButton")
FlyButton.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
FlyButton.TextColor3 = Color3.fromRGB(0, 0, 0)
FlyButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
FlyButton.Text = "Fly"
FlyButton.Size = UDim2.new(0, 513, 0, 109)
FlyButton.Name = "FlyButton"
FlyButton.BorderSizePixel = 0
FlyButton.TextWrapped = true
FlyButton.TextSize = 14
FlyButton.TextScaled = true
FlyButton.BackgroundColor3 = Color3.fromRGB(130, 0, 2)
FlyButton.Parent = Frame

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 9)
UICorner.Parent = FlyButton

local LocalScript = Instance.new("LocalScript")
LocalScript.Source = "local isFlying = false
local camera workspace.CurrentCamera
local char = game.Players.LocalPlayer.Character
local hrp = char:WaitForChild("HumanoidRootPart")

local bodyPos Instance.new("BodyPosition")
bodyPos.MaxForce = Vector3.new()
bodyPos.D = 10
bodyPos.P = 100
bodyPos.Parent = hrp

local bodyGyro = Instance.new("BodyGyro")
bodyGyro.MaxTorque = Vector3.new()
bodyGyro.D = 10
bodyGyro.Parent = hrp

script.Parent.MouseButton1Click:Connect(function()
	isFlying = not isFlying
end)

script.Parent.MouseButton2Click:Conncet(function()
	isFlying = false
end)

game:GetService("RunService").RenderStepped:Connect(function()
	if isFlying then
		bodyPos.MaxForce = Vector3.new(math.huge, math.huge, math)
		bodyGyro.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
		bodyPos.Position = hrp.Position + ((hrp.Position - camera.CFrame.Position).Unit * 10)
		bodyGyro.CFrame = CFrame.new(camera.CFrame.Position, hrp.Position
	else
		bodyPos.MaxForce = Vector3.new()
		bodyGyro.MaxTorque = Vector3.new()
	end
end)
"
LocalScript.Parent = FlyButton

local BloodScriptLabel = Instance.new("TextLabel")
BloodScriptLabel.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
BloodScriptLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
BloodScriptLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
BloodScriptLabel.Text = "Blood script"
BloodScriptLabel.BorderSizePixel = 0
BloodScriptLabel.Size = UDim2.new(0, 513, 0, 148)
BloodScriptLabel.Name = "BloodScriptLabel"
BloodScriptLabel.Position = UDim2.new(0, 0, 0.324404776096344, 0)
BloodScriptLabel.TextWrapped = true
BloodScriptLabel.TextSize = 14
BloodScriptLabel.TextScaled = true
BloodScriptLabel.BackgroundColor3 = Color3.fromRGB(106, 0, 2)
BloodScriptLabel.Parent = Frame

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 9)
UICorner.Parent = BloodScriptLabel

local SpeedButton = Instance.new("TextButton")
SpeedButton.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
SpeedButton.TextColor3 = Color3.fromRGB(0, 0, 0)
SpeedButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
SpeedButton.Text = "Speed Up"
SpeedButton.BorderSizePixel = 0
SpeedButton.Size = UDim2.new(0, 513, 0, 79)
SpeedButton.Name = "SpeedButton"
SpeedButton.Position = UDim2.new(0, 0, 0.7648809552192688, 0)
SpeedButton.TextWrapped = true
SpeedButton.TextSize = 14
SpeedButton.TextScaled = true
SpeedButton.BackgroundColor3 = Color3.fromRGB(136, 0, 2)
SpeedButton.Parent = Frame

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 9)
UICorner.Parent = SpeedButton

local LocalScript = Instance.new("LocalScript")
LocalScript.Source = "local player = game.Players.LocalPlayer

player.PlayerGui.ScreenGui.Speed.MouseButton1Click:Connect(function()
	
	player.Character.Humanoid.Walkspeed *= 4
end)"
LocalScript.Parent = SpeedButton

local UIDragDetector = Instance.new("UIDragDetector")
UIDragDetector.DragUDim2 = UDim2.new(0, 94, 0, 12)
UIDragDetector.Parent = Frame

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 9)
UICorner.Parent = Frame

local OpenButton = Instance.new("TextButton")
OpenButton.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
OpenButton.TextColor3 = Color3.fromRGB(0, 0, 0)
OpenButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
OpenButton.Text = "Open"
OpenButton.BorderSizePixel = 0
OpenButton.Size = UDim2.new(0, 68, 0, 68)
OpenButton.Name = "OpenButton"
OpenButton.Position = UDim2.new(-0.09928689152002335, 332, 0.032006919384002686, -37)
OpenButton.TextWrapped = true
OpenButton.TextSize = 14
OpenButton.TextScaled = true
OpenButton.BackgroundColor3 = Color3.fromRGB(115, 0, 2)
OpenButton.Parent = Blood_gui

local LocalScript = Instance.new("LocalScript")
LocalScript.Source = "local button = script.Parent
local frame = script.Parent.Parent:WaitForChild("Frame")
local debounce = false

button.MouseButton1Up:Connect(function()

	if debounce == false then
		debounce = true

		frame.Visible = true
		script.Parent.Text = "Close gui"

	elseif debounce == true then
		debounce = false

		frame.Visible = false
		script.Parent.Text = "Open gui"

	end
end)

"
LocalScript.Parent = OpenButton

