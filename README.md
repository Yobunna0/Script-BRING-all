# Script-BRING-all
Créditos totalmente para Yobunna0 e mim_pipoca.
-- Remote Item Collector Hub v1.0
-- Script by Yobunna0
-- Credits: Yobunna0

-- Services
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

-- Player
local player = Players.LocalPlayer
local mouse = player:GetMouse()

-- GUI Creation
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ItemCollectorHub"
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = player:WaitForChild("PlayerGui")

-- Main Frame
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 350, 0, 450)
MainFrame.Position = UDim2.new(0.5, -175, 0.5, -225)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
MainFrame.BackgroundTransparency = 0.1
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Parent = ScreenGui

-- Corner Radius
local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 8)
UICorner.Parent = MainFrame

-- Top Bar
local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(1, 0, 0, 40)
TopBar.BackgroundColor3 = Color3.fromRGB(45, 45, 60)
TopBar.BorderSizePixel = 0
TopBar.Parent = MainFrame

local TopBarCorner = Instance.new("UICorner")
TopBarCorner.CornerRadius = UDim.new(0, 8)
TopBarCorner.Parent = TopBar

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(1, -40, 1, 0)
Title.Position = UDim2.new(0, 10, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "ITEM COLLECTOR HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 16
Title.Parent = TopBar

local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 0, 30)
CloseButton.Position = UDim2.new(1, -35, 0.5, -15)
CloseButton.BackgroundColor3 = Color3.fromRGB(220, 60, 60)
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.Font = Enum.Font.GothamBold
CloseButton.TextSize = 14
CloseButton.Parent = TopBar

local CloseButtonCorner = Instance.new("UICorner")
CloseButtonCorner.CornerRadius = UDim.new(0, 4)
CloseButtonCorner.Parent = CloseButton

-- Content Frame
local Content = Instance.new("Frame")
Content.Name = "Content"
Content.Size = UDim2.new(1, -20, 1, -60)
Content.Position = UDim2.new(0, 10, 0, 50)
Content.BackgroundTransparency = 1
Content.Parent = MainFrame

-- Credits Label
local CreditsLabel = Instance.new("TextLabel")
CreditsLabel.Name = "CreditsLabel"
CreditsLabel.Size = UDim2.new(1, 0, 0, 20)
CreditsLabel.Position = UDim2.new(0, 0, 1, -25)
CreditsLabel.BackgroundTransparency = 1
CreditsLabel.Text = "Created by Yobunna0"
CreditsLabel.TextColor3 = Color3.fromRGB(180, 180, 220)
CreditsLabel.Font = Enum.Font.Gotham
CreditsLabel.TextSize = 12
CreditsLabel.Parent = Content

-- Item Name Input
local ItemNameLabel = Instance.new("TextLabel")
ItemNameLabel.Name = "ItemNameLabel"
ItemNameLabel.Size = UDim2.new(1, 0, 0, 25)
ItemNameLabel.BackgroundTransparency = 1
ItemNameLabel.Text = "ITEM NAME:"
ItemNameLabel.TextColor3 = Color3.fromRGB(220, 220, 255)
ItemNameLabel.Font = Enum.Font.GothamBold
ItemNameLabel.TextSize = 14
ItemNameLabel.TextXAlignment = Enum.TextXAlignment.Left
ItemNameLabel.Parent = Content

local ItemNameBox = Instance.new("TextBox")
ItemNameBox.Name = "ItemNameBox"
ItemNameBox.Size = UDim2.new(1, 0, 0, 35)
ItemNameBox.Position = UDim2.new(0, 0, 0, 30)
ItemNameBox.BackgroundColor3 = Color3.fromRGB(50, 50, 65)
ItemNameBox.TextColor3 = Color3.fromRGB(255, 255, 255)
ItemNameBox.Font = Enum.Font.Gotham
ItemNameBox.PlaceholderText = "Enter item name here..."
ItemNameBox.Text = ""
ItemNameBox.TextSize = 14
ItemNameBox.Parent = Content

local ItemNameBoxCorner = Instance.new("UICorner")
ItemNameBoxCorner.CornerRadius = UDim.new(0, 6)
ItemNameBoxCorner.Parent = ItemNameBox

local ItemNameBoxPadding = Instance.new("UIPadding")
ItemNameBoxPadding.PaddingLeft = UDim.new(0, 10)
ItemNameBoxPadding.PaddingRight = UDim.new(0, 10)
ItemNameBoxPadding.Parent = ItemNameBox

-- Collect Once Button
local CollectOnceButton = Instance.new("TextButton")
CollectOnceButton.Name = "CollectOnceButton"
CollectOnceButton.Size = UDim2.new(1, 0, 0, 45)
CollectOnceButton.Position = UDim2.new(0, 0, 0, 85)
CollectOnceButton.BackgroundColor3 = Color3.fromRGB(70, 130, 200)
CollectOnceButton.Text = "COLLECT ITEMS ONCE"
CollectOnceButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CollectOnceButton.Font = Enum.Font.GothamBold
CollectOnceButton.TextSize = 16
CollectOnceButton.Parent = Content

