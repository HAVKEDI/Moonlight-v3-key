-- Gui to Lua
-- Version: 3.2

-- Instances:

local MyCoortGui = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local panel = Instance.new("Frame")
local ImageLabel = Instance.new("ImageLabel")
local UICorner = Instance.new("UICorner")
local Execute = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local TextBox = Instance.new("TextBox")
local UICorner_3 = Instance.new("UICorner")
local UICorner_4 = Instance.new("UICorner")

--Properties:

MyCoortGui.Name = "MyCoortGui"
MyCoortGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Main.Name = "Main"
Main.Parent = MyCoortGui
Main.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Main.BorderColor3 = Color3.fromRGB(0, 0, 0)
Main.BorderSizePixel = 0
Main.Position = UDim2.new(0.102011494, 0, 0.278728604, 0)
Main.Size = UDim2.new(0.494971275, 0, 0.458435208, 0)

panel.Name = "panel"
panel.Parent = Main
panel.BackgroundColor3 = Color3.fromRGB(38, 38, 38)
panel.BorderColor3 = Color3.fromRGB(0, 0, 0)
panel.BorderSizePixel = 0
panel.Position = UDim2.new(-0.0131974127, 0, 1.22070318e-07, 0)
panel.Size = UDim2.new(1.01319742, 0, 0.999999762, 0)

ImageLabel.Parent = panel
ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
ImageLabel.Size = UDim2.new(0.0808926001, 0, 0.112798266, 0)
ImageLabel.Image = "rbxassetid://89525716302778"

UICorner.Parent = panel

Execute.Name = "Execute"
Execute.Parent = panel
Execute.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
Execute.BorderColor3 = Color3.fromRGB(0, 0, 0)
Execute.BorderSizePixel = 0
Execute.Position = UDim2.new(0.721059978, 0, 0.89154011, 0)
Execute.Size = UDim2.new(0.278939992, 0, 0.108459868, 0)
Execute.Font = Enum.Font.SourceSansBold
Execute.Text = "Execute"
Execute.TextColor3 = Color3.fromRGB(0, 0, 0)
Execute.TextScaled = true
Execute.TextSize = 14.000
Execute.TextWrapped = true

UICorner_2.Parent = Execute

TextBox.Parent = panel
TextBox.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
TextBox.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.0348675027, 0, 0.136659443, 0)
TextBox.Size = UDim2.new(0.938633025, 0, 0.670282006, 0)
TextBox.Font = Enum.Font.SourceSansBold
TextBox.PlaceholderColor3 = Color3.fromRGB(0, 0, 0)
TextBox.PlaceholderText = "print(\"Hello world!\")"
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(0, 0, 0)
TextBox.TextSize = 14.000
TextBox.TextWrapped = true

UICorner_3.Parent = TextBox

UICorner_4.Parent = Main

-- Scripts:

local function LWDGR_fake_script() -- Execute.LocalScript 
	local script = Instance.new('LocalScript', Execute)

	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Parent.ExecuteEvent:FireServer(script.Parent.Parent.TextBox.Text)
		end)
end
coroutine.wrap(LWDGR_fake_script)()
local function UXMV_fake_script() -- Main.Smooth GUI Dragging 
	local script = Instance.new('LocalScript', Main)

	local UserInputService = game:GetService("UserInputService")
	local runService = (game:GetService("RunService"));
	
	local gui = script.Parent
	
	local dragging
	local dragInput
	local dragStart
	local startPos
	
	function Lerp(a, b, m)
	    return a + (b - a) * m
	end;
	
	local lastMousePos
	local lastGoalPos
	local DRAG_SPEED = (8); -- // The speed of the UI darg.
	function Update(dt)
	    if not (startPos) then return end;
	    if not (dragging) and (lastGoalPos) then
	        gui.Position = UDim2.new(startPos.X.Scale, Lerp(gui.Position.X.Offset, lastGoalPos.X.Offset, dt * DRAG_SPEED), startPos.Y.Scale, Lerp(gui.Position.Y.Offset, lastGoalPos.Y.Offset, dt * DRAG_SPEED))
	        return 
	    end;
	
	    local delta = (lastMousePos - UserInputService:GetMouseLocation())
	    local xGoal = (startPos.X.Offset - delta.X);
	    local yGoal = (startPos.Y.Offset - delta.Y);
	    lastGoalPos = UDim2.new(startPos.X.Scale, xGoal, startPos.Y.Scale, yGoal)
	    gui.Position = UDim2.new(startPos.X.Scale, Lerp(gui.Position.X.Offset, xGoal, dt * DRAG_SPEED), startPos.Y.Scale, Lerp(gui.Position.Y.Offset, yGoal, dt * DRAG_SPEED))
	end;
	
	gui.InputBegan:Connect(function(input)
	    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
	        dragging = true
	        dragStart = input.Position
	        startPos = gui.Position
	        lastMousePos = UserInputService:GetMouseLocation()
	
	        input.Changed:Connect(function()
	            if input.UserInputState == Enum.UserInputState.End then
	                dragging = false
	            end
	        end)
	    end
	end)
	
	gui.InputChanged:Connect(function(input)
	    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
	        dragInput = input
	    end
	end)
	
	runService.Heartbeat:Connect(Update)
end
coroutine.wrap(UXMV_fake_script)()
local function TVZU_fake_script() -- MyCoortGui.LocalScript 
	local script = Instance.new('LocalScript', MyCoortGui)

	
	local Frame = script.Parent.Parent
	
	script.Parent.MouseButton1Click:Connect(function()
		Frame.Visible = true
	end)
end
coroutine.wrap(TVZU_fake_script)()
