-- إنشاء القائمة الرئيسية والتحكم الكامل
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")

-- إزالة أي واجهة قديمة لمنع التكرار
if CoreGui:FindFirstChild("TimeBombDevGUI") then
    CoreGui.TimeBombDevGUI:Destroy()
end
if CoreGui:FindFirstChild("StrictAutoBombGUI") then
    CoreGui.StrictAutoBombGUI:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "TimeBombDevGUI"
ScreenGui.Parent = CoreGui

-- القائمة الرئيسية في منتصف الشاشة تماماً
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.Position = UDim2.new(0.5, -130, 0.5, -155)
MainFrame.Size = UDim2.new(0, 260, 0, 315)
MainFrame.Active = true
MainFrame.Draggable = true
Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 8)

-- شريط العنوان العلوي للقائمة الرئيسية
local Title = Instance.new("TextLabel", MainFrame)
Title.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Title.Size = UDim2.new(1, 0, 0, 38)
Title.Font = Enum.Font.SourceSansBold
Title.Text = "  Time Bomb 👑"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 17
Title.TextXAlignment = Enum.TextXAlignment.Left
Instance.new("UICorner", Title).CornerRadius = UDim.new(0, 8)

-- أزرار أقصى اليمين للقائمة الرئيسية (قفل، حذف، وتصغير)
local CloseBtn = Instance.new("TextButton", Title)
CloseBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
CloseBtn.Position = UDim2.new(1, -30, 0.18, 0)
CloseBtn.Size = UDim2.new(0, 24, 0, 24)
CloseBtn.Font = Enum.Font.SourceSansBold
CloseBtn.Text = "🗑️"
CloseBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseBtn.TextSize = 12
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 4)

local MinBtn = Instance.new("TextButton", Title)
MinBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
MinBtn.Position = UDim2.new(1, -60, 0.18, 0)
MinBtn.Size = UDim2.new(0, 24, 0, 24)
MinBtn.Font = Enum.Font.SourceSansBold
MinBtn.Text = "-"
MinBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
MinBtn.TextSize = 14
Instance.new("UICorner", MinBtn).CornerRadius = UDim.new(0, 4)

local LockBtn = Instance.new("TextButton", Title)
LockBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
LockBtn.Position = UDim2.new(1, -90, 0.18, 0)
LockBtn.Size = UDim2.new(0, 24, 0, 24)
LockBtn.Font = Enum.Font.SourceSansBold
LockBtn.Text = "🔓"
LockBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
LockBtn.TextSize = 11
Instance.new("UICorner", LockBtn).CornerRadius = UDim.new(0, 4)

-- اسم المطور
local DevLabel = Instance.new("TextLabel", MainFrame)
DevLabel.BackgroundTransparency = 1
DevLabel.Position = UDim2.new(0, 0, 0, 42)
DevLabel.Size = UDim2.new(1, 0, 0, 25)
DevLabel.Font = Enum.Font.SourceSansBold
DevLabel.Text = "المطور : عبدالله العتيبي"
DevLabel.TextColor3 = Color3.fromRGB(255, 50, 50)
DevLabel.TextSize = 15

-- --- الأزرار داخل القائمة الرئيسية (بالترتيب الجديد) ---

-- 1. زر Korblox
local KorbloxBtn = Instance.new("TextButton", MainFrame)
KorbloxBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
KorbloxBtn.Position = UDim2.new(0.08, 0, 0.25, 0)
KorbloxBtn.Size = UDim2.new(0.84, 0, 0, 34)
KorbloxBtn.Font = Enum.Font.SourceSansBold
KorbloxBtn.Text = "Korblox"
KorbloxBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
KorbloxBtn.TextSize = 15
Instance.new("UICorner", KorbloxBtn).CornerRadius = UDim.new(0, 6)

-- 2. زر Headless
local HeadlessBtn = Instance.new("TextButton", MainFrame)
HeadlessBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
HeadlessBtn.Position = UDim2.new(0.08, 0, 0.41, 0)
HeadlessBtn.Size = UDim2.new(0.84, 0, 0, 34)
HeadlessBtn.Font = Enum.Font.SourceSansBold
HeadlessBtn.Text = "Headless"
HeadlessBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
HeadlessBtn.TextSize = 15
Instance.new("UICorner", HeadlessBtn).CornerRadius = UDim.new(0, 6)

-- 3. زر Auto 💣 (صار فوق الريتش)
local AutoMenuBtn = Instance.new("TextButton", MainFrame)
AutoMenuBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
AutoMenuBtn.Position = UDim2.new(0.08, 0, 0.57, 0)
AutoMenuBtn.Size = UDim2.new(0.84, 0, 0, 34)
AutoMenuBtn.Font = Enum.Font.SourceSansBold
AutoMenuBtn.Text = "Auto 💣"
AutoMenuBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
AutoMenuBtn.TextSize = 15
Instance.new("UICorner", AutoMenuBtn).CornerRadius = UDim.new(0, 6)

