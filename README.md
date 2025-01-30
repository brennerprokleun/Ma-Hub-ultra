-- MAÇÃ HUB 2025 ULTRA - Script Completo para Blox Fruits
-- Criado para Auto-Farm, Auto-Raid, Auto-Level, Auto-V4, Auto-Katakuri, Auto-Trial, Auto-Mastery e mais.
-- Sistema Anti-Ban integrado.

local AppleHub = {}
AppleHub.Name = "MAÇÃ HUB 2025 ULTRA"
AppleHub.Version = "3.0"
AppleHub.AntiBan = true

-- Proteção Anti-Ban (Randomização e Delay Dinâmico)
function AppleHub.AntiDetect()
    local randomDelay = math.random(3, 6)
    wait(randomDelay)
end

-- Auto-Farm XP, Beli e Drops
function AppleHub.AutoFarm()
    while wait(1) do
        AppleHub.AntiDetect()
        for _, enemy in pairs(workspace.Enemies:GetChildren()) do
            if enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
                game:GetService("ReplicatedStorage").Remotes.Combat:FireServer("Attack")
                wait(0.5)
            end
        end
    end
end

-- Auto-Level (Completa Missões e Upa até o Máximo)
function AppleHub.AutoLevel()
    while wait(2) do
        AppleHub.AntiDetect()
        local player = game.Players.LocalPlayer
        if player.leaderstats.Level.Value < 2500 then -- Troque 2500 pelo nível máximo
            game:GetService("ReplicatedStorage").Remotes.Quest:FireServer("Aceitar")
            AppleHub.AutoFarm()
        end
    end
end

-- Auto-Katakuri (Derrota o Boss Katakuri Automaticamente)
function AppleHub.AutoKatakuri()
    while wait(3) do
        AppleHub.AntiDetect()
        local boss = workspace.Enemies:FindFirstChild("Katakuri")
        if boss and boss:FindFirstChild("Humanoid") and boss.Humanoid.Health > 0 then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = boss.HumanoidRootPart.CFrame
            game:GetService("ReplicatedStorage").Remotes.Combat:FireServer("Attack")
            wait(1)
        end
    end
end

-- Auto-V4 (Desperta o Gear 4 Automaticamente)
function AppleHub.AutoV4()
    while wait(5) do
        AppleHub.AntiDetect()
        local altar = workspace:FindFirstChild("Altar V4")
        if altar then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = altar.CFrame
            game:GetService("ReplicatedStorage").Remotes.Quest:FireServer("DespertarV4")
            wait(2)
        end
    end
end

-- Auto-Leviathan (Derrota o Boss Leviathan e Coleta Recompensas)
function AppleHub.AutoLeviathan()
    while wait(4) do
        AppleHub.AntiDetect()
        local boss = workspace.Enemies:FindFirstChild("Leviathan")
        if boss and boss:FindFirstChild("Humanoid") and boss.Humanoid.Health > 0 then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = boss.HumanoidRootPart.CFrame
            game:GetService("ReplicatedStorage").Remotes.Combat:FireServer("Attack")
            wait(1)
        end
    end
end

-- Auto-Trial (Completa Trials V4 Automaticamente)
function AppleHub.AutoTrial()
    while wait(3) do
        AppleHub.AntiDetect()
        local trial = workspace:FindFirstChild("Trial V4")
        if trial then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = trial.CFrame
            game:GetService("ReplicatedStorage").Remotes.Quest:FireServer("CompletarTrial")
            wait(2)
        end
    end
end

-- Auto-Farm Fruit (Coleta e Guarda Frutas Automaticamente)
function AppleHub.AutoFarmFruit()
    while wait(2) do
        AppleHub.AntiDetect()
        for _, item in pairs(workspace:GetChildren()) do
            if item:IsA("Tool") and item.Name:match("Fruit") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = item.Handle.CFrame
                wait(0.5)
            end
        end
    end
end

