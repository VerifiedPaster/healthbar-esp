-- Services
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
 
-- Function to create the health bar GUI
local function createHealthBar(player)
    -- Wait for the character to load
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
 
    -- Create BillboardGui
    local billboardGui = Instance.new("BillboardGui")
    billboardGui.Name = "HealthBar"
    billboardGui.Adornee = character:WaitForChild("Head")
    billboardGui.Size = UDim2.new(4, 0, 0.5, 0)
    billboardGui.StudsOffset = Vector3.new(0, 3, 0)
    billboardGui.AlwaysOnTop = true
    billboardGui.Parent = character.Head
 
    -- Create Background Frame
    local background = Instance.new("Frame")
    background.Size = UDim2.new(1, 0, 1, 0)
    background.BackgroundColor3 = Color3.new(0, 0, 0)
    background.BorderSizePixel = 0
    background.Parent = billboardGui
 
    -- Create Health Bar Frame
    local healthBar = Instance.new("Frame")
    healthBar.Size = UDim2.new(1, 0, 1, 0)
    healthBar.BackgroundColor3 = Color3.new(0, 1, 0)
    healthBar.BorderSizePixel = 0
    healthBar.Parent = background
 
    -- Update health bar based on humanoid health
    local function updateHealth()
        local healthPercent = humanoid.Health / humanoid.MaxHealth
        healthBar.Size = UDim2.new(healthPercent, 0, 1, 0)
        healthBar.BackgroundColor3 = Color3.fromRGB(255 * (1 - healthPercent), 255 * healthPercent, 0)
    end
 
    humanoid.HealthChanged:Connect(updateHealth)
    updateHealth()
end
 
-- Connect function to all existing players
for _, player in pairs(Players:GetPlayers()) do
    if player ~= Players.LocalPlayer then
        createHealthBar(player)
    end
end
 
-- Connect function to players joining
Players.PlayerAdded:Connect(function(player)
    if player ~= Players.LocalPlayer then
        player.CharacterAdded:Connect(function()
            createHealthBar(player)
        end)
    end
end)