local CollectOnceButtonCorner = Instance.new("UICorner")
CollectOnceButtonCorner.CornerRadius = UDim.new(0, 8)
CollectOnceButtonCorner.Parent = CollectOnceButton

-- Toggle Auto Collect
local AutoCollectLabel = Instance.new("TextLabel")
AutoCollectLabel.Name = "AutoCollectLabel"
AutoCollectLabel.Size = UDim2.new(1, 0, 0, 25)
AutoCollectLabel.Position = UDim2.new(0, 0, 0, 145)
AutoCollectLabel.BackgroundTransparency = 1
AutoCollectLabel.Text = "AUTO COLLECT:"
AutoCollectLabel.TextColor3 = Color3.fromRGB(220, 220, 255)
AutoCollectLabel.Font = Enum.Font.GothamBold
AutoCollectLabel.TextSize = 14
AutoCollectLabel.TextXAlignment = Enum.TextXAlignment.Left
AutoCollectLabel.Parent = Content

local AutoCollectToggle = Instance.new("TextButton")
AutoCollectToggle.Name = "AutoCollectToggle"
AutoCollectToggle.Size = UDim2.new(0.5, 0, 0, 45)
AutoCollectToggle.Position = UDim2.new(0, 0, 0, 175)
AutoCollectToggle.BackgroundColor3 = Color3.fromRGB(200, 60, 60)
AutoCollectToggle.Text = "OFF"
AutoCollectToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
AutoCollectToggle.Font = Enum.Font.GothamBold
AutoCollectToggle.TextSize = 16
AutoCollectToggle.Parent = Content

local AutoCollectToggleCorner = Instance.new("UICorner")
AutoCollectToggleCorner.CornerRadius = UDim.new(0, 8)
AutoCollectToggleCorner.Parent = AutoCollectToggle

-- Status Label
local StatusLabel = Instance.new("TextLabel")
StatusLabel.Name = "StatusLabel"
StatusLabel.Size = UDim2.new(1, 0, 0, 40)
StatusLabel.Position = UDim2.new(0, 0, 1, -100)
StatusLabel.BackgroundColor3 = Color3.fromRGB(40, 40, 55)
StatusLabel.Text = "Status: Ready"
StatusLabel.TextColor3 = Color3.fromRGB(180, 220, 180)
StatusLabel.Font = Enum.Font.Gotham
StatusLabel.TextSize = 14
StatusLabel.Parent = Content

local StatusLabelCorner = Instance.new("UICorner")
StatusLabelCorner.CornerRadius = UDim.new(0, 6)
StatusLabelCorner.Parent = StatusLabel

local StatusLabelPadding = Instance.new("UIPadding")
StatusLabelPadding.PaddingLeft = UDim.new(0, 10)
StatusLabelPadding.PaddingRight = UDim.new(0, 10)
StatusLabelPadding.Parent = StatusLabel

-- Log Output
local LogLabel = Instance.new("TextLabel")
LogLabel.Name = "LogLabel"
LogLabel.Size = UDim2.new(1, 0, 0, 25)
LogLabel.Position = UDim2.new(0, 0, 0, 235)
LogLabel.BackgroundTransparency = 1
LogLabel.Text = "LOG:"
LogLabel.TextColor3 = Color3.fromRGB(220, 220, 255)
LogLabel.Font = Enum.Font.GothamBold
LogLabel.TextSize = 14
LogLabel.TextXAlignment = Enum.TextXAlignment.Left
LogLabel.Parent = Content

local LogBox = Instance.new("ScrollingFrame")
LogBox.Name = "LogBox"
LogBox.Size = UDim2.new(1, 0, 0, 120)
LogBox.Position = UDim2.new(0, 0, 0, 265)
LogBox.BackgroundColor3 = Color3.fromRGB(40, 40, 55)
LogBox.BorderSizePixel = 0
LogBox.ScrollBarThickness = 6
LogBox.Parent = Content

local LogBoxCorner = Instance.new("UICorner")
LogBoxCorner.CornerRadius = UDim.new(0, 6)
LogBoxCorner.Parent = LogBox

local LogLayout = Instance.new("UIListLayout")
LogLayout.Parent = LogBox

local LogPadding = Instance.new("UIPadding")
LogPadding.PaddingTop = UDim.new(0, 5)
LogPadding.PaddingLeft = UDim.new(0, 10)
LogPadding.PaddingRight = UDim.new(0, 10)
LogPadding.Parent = LogBox

-- Variables
local autoCollectEnabled = false
local autoCollectConnection = nil
local itemsCollected = 0

-- Functions
local function addLog(message, color)
    color = color or Color3.fromRGB(220, 220, 220)
    
    local logEntry = Instance.new("TextLabel")
    logEntry.Size = UDim2.new(1, 0, 0, 20)
    logEntry.BackgroundTransparency = 1
    logEntry.Text = "> " .. message
    logEntry.TextColor3 = color
    logEntry.Font = Enum.Font.Gotham
    logEntry.TextSize = 12
    logEntry.TextXAlignment = Enum.TextXAlignment.Left
    logEntry.Parent = LogBox
    
    -- Auto-scroll to bottom
    LogBox.CanvasPosition = Vector2.new(0, LogBox.CanvasPosition.Y + 25)