-- 4. زر Reach الجديد (صار تحته)
local ReachBtn = Instance.new("TextButton", MainFrame)
ReachBtn.BackgroundColor3 = Color3.fromRGB(180, 40, 40)
ReachBtn.Position = UDim2.new(0.08, 0, 0.73, 0)
ReachBtn.Size = UDim2.new(0.84, 0, 0, 34)
ReachBtn.Font = Enum.Font.SourceSansBold
ReachBtn.Text = "Reach : OFF"
ReachBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ReachBtn.TextSize = 15
Instance.new("UICorner", ReachBtn).CornerRadius = UDim.new(0, 6)


-- ==========================================
-- قائمة الأوتو الفرعية المصغرة
-- ==========================================
local AutoScreenGui = Instance.new("ScreenGui")
AutoScreenGui.Name = "StrictAutoBombGUI"
AutoScreenGui.Parent = CoreGui
AutoScreenGui.Enabled = false

local AutoMainFrame = Instance.new("Frame")
AutoMainFrame.Parent = AutoScreenGui
AutoMainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
AutoMainFrame.Position = UDim2.new(0, 15, 0, 75)
AutoMainFrame.Size = UDim2.new(0, 180, 0, 85)
AutoMainFrame.Active = true
AutoMainFrame.Draggable = true
Instance.new("UICorner", AutoMainFrame).CornerRadius = UDim.new(0, 8)

local AutoLockBtn = Instance.new("TextButton")
AutoLockBtn.Parent = AutoMainFrame
AutoLockBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
AutoLockBtn.Position = UDim2.new(1, -30, 0.1, 0)
AutoLockBtn.Size = UDim2.new(0, 22, 0, 22)
AutoLockBtn.Font = Enum.Font.SourceSansBold
AutoLockBtn.Text = "🔓"
AutoLockBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
AutoLockBtn.TextSize = 10
Instance.new("UICorner", AutoLockBtn).CornerRadius = UDim.new(0, 4)

local AutoButton = Instance.new("TextButton")
AutoButton.Parent = AutoMainFrame
AutoButton.BackgroundColor3 = Color3.fromRGB(180, 40, 40)
AutoButton.Position = UDim2.new(0.1, 0, 0.42, 0)
AutoButton.Size = UDim2.new(0.8, 0, 0, 38)
AutoButton.Font = Enum.Font.SourceSansBold
AutoButton.Text = "Auto Bomb : OFF"
AutoButton.TextColor3 = Color3.fromRGB(255, 255, 255)
AutoButton.TextSize = 13
Instance.new("UICorner", AutoButton).CornerRadius = UDim.new(0, 6)


-- ==========================================
-- وظائف وربط الأزرار
-- ==========================================

local autoEnabled = false
local reachEnabled = false

AutoMenuBtn.MouseButton1Click:Connect(function()
    AutoScreenGui.Enabled = not AutoScreenGui.Enabled
end)

local autoLocked = false
AutoLockBtn.MouseButton1Click:Connect(function()
    autoLocked = not autoLocked
    AutoMainFrame.Draggable = not autoLocked
    if autoLocked then
        AutoLockBtn.Text = "🔒"
        AutoLockBtn.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    else
        AutoLockBtn.Text = "🔓"
        AutoLockBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    end
end)

CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
    AutoScreenGui:Destroy()
end)

local minimized = false
MinBtn.MouseButton1Click:Connect(function()
    minimized = not minimized
    DevLabel.Visible = not minimized
    KorbloxBtn.Visible = not minimized
    HeadlessBtn.Visible = not minimized
    AutoMenuBtn.Visible = not minimized
    ReachBtn.Visible = not minimized
    if minimized then
        MainFrame.Size = UDim2.new(0, 260, 0, 38)
        MinBtn.Text = "+"
    else
        MainFrame.Size = UDim2.new(0, 260, 0, 315)
        MinBtn.Text = "-"
    end
end)

local locked = false
LockBtn.MouseButton1Click:Connect(function()
    locked = not locked
    MainFrame.Draggable = not locked
    if locked then
        LockBtn.Text = "🔒"
        LockBtn.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    else
        LockBtn.Text = "🔓"
        LockBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    end
end)

KorbloxBtn.MouseButton1Click:Connect(function()
    pcall(function()
        loadstring(game:HttpGet("https://scriptblox.com/raw/Universal-Script-Korblox-All-145374"))()
    end)
end)

HeadlessBtn.MouseButton1Click:Connect(function()
    pcall(function()
        loadstring(game:HttpGet("https://scriptblox.com/raw/Universal-Script-Headless-(R6R15)-224493"))()
    end)
end)

