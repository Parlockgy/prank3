local Lighting = game:GetService("Lighting")
local PlayerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

-- Criar GUI
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
local Frame = Instance.new("Frame", ScreenGui)
local TextButton = Instance.new("TextButton", Frame)

Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Size = UDim2.new(0, 150, 0, 50)
Frame.Position = UDim2.new(0.5, -75, 0.8, -25)

TextButton.Size = UDim2.new(1, 0, 1, 0)
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "ChangeSky"
TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
TextButton.TextSize = 14

-- Função para remover o céu existente
local function RemoveSky()
    for _, obj in pairs(Lighting:GetChildren()) do
        if obj:IsA("Sky") then
            obj:Destroy()
        end
    end
end

-- Criar novo céu
local function ChangeSky()
    RemoveSky()
    
    local newSky = Instance.new("Sky", Lighting)
    newSky.Name = "Teste"
    
    -- IDs do Skybox
    local assetId = "rbxassetid://117040568125131"
    newSky.SkyboxBk = assetId
    newSky.SkyboxDn = assetId
    newSky.SkyboxFt = assetId
    newSky.SkyboxLf = assetId
    newSky.SkyboxRt = assetId
    newSky.SkyboxUp = assetId
    newSky.SunTextureId = "0"
end

-- Conectar botão
TextButton.MouseButton1Click:Connect(ChangeSky)