end

local function updateStatus(message, isError)
    StatusLabel.Text = "Status: " .. message
    if isError then
        StatusLabel.TextColor3 = Color3.fromRGB(220, 180, 180)
    else
        StatusLabel.TextColor3 = Color3.fromRGB(180, 220, 180)
    end
end

local function findItemsByName(itemName)
    local items = {}
    
    -- Search in workspace
    for _, item in pairs(workspace:GetDescendants()) do
        if item:IsA("BasePart") or item:IsA("Model") then
            if item.Name:lower():find(itemName:lower()) then
                table.insert(items, item)
            end
        end
    end
    
    return items
end

local function bringItemToPlayer(item)
    local character = player.Character
    if not character then return false end
    
    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
    if not humanoidRootPart then return false end
    
    local itemPosition
    local itemInstance
    
    if item:IsA("BasePart") then
        itemPosition = item.Position
        itemInstance = item
    elseif item:IsA("Model") and item.PrimaryPart then
        itemPosition = item.PrimaryPart.Position
        itemInstance = item.PrimaryPart
    else
        return false
    end
    
    -- Move item to player's center
    local targetPosition = humanoidRootPart.Position
    
    -- Use CFrame to move the item
    if itemInstance then
        itemInstance.CFrame = CFrame.new(targetPosition)
        return true
    end
    
    return false
end

local function collectItemsOnce()
    local itemName = ItemNameBox.Text
    if itemName == "" then
        updateStatus("Please enter an item name", true)
        addLog("Error: No item name entered", Color3.fromRGB(220, 120, 120))
        return
    end
    
    updateStatus("Searching for items...", false)
    addLog("Searching for items named: " .. itemName, Color3.fromRGB(180, 180, 220))
    
    local items = findItemsByName(itemName)
    
    if #items == 0 then
        updateStatus("No items found", true)
        addLog("No items found with name: " .. itemName, Color3.fromRGB(220, 120, 120))
        return
    end
    
    updateStatus("Bringing " .. #items .. " items...", false)
    
    local successful = 0
    for _, item in pairs(items) do
        if bringItemToPlayer(item) then
            successful = successful + 1
            itemsCollected = itemsCollected + 1
        end
    end
    
    updateStatus("Collected " .. successful .. "/" .. #items .. " items", false)
    addLog("Successfully collected " .. successful .. " items", Color3.fromRGB(180, 220, 180))
end

local function toggleAutoCollect()
    autoCollectEnabled = not autoCollectEnabled
    
    if autoCollectEnabled then
        AutoCollectToggle.BackgroundColor3 = Color3.fromRGB(60, 200, 60)
        AutoCollectToggle.Text = "ON"
        updateStatus("Auto collect enabled", false)
        addLog("Auto collect enabled", Color3.fromRGB(180, 220, 180))
        
        -- Start auto-collect loop
        autoCollectConnection = RunService.Heartbeat:Connect(function()
            local itemName = ItemNameBox.Text
            if itemName ~= "" then
                local items = findItemsByName(itemName)
                for _, item in pairs(items) do
                    bringItemToPlayer(item)
                end
            end
        end)
    else
        AutoCollectToggle.BackgroundColor3 = Color3.fromRGB(200, 60, 60)
        AutoCollectToggle.Text = "OFF"
        updateStatus("Auto collect disabled", false)
        addLog("Auto collect disabled", Color3.fromRGB(220, 180, 180))
        
        -- Stop auto-collect loop
        if autoCollectConnection then
            autoCollectConnection:Disconnect()
            autoCollectConnection = nil
        end
    end
end

-- Button Events
CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

CollectOnceButton.MouseButton1Click:Connect(function()
    collectItemsOnce()
end)

AutoCollectToggle.MouseButton1Click:Connect(function()
    toggleAutoCollect()
end)

-- Button hover effects
local function setupButtonHover(button)
    local originalColor = button.BackgroundColor3
    
    button.MouseEnter:Connect(function()
        button.BackgroundColor3 = originalColor * 1.2
    end)
    
    button.MouseLeave:Connect(function()
        button.BackgroundColor3 = originalColor
    end)
    
    button.MouseButton1Down:Connect(function()
        button.BackgroundColor3 = originalColor * 0.8
    end)
    
    button.MouseButton1Up:Connect(function()
        button.BackgroundColor3 = originalColor * 1.2
    end)
end

setupButtonHover(CollectOnceButton)
setupButtonHover(AutoCollectToggle)
setupButtonHover(CloseButton)

-- Initial log messages
addLog("Item Collector Hub loaded", Color3.fromRGB(180, 220, 220))
addLog("Created by Yobunna0", Color3.fromRGB(180, 180, 220))
addLog("Enter item name and click COLLECT", Color3.fromRGB(220, 220, 180))

-- Make sure GUI is on top
ScreenGui.DisplayOrder = 999
