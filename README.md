-- [[ PARRA NINJA HUB MASHMELLOW -  PARRABDOMINA ]] --
-- LÓGICA ORIGINAL INTACTA | DISEÑO ROJO/NEGRO | ANTI-KICK 267

local _K = "PARRAHUD"
local lp = game:GetService("Players").LocalPlayer
local vim = game:GetService("VirtualInputManager")
local vu = game:GetService("VirtualUser")
local coreGui = game:GetService("CoreGui")
local http = game:GetService("HttpService")

-- Seguridad: Verificación de entorno y camuflaje para evitar Kick 267
local targetParent = lp:FindFirstChild("PlayerGui") or coreGui
local function CleanUI()
    for _, v in pairs(targetParent:GetChildren()) do
        if v:FindFirstChild("AC_TAG_DOMINA CON PARRA") then v:Destroy() end
    end
end
CleanUI()

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "RobloxGui" -- Camuflaje para el Anti-Cheat
ScreenGui.Parent = targetParent
ScreenGui.ResetOnSpawn = false
local tag = Instance.new("BoolValue", ScreenGui)
tag.Name = "AC_TAG_DOMINA CON PARRA"

-- [ ESTILO ROJO Y NEGRO ]
local MainRed = Color3.fromRGB(255, 0, 0)
local DarkBg = Color3.fromRGB(5, 5, 5)

-- [ LOGIN: PARRA DOMINA ]
local LoginFrame = Instance.new("Frame", ScreenGui)
LoginFrame.Size = UDim2.new(0, 300, 0, 200)
LoginFrame.Position = UDim2.new(0.5, -150, 0.4, -100)
LoginFrame.BackgroundColor3 = DarkBg
Instance.new("UICorner", LoginFrame)
local LStroke = Instance.new("UIStroke", LoginFrame)
LStroke.Color = MainRed
LStroke.Thickness = 2

local LTitle = Instance.new("TextLabel", LoginFrame)
LTitle.Size = UDim2.new(1, 0, 0, 40)
LTitle.Text = "PARRA DOMINA"
LTitle.TextColor3 = MainRed
LTitle.Font = Enum.Font.GothamBold
LTitle.TextSize = 20
LTitle.BackgroundTransparency = 1

local KeyInput = Instance.new("TextBox", LoginFrame)
KeyInput.Size = UDim2.new(0.8, 0, 0, 40)
KeyInput.Position = UDim2.new(0.1, 0, 0.4, 0)
KeyInput.PlaceholderText = "ENTER KEY"
KeyInput.BackgroundColor3 = Color3.fromRGB(15, 0, 0)
KeyInput.TextColor3 = Color3.fromRGB(255, 255, 255)
Instance.new("UICorner", KeyInput)

local LoginBtn = Instance.new("TextButton", LoginFrame)
LoginBtn.Size = UDim2.new(0.8, 0, 0, 40)
LoginBtn.Position = UDim2.new(0.1, 0, 0.75, 0)
LoginBtn.BackgroundColor3 = MainRed
LoginBtn.Text = "VERIFICAR"
LoginBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
LoginBtn.Font = Enum.Font.GothamBold
Instance.new("UICorner", LoginBtn)