-- تفعيل / إيقاف زر Reach
ReachBtn.MouseButton1Click:Connect(function()
    reachEnabled = not reachEnabled
    if reachEnabled then
        ReachBtn.Text = "Reach : ON"
        ReachBtn.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    else
        ReachBtn.Text = "Reach : OFF"
        ReachBtn.BackgroundColor3 = Color3.fromRGB(180, 40, 40)
        -- تنظيف المربعات عند الإيقاف
        for _, p in pairs(Players:GetPlayers()) do
            if p.Character then
                local hl = p.Character:FindFirstChild("ReachHighlight")
                if hl then hl:Destroy() end
            end
        end
    end
end)

AutoButton.MouseButton1Click:Connect(function()
    autoEnabled = not autoEnabled
    if autoEnabled then
        AutoButton.Text = "Auto Bomb : ON"
        AutoButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    else
        AutoButton.Text = "Auto Bomb : OFF"
        AutoButton.BackgroundColor3 = Color3.fromRGB(180, 40, 40)
    end
end)

-- تشغيل مظهر الريتش (مربع أحمر على حجم الجسم ولا يظهر عليك)
RunService.RenderStepped:Connect(function()
    pcall(function()
        if reachEnabled then
            for _, p in pairs(Players:GetPlayers()) do
                if p ~= LocalPlayer and p.Character then
                    local char = p.Character
                    local humanoid = char:FindFirstChildOfClass("Humanoid")
                    if humanoid and humanoid.Health > 0 then
                        local highlight = char:FindFirstChild("ReachHighlight")
                        if not highlight then
                            highlight = Instance.new("Highlight")
                            highlight.Name = "ReachHighlight"
                            highlight.Adornee = char
                            highlight.FillTransparency = 1
                            highlight.OutlineColor = Color3.fromRGB(255, 0, 0)
                            highlight.OutlineTransparency = 0
                            highlight.Parent = char
                        end
                    else
                        local hl = char:FindFirstChild("ReachHighlight")
                        if hl then hl:Destroy() end
                    end
                else
                    -- ضمان عدم ظهور المربع عليك نهائياً
                    if p == LocalPlayer and p.Character then
                        local hl = p.Character:FindFirstChild("ReachHighlight")
                        if hl then hl:Destroy() end
                    end
                end
            end
        end
    end)
end)

local function hasBomb()
    local character = LocalPlayer.Character
    if not character then return false end
    for _, item in pairs(character:GetChildren()) do
        if item:IsA("Tool") then
            local name = item.Name:lower()
            if name:find("bomb") or name:find("c4") or name:find("قنبلة") then
                return true
            end
        end
    end
    if LocalPlayer:FindFirstChild("Backpack") then
        for _, item in pairs(LocalPlayer.Backpack:GetChildren()) do
            if item:IsA("Tool") then
                local name = item.Name:lower()
                if name:find("bomb") or name:find("c4") or name:find("قنبلة") then
                    return true
                end
            end
        end
    end
    return false
end

local function isStrictEnemy(player)
    if player == LocalPlayer then return false end
    if LocalPlayer.Team and player.Team then
        if LocalPlayer.Team == player.Team then
            return false
        end
    end
    return true
end

local function isInCurrentMap(targetCharacter)
    local myChar = LocalPlayer.Character
    if not myChar or not myChar:FindFirstChild("HumanoidRootPart") then return false end
    if not targetCharacter or not targetCharacter:FindFirstChild("HumanoidRootPart") then return false end
    
    local myPos = myChar.HumanoidRootPart.Position
    local targetPos = targetCharacter.HumanoidRootPart.Position
    
    if (myPos - targetPos).Magnitude > 250 then return false end
    if math.abs(myPos.Y - targetPos.Y) > 80 then return false end
    
    return true
end

local function getValidMapEnemy()
    local character = LocalPlayer.Character
    if not character or not character:FindFirstChild("HumanoidRootPart") then return nil end
    
    local bestTarget = nil
    local shortestDistance = math.huge
    
    for _, player in pairs(Players:GetPlayers()) do
        if isStrictEnemy(player) and player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character:FindFirstChild("Humanoid") then
            if player.Character.Humanoid.Health > 0 then
                if isInCurrentMap(player.Character) then
                    local targetHRP = player.Character.HumanoidRootPart
                    local distance = (character.HumanoidRootPart.Position - targetHRP.Position).Magnitude
                    if distance < shortestDistance then
                        shortestDistance = distance
                        bestTarget = targetHRP
                    end
                end
            end
        end
    end
    
    return bestTarget
end

task.spawn(function()
    while true do
        RunService.RenderStepped:Wait()
        pcall(function()
            if autoEnabled and hasBomb() then
                local character = LocalPlayer.Character
                if character and character:FindFirstChild("Humanoid") and character:FindFirstChild("HumanoidRootPart") then
                    local targetHRP = getValidMapEnemy()
                    if targetHRP then
                        character.Humanoid:MoveTo(targetHRP.Position)
                        
                        local distance = (character.HumanoidRootPart.Position - targetHRP.Position).Magnitude
                        if distance < 6 then
                            local tool = character:FindFirstChildOfClass("Tool")
                            if tool then
                                tool:Activate()
                            end
                        end
                    end
                end
            end
        end)
    end
end)