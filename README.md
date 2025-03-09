local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UICornerFrame = Instance.new("UICorner")
local UIStrokeFrame = Instance.new("UIStroke")
local Title = Instance.new("TextLabel")
local UICornerTitle = Instance.new("UICorner")
local Button = Instance.new("TextButton")
local UICornerButton = Instance.new("UICorner")
local Message = Instance.new("TextLabel")
local running = false
local loopConnection

-- Propriedades da ScreenGui
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Propriedades da Frame
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Frame.Position = UDim2.new(0.5, -100, 0.5, -150)
Frame.Size = UDim2.new(0, 200, 0, 150)
Frame.Active = true
Frame.Draggable = true

-- Adicionando cantos arredondados e borda à Frame
UICornerFrame.CornerRadius = UDim.new(0, 50)
UICornerFrame.Parent = Frame

UIStrokeFrame.Color = Color3.fromRGB(255, 255, 255)
UIStrokeFrame.Thickness = 2
UIStrokeFrame.Parent = Frame

-- Propriedades do Title
Title.Parent = Frame
Title.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Title.Size = UDim2.new(1, 0, 0, 50)
Title.Font = Enum.Font.SourceSansBold
Title.Text = "tubergamer (beta) (1.0)"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 24

-- Adicionando cantos arredondados ao Title
UICornerTitle.CornerRadius = UDim.new(0, 50)
UICornerTitle.Parent = Title

-- Propriedades do Button
Button.Parent = Frame
Button.BackgroundColor3 = Color3.fromRGB(255, 140, 0)
Button.Position = UDim2.new(0.5, -75, 0.5, 10)
Button.Size = UDim2.new(0, 150, 0, 50)
Button.Text = "inf parts"
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.Font = Enum.Font.SourceSansBold
Button.TextSize = 20

-- Adicionando cantos arredondados ao Button
UICornerButton.CornerRadius = UDim.new(0, 50)
UICornerButton.Parent = Button

-- Propriedades do Message
Message.Parent = ScreenGui
Message.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Message.BackgroundTransparency = 0.5
Message.Position = UDim2.new(0.5, -100, 0.3, 0)
Message.Size = UDim2.new(0, 200, 0, 50)
Message.Font = Enum.Font.SourceSansBold
Message.Text = ""
Message.TextColor3 = Color3.fromRGB(255, 255, 255)
Message.TextSize = 20
Message.Visible = false

-- Função para mostrar mensagem temporária
local function showMessage(text)
    Message.Text = text
    Message.Visible = true
    wait(3) -- Mensagem visível por 3 segundos
    Message.Visible = false
end

-- Função para executar ou parar o script
local function toggleScript()
    running = not running
    if running then
        loopConnection = game:GetService("RunService").Stepped:Connect(function()
            local thefrickingfolder = workspace.Parts:GetChildren()
            for i = 1, #thefrickingfolder do
                local bigmagik = thefrickingfolder[i]
                bigmagik.Anchored = true
                bigmagik.Position = Vector3.new(69420, 60420, 69420) -- não pergunte sobre 69420, por favor
            end
        end)
        showMessage("inf parts enabled")
    else
        if loopConnection then
            loopConnection:Disconnect()
        end
        showMessage("inf parts stopped")
    end
end

-- Script do botão
Button.MouseButton1Click:Connect(toggleScript)