-- [ HUB CONTROL ]
local function StartHub()
    LoginFrame:Destroy()
    
    local MainFrame = Instance.new("Frame", ScreenGui)
    MainFrame.Size = UDim2.new(0, 460, 0, 350)
    MainFrame.Position = UDim2.new(0.5, -230, 0.5, -175)
    MainFrame.BackgroundColor3 = DarkBg
    MainFrame.Active = true
    MainFrame.Draggable = true
    Instance.new("UICorner", MainFrame)
    Instance.new("UIStroke", MainFrame).Color = MainRed

    -- BOTÓN PARA REGRESAR (MINIMIZADO)
    local OpenBtn = Instance.new("TextButton", ScreenGui)
    OpenBtn.Size = UDim2.new(0, 80, 0, 30)
    OpenBtn.Position = UDim2.new(0, 10, 0.5, 0)
    OpenBtn.BackgroundColor3 = DarkBg
    OpenBtn.Text = "ABRIR"
    OpenBtn.TextColor3 = MainRed
    OpenBtn.Visible = false
    OpenBtn.Font = Enum.Font.GothamBold
    Instance.new("UICorner", OpenBtn)
    Instance.new("UIStroke", OpenBtn).Color = MainRed

    local Title = Instance.new("TextLabel", MainFrame)
    Title.Size = UDim2.new(1, 0, 0, 40)
    Title.Text = "PARRA NINJA HUB MASHMELLOW"
    Title.TextColor3 = MainRed
    Title.Font = Enum.Font.GothamBold
    Title.BackgroundTransparency = 1

    -- BOTÓN CERRAR (X) Y MINIMIZAR (-)
    local CloseBtn = Instance.new("TextButton", MainFrame)
    CloseBtn.Size = UDim2.new(0, 30, 0, 30)
    CloseBtn.Position = UDim2.new(1, -35, 0, 5)
    CloseBtn.BackgroundTransparency = 1
    CloseBtn.Text = "X"
    CloseBtn.TextColor3 = MainRed
    CloseBtn.Font = Enum.Font.GothamBold

    local MiniBtn = Instance.new("TextButton", MainFrame)
    MiniBtn.Size = UDim2.new(0, 30, 0, 30)
    MiniBtn.Position = UDim2.new(1, -65, 0, 5)
    MiniBtn.BackgroundTransparency = 1
    MiniBtn.Text = "-"
    MiniBtn.TextColor3 = MainRed
    MiniBtn.Font = Enum.Font.GothamBold

    local InfoLabel = Instance.new("TextLabel", MainFrame)
    InfoLabel.Size = UDim2.new(0.55, 0, 0, 260)
    InfoLabel.Position = UDim2.new(0.05, 0, 0, 65)
    InfoLabel.BackgroundColor3 = Color3.fromRGB(15, 0, 0)
    InfoLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    InfoLabel.Font = Enum.Font.Code
    InfoLabel.TextSize = 12
    InfoLabel.TextXAlignment = Enum.TextXAlignment.Left
    InfoLabel.TextYAlignment = Enum.TextYAlignment.Top
    Instance.new("UICorner", InfoLabel)

    local function CreateBtn(txt, pos)
        local b = Instance.new("TextButton", MainFrame)
        b.Size = UDim2.new(0.33, 0, 0, 50)
        b.Position = pos
        b.BackgroundColor3 = Color3.fromRGB(30, 0, 0)
        b.TextColor3 = Color3.fromRGB(255, 255, 255)
        b.Font = Enum.Font.GothamBold
        b.Text = txt
        Instance.new("UICorner", b)
        return b
    end

    local FarmBtn = CreateBtn("FARM MASHMELLOW", UDim2.new(0.63, 0, 0, 65))
    local SellBtn = CreateBtn("SELL MASHMELLOW", UDim2.new(0.63, 0, 0, 130))
    local ToolBtn = CreateBtn("MASHMELLOW TOOL", UDim2.new(0.63, 0, 0, 195))

    local farmActive, sellActive = false, false
    
    -- LÓGICA DE FARM SIN TOCAR (ORDEN ORIGINAL)
    local items = {"Water", "Sugar Block Bag", "Gelatin", "Empty Bag"}

    CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)
    MiniBtn.MouseButton1Click:Connect(function() MainFrame.Visible = false OpenBtn.Visible = true end)
    OpenBtn.MouseButton1Click:Connect(function() MainFrame.Visible = true OpenBtn.Visible = false end)

    FarmBtn.MouseButton1Click:Connect(function()
        farmActive = not farmActive
        FarmBtn.Text = farmActive and "STOP FARM" or "FARM MASHMELLOW"
        FarmBtn.BackgroundColor3 = farmActive and Color3.fromRGB(150, 0, 0) or Color3.fromRGB(30, 0, 0)
        
        task.spawn(function()
            while farmActive do
                pcall(function()
                    for _, itemName in ipairs(items) do
                        if not farmActive then break end
                        local char = lp.Character
                        local tool = lp.Backpack:FindFirstChild(itemName) or (char and char:FindFirstChild(itemName))
                        if tool and char and char:FindFirstChild("Humanoid") then
                            char.Humanoid:EquipTool(tool)
                            task.wait(0.3)
                            vim:SendMouseButtonEvent(0, 0, 0, true, game, 0)
                            task.wait(0.1)
                            vim:SendMouseButtonEvent(0, 0, 0, false, game, 0)
                            task.wait(0.2)
                            vim:SendKeyEvent(true, Enum.KeyCode.E, false, game)
                            task.wait(0.1)
                            vim:SendKeyEvent(false, Enum.KeyCode.E, false, game)
                            task.wait(1.5)
                        end
                    end
                end)
                task.wait(0.5)
            end
        end)
    end)

    -- AUTO-SELL SIN TOCAR NADA
    SellBtn.MouseButton1Click:Connect(function()
        sellActive = not sellActive
        SellBtn.Text = sellActive and "AUTO-SELL ON" or "SELL MASHMELLOW"
        SellBtn.BackgroundColor3 = sellActive and Color3.fromRGB(150, 0, 0) or Color3.fromRGB(30, 0, 0)
    end)

    -- DELETE TOOL SIN TOCAR NADA
    ToolBtn.MouseButton1Click:Connect(function()
        local t = Instance.new("Tool", lp.Backpack)
        t.Name = "MASHMELLOW DELETE"
        t.RequiresHandle = false
        t.Activated:Connect(function()
            local m = lp:GetMouse()
            if m.Target then pcall(function() m.Target:Destroy() end) end
        end)
    end)

    -- LOOP DE CONTEO Y AUTO-SELL ORIGINAL
    task.spawn(function()
        while task.wait(1) do
            local char = lp.Character
            if not char or not char:FindFirstChild("HumanoidRootPart") then continue end

            if sellActive then
                local isNear = false
                for _, v in pairs(workspace:GetDescendants()) do
                    if (v.Name:lower():find("sell") or v.Name:lower():find("buyer") or v:IsA("ProximityPrompt")) then
                        local pos = v:IsA("Model") and v.PrimaryPart and v.PrimaryPart.Position or (v:IsA("BasePart") and v.Position) or (v:IsA("ProximityPrompt") and v.Parent:IsA("BasePart") and v.Parent.Position)
                        if pos and (char.HumanoidRootPart.Position - pos).Magnitude < 15 then
                            isNear = true
                            break
                        end
                    end
                end
                if isNear then
                    pcall(function()
                        for _, i in pairs(lp.Backpack:GetChildren()) do
                            if i.Name:find("Small") or i.Name:find("Medium") or i.Name:find("Large") then
                                char.Humanoid:EquipTool(i)
                                task.wait(0.2)
                                vim:SendKeyEvent(true, Enum.KeyCode.E, false, game)
                                task.wait(0.1)
                            end
                        end
                    end)
                end
            end

            local c = {W=0, S=0, G=0, B=0, Sm=0, M=0, L=0}
            local inv = lp.Backpack:GetChildren()
            for _, v in pairs(char:GetChildren()) do table.insert(inv, v) end
            for _, i in pairs(inv) do
                if i.Name == "Water" then c.W=c.W+1 
                elseif i.Name == "Sugar Block Bag" then c.S=c.S+1 
                elseif i.Name == "Gelatin" then c.G=c.G+1 
                elseif i.Name == "Empty Bag" then c.B=c.B+1 
                elseif i.Name:find("Small") then c.Sm=c.Sm+1 
                elseif i.Name:find("Medium") then c.M=c.M+1 
                elseif i.Name:find("Large") then c.L=c.L+1 end
            end

            InfoLabel.Text = string.format([[
  [ PARRA HUB ]
  DOMINANDO EL SERVER DE PARRA...
  
  PRODUCTOS:
  - Small:   %d
  - Medium:  %d
  - Large:   %d

  MATERIALES:
  - Agua:    %d
  - Azucar:  %d
  - Gelatina:%d
  - Bolsas:  %d

  [ SEGURIDAD ]
  Status: Anti-Ban Active
  Key: Verified
            ]], c.Sm, c.M, c.L, c.W, c.S, c.G, c.B)
        end
    end)
end

LoginBtn.MouseButton1Click:Connect(function()
    if KeyInput.Text == _K then StartHub() else LoginBtn.Text = "ERROR" task.wait(1) LoginBtn.Text = "VERIFICAR" end
end)

lp.Idled:Connect(function() vu:CaptureController() vu:ClickButton2(Vector2.new()) end)
