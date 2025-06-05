-- GUI: Interface básica
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local Button = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.Name = "CopySkinGui"

Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0, 300, 0, 150)
Frame.Position = UDim2.new(0.5, -150, 0.5, -75)
Frame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
Frame.BorderSizePixel = 0

TextBox.Parent = Frame
TextBox.PlaceholderText = "Nome do jogador"
TextBox.Size = UDim2.new(1, -20, 0, 40)
TextBox.Position = UDim2.new(0, 10, 0, 10)
TextBox.BackgroundColor3 = Color3.new(1, 1, 1)
TextBox.TextColor3 = Color3.new(0, 0, 0)

Button.Parent = Frame
Button.Text = "Copiar Skin"
Button.Size = UDim2.new(1, -20, 0, 40)
Button.Position = UDim2.new(0, 10, 0, 60)
Button.BackgroundColor3 = Color3.new(0.2, 0.6, 0.2)
Button.TextColor3 = Color3.new(1, 1, 1)

-- Função copiar skin
Button.MouseButton1Click:Connect(function()
    local targetName = TextBox.Text
    local target = game.Players:FindFirstChild(targetName)
    local player = game.Players.LocalPlayer

    if target and target.Character and player.Character then
        local targetHumanoid = target.Character:FindFirstChildOfClass("Humanoid")
        local playerHumanoid = player.Character:FindFirstChildOfClass("Humanoid")

        if targetHumanoid and playerHumanoid then
            playerHumanoid:ApplyDescription(targetHumanoid:GetAppliedDescription())
        else
            warn("Humanoid não encontrado.")
        end
    else
        warn("Jogador ou personagem inválido.")
    end
end)
