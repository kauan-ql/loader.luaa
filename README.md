-- Dark Hub | Painel Mobile
-- Feito para Delta / Mobile

local player = game.Players.LocalPlayer

-- Evitar duplicar GUI
if player.PlayerGui:FindFirstChild("DarkHub") then
    player.PlayerGui.DarkHub:Destroy()
end

-- ScreenGui
local gui = Instance.new("ScreenGui")
gui.Name = "DarkHub"
gui.Parent = player.PlayerGui
gui.ResetOnSpawn = false

-- Botão flutuante (toggle)
local toggle = Instance.new("TextButton")
toggle.Parent = gui
toggle.Size = UDim2.new(0,50,0,50)
toggle.Position = UDim2.new(0.85,0,0.6,0)
toggle.Text = "≡"
toggle.Font = Enum.Font.GothamBold
toggle.TextSize = 22
toggle.TextColor3 = Color3.fromRGB(255,255,255)
toggle.BackgroundColor3 = Color3.fromRGB(20,20,20)
toggle.BorderSizePixel = 0
toggle.Active = true
toggle.Draggable = true
Instance.new("UICorner", toggle).CornerRadius = UDim.new(1,0)

-- Painel principal
local frame = Instance.new("Frame")
frame.Parent = gui
frame.Size = UDim2.new(0,240,0,220)
frame.Position = UDim2.new(0.5,-120,0.5,-110)
frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
frame.BorderSizePixel = 0
frame.Visible = false
frame.Active = true
frame.Draggable = true
Instance.new("UICorner", frame).CornerRadius = UDim.new(0,12)

-- Título
local title = Instance.new("TextLabel")
title.Parent = frame
title.Size = UDim2.new(1,0,0,35)
title.BackgroundTransparency = 1
title.Text = "Dark Hub | Mobile"
title.Font = Enum.Font.GothamBold
title.TextSize = 14
title.TextColor3 = Color3.fromRGB(255,255,255)

-- Layout
local layout = Instance.new("UIListLayout")
layout.Parent = frame
layout.Padding = UDim.new(0,10)
layout.HorizontalAlignment = Enum.HorizontalAlignment.Center

-- Função criar botão
local function criarBotao(texto, callback)
    local btn = Instance.new("TextButton")
    btn.Parent = frame
    btn.Size = UDim2.new(1,-20,0,42)
    btn.Text = texto
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 14
    btn.TextColor3 = Color3.fromRGB(255,255,255)
    btn.BackgroundColor3 = Color3.fromRGB(45,45,45)
    btn.BorderSizePixel = 0
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0,8)
    btn.MouseButton1Click:Connect(callback)
end

-- BOTÕES (você pode trocar depois pelos seus scripts)
criarBotao("Infinite Yield", function()
    print("Infinite Yield clicado")
    -- loadstring(game:HttpGet("LINK_RAW_DO_IY"))()
end)

criarBotao("Fly", function()
    print("Fly clicado")
    -- loadstring(game:HttpGet("LINK_RAW_DO_FLY"))()
end)

criarBotao("Meu Script", function()
    print("Meu script clicado")
    -- loadstring(game:HttpGet("LINK_DO_SEU_SCRIPT"))()
end)

-- Toggle abrir / fechar
toggle.MouseButton1Click:Connect(function()
    frame.Visible = not frame.Visible
end)

print("Dark Hub carregado com sucesso!")
