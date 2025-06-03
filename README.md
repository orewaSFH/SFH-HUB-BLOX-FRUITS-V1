
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.Name = "SFHhub"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 600, 0, 350)
frame.Position = UDim2.new(0.5, -300, 0.5, -175)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.Active = true
frame.Draggable = true

local topBar = Instance.new("Frame", frame)
topBar.Size = UDim2.new(1, 0, 0, 30)
topBar.BackgroundColor3 = Color3.fromRGB(25, 25, 25)

local title = Instance.new("TextLabel", topBar)
title.Size = UDim2.new(1, -60, 1, 0)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "SFHhub"
title.TextColor3 = Color3.new(1, 1, 1)
title.TextXAlignment = Enum.TextXAlignment.Left
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local closeBtn = Instance.new("TextButton", topBar)
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -30, 0, 0)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.new(1, 0, 0)
closeBtn.BackgroundColor3 = Color3.fromRGB(40, 0, 0)
closeBtn.MouseButton1Click:Connect(function()
	gui:Destroy()
end)

local minBtn = Instance.new("TextButton", topBar)
minBtn.Size = UDim2.new(0, 30, 0, 30)
minBtn.Position = UDim2.new(1, -60, 0, 0)
minBtn.Text = "-"
minBtn.TextColor3 = Color3.new(1, 1, 0)
minBtn.BackgroundColor3 = Color3.fromRGB(40, 40, 0)

local content = Instance.new("Frame", frame)
content.Size = UDim2.new(1, 0, 1, -30)
content.Position = UDim2.new(0, 0, 0, 30)
content.BackgroundColor3 = Color3.fromRGB(35, 35, 35)

minBtn.MouseButton1Click:Connect(function()
	content.Visible = not content.Visible
end)

local tabBar = Instance.new("Frame", content)
tabBar.Size = UDim2.new(0, 100, 1, 0)
tabBar.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

local tabContent = Instance.new("Frame", content)
tabContent.Size = UDim2.new(1, -100, 1, 0)
tabContent.Position = UDim2.new(0, 100, 0, 0)
tabContent.BackgroundColor3 = Color3.fromRGB(40, 40, 40)

local tabs = {}
local function createTab(name)
	local btn = Instance.new("TextButton", tabBar)
	btn.Size = UDim2.new(1, 0, 0, 30)
	btn.Text = name
	btn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	btn.TextColor3 = Color3.new(1, 1, 1)

	local page = Instance.new("Frame", tabContent)
	page.Size = UDim2.new(1, 0, 1, 0)
	page.BackgroundTransparency = 1
	page.Visible = false

	btn.MouseButton1Click:Connect(function()
		for _, v in pairs(tabContent:GetChildren()) do v.Visible = false end
		page.Visible = true
	end)

	tabs[name] = page
	return page
end

local function createButton(parent, text, callback)
	local btn = Instance.new("TextButton", parent)
	btn.Size = UDim2.new(0, 200, 0, 30)
	btn.Position = UDim2.new(0, 10, 0, #parent:GetChildren() * 35)
	btn.Text = text
	btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	btn.TextColor3 = Color3.new(1, 1, 1)
	btn.MouseButton1Click:Connect(callback)
end

-- Tabs & Features
local main = createTab("Main")

createButton(main, "Auto Farm (Redz)", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/RedzHub/All-Scripts/main/BF%20AutoFarm"))()
end)

local race = createTab("Race")
createButton(race, "Auto V2", function()
	-- future function
end)

createButton(race, "Auto V3", function()
	-- future function
end)

createButton(race, "Auto Trial (V4)", function()
	-- future function
end)

createButton(race, "Auto Mirage", function()
	-- future function
end)

createButton(race, "Teleport to Gear", function()
	-- future function
end)

createButton(race, "Lock to Moon", function()
	-- future function
end)

-- Show default tab
tabs["Main"].Visible = true
