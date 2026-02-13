-- PAINEL SIMPLES FUNCIONAL
-- Uso educacional / jogo próprio
-- GitHub Ready

local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- CONFIG
local SENHA = "key321789"

-- GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PainelGUI"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = player:WaitForChild("PlayerGui")

-- TELA DE LOGIN
local LoginFrame = Instance.new("Frame", ScreenGui)
LoginFrame.Size = UDim2.new(0,300,0,180)
LoginFrame.Position = UDim2.new(0.5,-150,0.5,-90)
LoginFrame.BackgroundColor3 = Color3.fromRGB(20,20,20)
LoginFrame.Active = true
LoginFrame.Draggable = true

local Title = Instance.new("TextLabel", LoginFrame)
Title.Size = UDim2.new(1,0,0,40)
Title.Text = "LOGIN"
Title.TextColor3 = Color3.new(1,1,1)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 22

local TextBox = Instance.new("TextBox", LoginFrame)
TextBox.Size = UDim2.new(0,240,0,35)
TextBox.Position = UDim2.new(0.5,-120,0,60)
TextBox.PlaceholderText = "Digite a senha"
TextBox.Text = ""
TextBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
TextBox.TextColor3 = Color3.new(1,1,1)
TextBox.ClearTextOnFocus = false

local LoginButton = Instance.new("TextButton", LoginFrame)
LoginButton.Size = UDim2.new(0,240,0,35)
LoginButton.Position = UDim2.new(0.5,-120,0,110)
LoginButton.Text = "ENTRAR"
LoginButton.BackgroundColor3 = Color3.fromRGB(70,70,70)
LoginButton.TextColor3 = Color3.new(1,1,1)

-- PAINEL PRINCIPAL
local Panel = Instance.new("Frame", ScreenGui)
Panel.Size = UDim2.new(0,350,0,250)
Panel.Position = UDim2.new(0.5,-175,0.5,-125)
Panel.BackgroundColor3 = Color3.fromRGB(25,25,25)
Panel.Visible = false
Panel.Active = true
Panel.Draggable = true

local PanelTitle = Instance.new("TextLabel", Panel)
PanelTitle.Size = UDim2.new(1,0,0,40)
PanelTitle.Text = "PAINEL FUNCIONAL"
PanelTitle.TextColor3 = Color3.new(1,1,1)
PanelTitle.BackgroundTransparency = 1
PanelTitle.Font = Enum.Font.SourceSansBold
PanelTitle.TextSize = 22

-- BOTÃO SPEED
local SpeedBtn = Instance.new("TextButton", Panel)
SpeedBtn.Size = UDim2.new(0,280,0,40)
SpeedBtn.Position = UDim2.new(0.5,-140,0,60)
SpeedBtn.Text = "SPEED ON / OFF"
SpeedBtn.BackgroundColor3 = Color3.fromRGB(60,60,60)
SpeedBtn.TextColor3 = Color3.new(1,1,1)

-- BOTÃO PULO
local JumpBtn = Instance.new("TextButton", Panel)
JumpBtn.Size = UDim2.new(0,280,0,40)
JumpBtn.Position = UDim2.new(0.5,-140,0,110)
JumpBtn.Text = "PULO ALTO"
JumpBtn.BackgroundColor3 = Color3.fromRGB(60,60,60)
JumpBtn.TextColor3 = Color3.new(1,1,1)

-- BOTÃO FECHAR
local CloseBtn = Instance.new("TextButton", Panel)
CloseBtn.Size = UDim2.new(0,280,0,40)
CloseBtn.Position = UDim2.new(0.5,-140,0,160)
CloseBtn.Text = "FECHAR"
CloseBtn.BackgroundColor3 = Color3.fromRGB(120,50,50)
CloseBtn.TextColor3 = Color3.new(1,1,1)

-- FUNÇÕES
local speedOn = false

local function getHumanoid()
	local char = player.Character or player.CharacterAdded:Wait()
	return char:WaitForChild("Humanoid")
end

SpeedBtn.MouseButton1Click:Connect(function()
	local hum = getHumanoid()
	speedOn = not speedOn
	hum.WalkSpeed = speedOn and 50 or 16
end)

JumpBtn.MouseButton1Click:Connect(function()
	local hum = getHumanoid()
	hum.JumpPower = 100
end)

CloseBtn.MouseButton1Click:Connect(function()
	Panel.Visible = false
	LoginFrame.Visible = true
end)

LoginButton.MouseButton1Click:Connect(function()
	if TextBox.Text == SENHA then
		LoginFrame.Visible = false
		Panel.Visible = true
	else
		TextBox.Text = ""
		TextBox.PlaceholderText = "Senha incorreta"
	end
end)