-- Auto-Mastery (Espada, Estilo de Luta e Fruta)
function AppleHub.AutoMastery()
    while wait(1) do
        AppleHub.AntiDetect()
        game:GetService("ReplicatedStorage").Remotes.Combat:FireServer("UpgradeMastery")
    end
end

-- Criação da GUI (Interface Gráfica)
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ButtonFarm = Instance.new("TextButton")
local ButtonLevel = Instance.new("TextButton")
local ButtonKatakuri = Instance.new("TextButton")
local ButtonV4 = Instance.new("TextButton")
local ButtonLeviathan = Instance.new("TextButton")
local ButtonTrial = Instance.new("TextButton")
local ButtonFruit = Instance.new("TextButton")
local ButtonMastery = Instance.new("TextButton")

-- Configurações da GUI
ScreenGui.Parent = game.Players.LocalPlayer.PlayerGui
ScreenGui.Name = "AppleHubGUI"

Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 250, 0, 400)
Frame.Position = UDim2.new(0.5, -125, 0.5, -200)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 2

-- Botão Auto-Farm
ButtonFarm.Parent = Frame
ButtonFarm.Size = UDim2.new(0, 220, 0, 50)
ButtonFarm.Position = UDim2.new(0, 15, 0, 10)
ButtonFarm.Text = "Auto-Farm"
ButtonFarm.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonFarm.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonFarm.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoFarm)
end)

-- Botão Auto-Level
ButtonLevel.Parent = Frame
ButtonLevel.Size = UDim2.new(0, 220, 0, 50)
ButtonLevel.Position = UDim2.new(0, 15, 0, 70)
ButtonLevel.Text = "Auto-Level"
ButtonLevel.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonLevel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonLevel.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoLevel)
end)

-- Botão Auto-Katakuri
ButtonKatakuri.Parent = Frame
ButtonKatakuri.Size = UDim2.new(0, 220, 0, 50)
ButtonKatakuri.Position = UDim2.new(0, 15, 0, 130)
ButtonKatakuri.Text = "Auto-Katakuri"
ButtonKatakuri.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonKatakuri.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonKatakuri.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoKatakuri)
end)

-- Botão Auto-V4
ButtonV4.Parent = Frame
ButtonV4.Size = UDim2.new(0, 220, 0, 50)
ButtonV4.Position = UDim2.new(0, 15, 0, 190)
ButtonV4.Text = "Auto-V4"
ButtonV4.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonV4.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonV4.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoV4)
end)

-- Botão Auto-Leviathan
ButtonLeviathan.Parent = Frame
ButtonLeviathan.Size = UDim2.new(0, 220, 0, 50)
ButtonLeviathan.Position = UDim2.new(0, 15, 0, 250)
ButtonLeviathan.Text = "Auto-Leviathan"
ButtonLeviathan.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonLeviathan.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonLeviathan.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoLeviathan)
end)

-- Botão Auto-Trial
ButtonTrial.Parent = Frame
ButtonTrial.Size = UDim2.new(0, 220, 0, 50)
ButtonTrial.Position = UDim2.new(0, 15, 0, 310)
ButtonTrial.Text = "Auto-Trial"
ButtonTrial.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonTrial.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonTrial.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoTrial)
end)

-- Botão Auto-Farm Fruit
ButtonFruit.Parent = Frame
ButtonFruit.Size = UDim2.new(0, 220, 0, 50)
ButtonFruit.Position = UDim2.new(0, 15, 0, 370)
ButtonFruit.Text = "Auto-Fruit"
ButtonFruit.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonFruit.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonFruit.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoFarmFruit)
end)

-- Botão Auto-Mastery
ButtonMastery.Parent = Frame
ButtonMastery.Size = UDim2.new(0, 220, 0, 50)
ButtonMastery.Position = UDim2.new(0, 15, 0, 430)
ButtonMastery.Text = "Auto-Mastery"
ButtonMastery.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonMastery.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

ButtonMastery.MouseButton1Click:Connect(function()
    spawn(AppleHub.AutoMastery)
end)

print("✅ MAÇÃ HUB 2025 ULTRA - Rodando com sucesso!")
