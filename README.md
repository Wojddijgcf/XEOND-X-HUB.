local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("XEOND  X Hub", "Synapse")

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")
 
--Properties:
 
ScreenGui.Parent = game:GetService("CoreGui")
 
Frame.Name = "Frame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.BackgroundTransparency = 1.000
Frame.Position = UDim2.new(-0.254758418, 0, -0.37299037, 0)
Frame.Size = UDim2.new(0, 2061, 0, 1048)
Frame.Image = "rbxassetid://3570695787"
Frame.ImageColor3 = Color3.fromRGB(57, 57, 57)
Frame.ScaleType = Enum.ScaleType.Slice
Frame.SliceCenter = Rect.new(100, 100, 100, 100)
Frame.SliceScale = 0.120
 
TextLabel.Parent = ScreenGui
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Position = UDim2.new(0.419472903, 0, 0.443729907, 0)
TextLabel.Size = UDim2.new(0, 219, 0, 70)
TextLabel.Font = Enum.Font.SpecialElite
TextLabel.Text = "XEOND X HUB"
TextLabel.TextColor3 = Color3.fromRGB(247, 72, 119)
TextLabel.TextSize = 100.000
TextLabel.TextStrokeTransparency = 0.000
wait(4)
game.CoreGui:FindFirstChild("ScreenGui"):Destroy()


local Tab = Window:NewTab("Player")
local PlayerSection = Tab:NewSection("!Player!")
local Section = Tab:NewSection("!Select Player!")
Plr = {}
for i,v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(Plr,v.Name) 
end
local drop = Section:NewDropdown("Select Player!", "Click To Select", Plr, function(t)
   PlayerTP = t
end)
local Weaponlist = {}
local Weapon = nil

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
end

Section:NewDropdown("select weapon", " ", Weaponlist, function(currentOption)
    Weapon = currentOption
end)

Section:NewToggle("Auto Equip", " ", function(a)
AutoEquiped = a
end)

spawn(function()
while wait() do
if AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Weapon))
end)
end
end
end)
Section:NewButton("Click To TP", "", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame
end)
Section:NewToggle("Auto Tp", "", function(t)
_G.TPPlayer = t
while _G.TPPlayer do wait()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame
end
end)

Section:NewButton("Refresh Dropdown","Refresh Dropdown", function()
  drop:Refresh(Plr)
end)
PlayerSection:NewSlider("WalkSpeed", "MoreSpeed", 500, 0, function(s) 
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)
 
PlayerSection:NewDropdown("Admin:O", "Give player admin", {"admin", "script", "soon"}, function(s)
    loadstring(game:HttpGet("https://raw.githubusercontent.com/fatesc/fates-admin/main/main.lua"))();
    print(currentOption)
end)
 
PlayerSection:NewSlider("JumpPower", "SliderInfo", 500, 50, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)
 
 
local Tab = Window:NewTab("Aimbot")
local AimbotSection = Tab:NewSection("Aimbot")
AimbotSection:NewButton("Aimbot", "XEOND  X Hub", function(s)
     loadstring(game:HttpGet("https://raw.githubusercontent.com/ThunderZ-HUB/HUB/main/Aimbot"))()
    print("Clicked")
end)
Section:NewButton("Aimbot", "XEOND X ", function(s)
getgenv().setting = {
    Fov = 50,
    Color = Color3.fromRGB(191, 255, 209),
    LockPlayers = false,
    LockPlayersBind = Enum.KeyCode.L,
    resetPlayersBind = Enum.KeyCode.P,
}
loadstring(game:HttpGet('https://raw.githubusercontent.com/Besty191/MAZI-API/main/Blox_Fruit_Silent_Aim'))()
    print("Clicked")
end)

local Tab = Window:NewTab("ADMIN")
local AimbotSection = Tab:NewSection("ADMIN")
AimbotSection:NewButton("ADMIN", "XEOND  X Hub", function(s)
     loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
    print("Clicked")
end)


local Tab = Window:NewTab("SCRIPT")
Section:NewToggle("AutoFarm", "AutoFarm", function(state)
_G.Auto_Farm = true -- true / false

function totarget(p)
    local Distance2 = (p.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    local tween_s = game:service"TweenService"
    local info = TweenInfo.new(Distance2/350, Enum.EasingStyle.Linear)
    local tween = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = p})
    tween:Play()
    if Distance2 <= 75 then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p
    end
end

function checklevel()
    local lv = game:GetService("Players").LocalPlayer.Data.Level.Value
    if lv == 1 or lv <= 9 then
        Mon = "Bandit [Lv. 5]"
        Title = "Bandit"
        QuestName = "BanditQuest1"
        QuestNumber = 1
        CFrameQuest = CFrame.new(1061.15271, 16.7367725, 1548.93018, -0.836085379, -3.89774577e-08, 0.548599303, -1.17575967e-08, 1, 5.31300408e-08, -0.548599303, 3.79710414e-08, -0.836085379)
        CFrameMon = CFrame.new(1151.11829, 16.7761021, 1599.73499, -0.999999762, 0, -0.000701809535, 0, 1, 0, 0.000701809535, 0, -0.999999762)
        CFramePuk = CFrame.new(1101.75903, 67.6758957, 1617.50391, -0.399259984, -5.24373327e-08, -0.916837752, -1.74068084e-08, 1, -4.96134582e-08, 0.916837752, -3.84945009e-09, -0.399259984)
    elseif lv == 10 or lv <= 14 then
        Mon = "Monkey [Lv. 14]"
        Title = "Monkey"
        QuestName = "JungleQuest"
        QuestNumber = 1
        CFrameQuest = CFrame.new(-1599.23096, 37.8653831, 153.335953, -0.0493941903, 1.29583286e-08, 0.998779356, 3.21716165e-08, 1, -1.13831318e-08, -0.998779356, 3.15700852e-08, -0.0493941903)
        CFrameMon = CFrame.new(-1479.76099, 23.195364, 106.327942, 0.96289885, 5.22265786e-10, -0.269862473, 6.59528099e-10, 1, 4.28857172e-09, 0.269862473, -4.30744285e-09, 0.96289885)
        CFramePuk = CFrame.new(-1776.32959, 61.1782455, 66.8902054, -0.912609756, -2.38546143e-08, 0.408831745, -2.14773621e-08, 1, 1.04056577e-08, -0.408831745, 7.15677129e-10, -0.912609756)
        elseif lv == 15 or lv <= 29 then
        Mon = "Gorilla [Lv. 20]"
        Title = "Gorilla"
        QuestName = "JungleQuest"
        QuestNumber = 2
        CFrameQuest = CFrame.new(-1599.23096, 37.8653831, 153.335953, -0.0493941903, 1.29583286e-08, 0.998779356, 3.21716165e-08, 1, -1.13831318e-08, -0.998779356, 3.15700852e-08, -0.0493941903)
        CFrameMon = CFrame.new(-1242.46655, 6.62262297, -523.166382, -0.974416733, 9.23166681e-08, -0.224748924, 9.58993027e-08, 1, -5.02435071e-09, 0.224748924, -2.64490758e-08, -0.974416733)
        CFramePuk = CFrame.new(-1133.4574, 40.8067436, -526.086792, 0.647179008, -2.76535794e-10, 0.762338042, 3.26674865e-08, 1, -2.73699801e-08, -0.762338042, 4.26169464e-08, 0.647179008)
    end
end

spawn(function()
    while task.wait(.1) do
        pcall(function()
            if _G.Auto_Farm then
            checklevel()
                if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
totarget(CFrameQuest)
wait(.3)
local args = {
    [1] = "StartQuest",
    [2] = QuestName,
    [3] = QuestNumber
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        for i,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v.Name == Mon and v2.Name == Mon then
            totarget(v.HumanoidRootPart.CFrame * CFrame.new(0,1,15))
            v.HumanoidRootPart.Size = Vector3.new(60,2.5,60)
            v.HumanoidRootPart.CFrame = CFrameMon
            game:GetService'VirtualUser':CaptureController()
            game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
            v2.HumanoidRootPart.CanCollide = false
            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
        end
        end
    end
                end
            end
        end)
    end
end)

spawn(function()
    while task.wait(.1) do
        pcall(function()
            if _G.Auto_Farm then
            checklevel()
    if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, Title) then
local args = {
    [1] = "AbandonQuest"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
            end
        end)
    end
end)

spawn(function()
    while task.wait(.1) do
        pcall(function()
            if _G.Auto_Farm then
            checklevel()
            if not game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                totarget(CFramePuk)
            end
            end
        end)
    end
end)

spawn(function()
    while task.wait(.1) do
        pcall(function()
            if _G.Auto_Farm then
            checklevel()
            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if v.Name == Mon then
            if v.Humanoid.Health == 0 then
            v:Destroy()
            end
            end
            end
            end
        end)
    end
end)
    if state then
        print("Toggle On")
    else
        print("Toggle Off")
    end
end)
Section:NewButton("30M", "---", function(s)
getgenv().Config = {
    ["Team"] = "Pirates", --// Marines, Pirates
    ["Webhook"] = {
        ["Enable"] = false, --// Enable if you have Webhook Url
        ["Url"] = "" --// Your webhook url
    },
    ["Skip"] = {
        ["V4"] = true, --// Skip V4
        ["Fruit"] = { --// Skip Fruit
            "Leopard-Leopard",
            "Venom-Venom",
            "Dough-Dough",
            "Portal-Portal"
        }
    },
    ["Chat"] = {
        ["Enable"] = false, --// Enable Chat
        ["Content"] = {"Hello me use MTriet Hub Auto Bounty"} --// Content
    },
    ["Misc"] = {
        ["Hide If Low Health"] = true, --// Run
        ["Hide Health"] = {4000,5000}, --// Health for run
        ["Lock Camera"] = true, --// Lock Cam to target
        ["FPS Boost"] = false, --// Booster FPS
        ["White Screen"] = false, --// White Screen
        ["Bypass TP"] = true, --// Bypass TP 1 -> 2 hit
        ["Spam All Skill On V4"] = true, --// If you have v4, warn: change your weapon setting
        ["Gun Method"] = false --// Enable if you use gun
    },
    --//  Next
    ["Weapons"] = {
        ["Melee"] = {
            ["Enable"] = true,
            ["Delay"] = 2.5,
            ["Skills"] = {
                ["Z"] = {["Enable"] = true, ["HoldTime"] = 0.1},
                ["X"] = {["Enable"] = true, ["HoldTime"] = 0.1},
                ["C"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["V"] = {["Enable"] = false, ["HoldTime"] = 0}
            }
        },
        ["Blox Fruit"] = {
            ["Enable"] = false,
            ["Delay"] = 3,
            ["Skills"] = {
                ["Z"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["X"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["C"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["V"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["F"] = {["Enable"] = false, ["HoldTime"] = 0}
            }
        },
        --// Copy Next
        ["Sword"] = {
            ["Enable"] = true,
            ["Delay"] = 1.5,
            ["Skills"] = {
                ["Z"] = {["Enable"] = true, ["HoldTime"] = 1},
                ["X"] = {["Enable"] = true, ["HoldTime"] = 0}
            }
        },
        ["Gun"] = {
            ["Enable"] = true,
            ["Delay"] = 1.2,
            ["Skills"] = {
                ["Z"] = {["Enable"] = true, ["HoldTime"] = 0},
                ["X"] = {["Enable"] = true, ["HoldTime"] = 0}
            }
        }
    }
}
repeat wait() until game:IsLoaded()
loadstring(game:HttpGet("https://raw.githubusercontent.com/Minhtriettt/Hunt/main/AutoBountyV2.lua"))()
    print("Clicked")
end)

local AimbotSection = Tab:NewSection("Blox fruits")
AimbotSection:NewButton("MTriet Hub", "Bloxfruits", function(s)
     loadstring(game:HttpGet("https://raw.githubusercontent.com/Minhtriettt/Free-Script/main/MTriet-Hub.lua"))()
    print("Clicked")
end)
Section:NewButton("CheckQuests", "Bloxfruits", function(s)
LocalPlayer = game:GetService("Players").LocalPlayer
Char = LocalPlayer.Character

_G.AutoFarm = true
local GetQuests = function(N,NB)
    local args = {
        [1] = "StartQuest",
        [2] = N or "BanditQuest1",
        [3] = NB or 1
    }
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(unpack(args))    
end;local ChackQ = function()
    local Lv = LocalPlayer.Data.Level
    if Lv.Value >= 1 and Lv.Value <= 9 then
        return {
            ["Mon"] = 'Bandit',
            ["NumQ"] = 'BanditQuest1',
            ["NameQ"] = 1,
            ["CFrameQ"] = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544),
            ["CFrameMon"] = CFrame.new(1196.172, 11.8689699, 1616.95923, -0.309060812, 0, 0.951042235, 0, 1, 0, -0.951042235, 0, -0.309060812)
        }
    elseif Lv.Value >= 10 and Lv.Value <= 9e99 then
        return {
            ["Mon"] = 'Monkey',
            ["NumQ"] = 'JungleQuest',
            ["NameQ"] = 1,
            ["CFrameQ"] = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0),
            ["CFrameMon"] = CFrame.new(-1619.10632, 21.7005882, 142.148117, 0.342042625, -0.000311157171, 0.939684391, 0.000113111477, 0.99999994, 0.000289957155, -0.939684391, 7.11137545e-06, 0.342042685)
        }
    end
end;local TW = function(...)
    local CFrame = {...}
    pcall(function()
        if not _G.StopTween then
            local Distance = (CFrame[1].Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
            Tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/20, Enum.EasingStyle.Cubic),{CFrame = CFrame[1]})
            if _G.StopTween then Tween:Cancel()
            elseif game.Players.LocalPlayer.Character.Humanoid.Health > 0 then Tween:Play() end
            if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("OMG Hub") then
                local Noclip = Instance.new("BodyVelocity")
                Noclip.Name = "OMG Hub"
                Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
                Noclip.MaxForce = Vector3.new(9e99,9e99,9e99)
                Noclip.Velocity = Vector3.new(0,0,0)
            end
        end
    end)
end;local ClearQ = function()
    if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, tostring(ChackQ()["Mon"])) then
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
    end
end

spawn(function()
    while wait() do
        pcall(function()
            if _G.AutoFarm then
                local UIQ = LocalPlayer.PlayerGui.Main.Quest
                ClearQ()
                if not UIQ.Visible or UIQ.Visible == false then
                    TW(ChackQ()["CFrameQ"])
                    if (ChackQ()["CFrameQ"].Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 15 then
                        wait(.2)
                        GetQuests(ChackQ()["NumQ"],ChackQ()["NameQ"])
                    end
                else
                    if game:GetService("Workspace").Enemies:FindFirstChild(ChackQ()["Mon"]) then
                        for _i,_v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if _v.Name == tostring(ChackQ()["Mon"]) and _v:FindFirstChild("Humanoid") and _v:FindFirstChild("HumanoidRootPart") then
                                if _v.Humanoid.Health > 0 then
                                    repeat wait()
                                        TW(_v:FindFirstChild("HumanoidRootPart").CFrame * CFrame.new(0,0,5))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not _G.AutoFarm or _G.AutoFarm == false or not _v.Parent or _v.Humanoid.Health <= 0 or not UIQ.Visible or UIQ.Visible == false
                                end
                            end
                        end
                    else
                        Char.HumanoidRootPart.CFrame = ChackQ()["CFrameMon"]
                    end
                end
            end
        end)
    end
end)
    print("Clicked")
end)
Section:NewButton("Door Hub", "Bloxfruits", function(s)
loadstring(game:HttpGet("https://www.knuxy92.com/Door_Hub/Script.lua"))()
    print("Clicked")
end)
Section:NewButton("Vector Hub", "Bloxfruits", function(s)
_G.Mode = "English"
loadstring(game:HttpGet("https://raw.githubusercontent.com/Tuxoz/VectorHub/main/MBPC"))()
    print("Clicked")
    Section:NewButton("Annie Hub", "Bloxfruits", function(s)
 loadstring(game:HttpGet('https://raw.githubusercontent.com/1st-Mars/Annie/main/1st.lua'))()
    print("Clicked")
end)
end)Section:NewButton("King Legacy ", "King Legacy ", function(s)
repeat wait() until game:IsLoaded()
loadstring(game:HttpGet("https://raw.githubusercontent.com/DookDekDEE/Hyper/main/script.lua"))()
    print("Clicked")
end)
Section:NewToggle("AutoChest", "AutoChest", function(state)
loadstring(game:HttpGet('https://raw.githubusercontent.com/SHAREHACK/bloxfruit/main/autochest'))()
    if state then
        print("Toggle On")
    else
        print("Toggle Off")
    end
end)
Section:NewButton("MAX", "MAX", function(s)
loadstring(game:HttpGet("https://raw.githubusercontent.com/scriptpastebin/raw/main/MaxFast"))()
    print("Clicked")
end)
Section:NewToggle("KillAura", "KillAura", function(state)
_G.KillAura = true -- true/false
 
while _G.KillAura do wait()
 
for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
    v.Humanoid.Health = die
end
 
end
    if state then
        print("Toggle On")
    else
        print("Toggle Off")
    end
end)
local Weaponlist = {}
local Weapon = nil

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
end

Section:NewDropdown("select weapon", " ", Weaponlist, function(currentOption)
    Weapon = currentOption
end)

Section:NewToggle("Auto Equip", " ", function(a)
AutoEquiped = a
end)

spawn(function()
while wait() do
if AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Weapon))
end)
end
end
end)
Section:NewToggle("FastAttack", "Click to use FastAttack", function(state)
local Fast = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local CameraShaker = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
_G.Fastattack = state -- true\false
game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.Fastattack then
Fast.activeController.timeToNextAttack = 0
Fast.activeController.hitboxMagnitude = 50
game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(686, 352))
CameraShaker.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
end
end)
end)
end)
Section:NewLabel("Bringmob")
Section:NewToggle("bringmob", "Click to use bringmob", function(state)
_G.bringmob = state
while _G.bringmob do wait()
    pcall(function()
for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
for x,y in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
if v.Name == "Bandit [Lv. 5]" then
    if y.Name == "Bandit [Lv. 5]" then
   v.HumanoidRootPart.CFrame = y.HumanoidRootPart.CFrame
   v.HumanoidRootPart.Size = Vector3.new(60,60,60)
   y.HumanoidRootPart.Size = Vector3.new(60,60,60)
   v.HumanoidRootPart.Transparency = 1
   v.HumanoidRootPart.CanCollide = false
   y.HumanoidRootPart.CanCollide = false
   v.Humanoid.WalkSpeed = 0
   y.Humanoid.WalkSpeed = 0
   v.Humanoid.JumpPower = 0
   y.Humanoid.JumpPower = 0
   if sethiddenproperty then
     sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
end
end
end
end
end
end)
end
end)
Section:NewButton("speed of legends", "XEOND X Hub", function(s)
loadstring(game:HttpGet("https://pastebin.com/raw/9CnxdySz"))()
    print("Clicked")
end)
Section:NewButton("strongest punch simulator", "XEOND X Hub", function(s)
loadstring(game:HttpGet('https://raw.githubusercontent.com/FlmesCoding/SwirlHub/main/Loader.lua'))()
    print("Clicked")
end)
Section:NewButton("Bicycle", "XEOND X Hub", function(s)
loadstring(game:HttpGet("https://pastebin.com/raw/njuhL3rM", true))()
    print("Clicked")
end)
Section:NewButton("Doors", "Doors", function(s)
loadstring(game:HttpGet(('https://pastebin.com/raw/R8QMbhzv')))()
    print("Clicked")
end)
Section:NewButton("blade ball", "blade ball", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/3345-c-a-t-s-u-s/SourceLua/main/Blade_Ball.lua"))()
    print("Clicked")
end)
Section:NewButton("HoHo Hub", "Bloxfruits", function(s)
loadstring(game:HttpGet('https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI'))()
    print("Clicked")
end)

local Tab = Window:NewTab("‽")
Section:NewButton("FIY", "fly", function()
loadstring(game:HttpGet(('https://pastebin.com/raw/VViuAmm5'),true))()
    print("Clicked")
end)
local Tab = Window:NewTab("Nolip")
Section:NewButton("Nolip", "Nolip", function(s)
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local Clipon = false

Noclip.Name = "Noclip"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(0.266667, 0.00392157, 0.627451)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "Noclip"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(0.266667, 0.00392157, 0.627451)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = "Toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "Created by KingLuna"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true

Toggle.MouseButton1Click:connect(function()
	if Status.Text == "off" then
		Clipon = true
		Status.Text = "on"
		Status.TextColor3 = Color3.new(0,185,0)
		Stepped = game:GetService("RunService").Stepped:Connect(function()
			if not Clipon == false then
				for a, b in pairs(Workspace:GetChildren()) do
                if b.Name == Plr.Name then
                for i, v in pairs(Workspace[Plr.Name]:GetChildren()) do
                if v:IsA("BasePart") then
                v.CanCollide = false
                end end end end
			else
				Stepped:Disconnect()
			end
		end)
	elseif Status.Text == "on" then
		Clipon = false
		Status.Text = "off"
		Status.TextColor3 = Color3.new(170,0,0)
	end
end)
    print("Clicked")
end)
Section:NewButton("copy", "copy", function(s)
-- Objects
plr = game.Players.LocalPlayer
ControlGui = Instance.new("ScreenGui")
Frame = Instance.new("Frame")
TextButton = Instance.new("TextButton")
TextBox = Instance.new("TextBox")
 
-- Properties
 
ControlGui.Name = "ControlGui"
ControlGui.Parent = plr.PlayerGui
 
Frame.Parent = ControlGui
Frame.BackgroundColor3 = Color3.new(1, 1, 1)
Frame.Position = UDim2.new(0, 300, 0, 200)
Frame.Size = UDim2.new(0, 300, 0, 150)
Frame.Active = true
Frame.Draggable = true
 
TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.new(1, 1, 1)
TextButton.Position = UDim2.new(0, 50, 0, 90)
TextButton.Size = UDim2.new(0, 200, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.FontSize = Enum.FontSize.Size32
TextButton.Text = "Control"
TextButton.TextSize = 30
TextButton.MouseButton1Down:connect(function()
	if TextButton.Text == "Control" then
	TextButton.Text = "UnControl"	
	workspace[TextBox.Text].Humanoid.PlatformStand = true
	W1 = Instance.new("Weld",workspace)
	W1.Name = "Weld1"
	W1.Part0 = plr.Character.Torso
	W1.Part1 = workspace[TextBox.Text].Torso
	W2 = Instance.new("Weld",workspace)
	W2.Name = "Weld2"
	W2.Part0 = plr.Character.Head
	W2.Part1 = workspace[TextBox.Text].Head
	W3 = Instance.new("Weld",workspace)
	W3.Name = "Weld3"
	W3.Part0 = plr.Character.HumanoidRootPart
	W3.Part1 = workspace[TextBox.Text].HumanoidRootPart
	W4 = Instance.new("Weld",workspace)
	W4.Name = "Weld4"
	W4.Part0 = plr.Character["Left Arm"]
	W4.Part1 = workspace[TextBox.Text]["Left Arm"]
	W5 = Instance.new("Weld",workspace)
	W5.Name = "Weld5"
	W5.Part0 = plr.Character["Left Leg"]
	W5.Part1 = workspace[TextBox.Text]["Left Leg"]
	W6 = Instance.new("Weld",workspace)
	W6.Name = "Weld6"
	W6.Part0 = plr.Character["Right Arm"]
	W6.Part1 = workspace[TextBox.Text]["Right Arm"]
	W7 = Instance.new("Weld",workspace)
	W7.Name = "Weld7"
	W7.Part0 = plr.Character["Right Leg"]
	W7.Part1 = workspace[TextBox.Text]["Right Leg"]
	for i,v in pairs(plr.Character:GetChildren()) do
			if v.ClassName == "Part" then
				v.Transparency = 1
			end
			plr.Character.HumanoidRootPart.Transparency = 1
			if v.ClassName == "Accessory" then
				v.Handle.Transparency = 1
			end
			plr.Character.Humanoid.NameOcclusion = "NoOcclusion"
	end
	elseif TextButton.Text == "UnControl" then
	TextButton.Text = "Control"
	workspace[TextBox.Text].Humanoid.PlatformStand = false
	workspace.Weld1:Remove()
	workspace.Weld2:Remove()
	workspace.Weld3:Remove()
	workspace.Weld4:Remove()
	workspace.Weld5:Remove()
	workspace.Weld6:Remove()
	workspace.Weld7:Remove()
	for i,v in pairs(plr.Character:GetChildren()) do
			if v.ClassName == "Part" then
				v.Transparency = 0
			end
			plr.Character.HumanoidRootPart.Transparency = 1
			if v.ClassName == "Accessory" then
				v.Handle.Transparency = 0
			end
			plr.Character.Humanoid.NameOcclusion = "OccludeAll"
	end
end
end)
 
TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.new(1, 1, 1)
TextBox.Position = UDim2.new(0, 50, 0, 20)
TextBox.Size = UDim2.new(0, 200, 0, 30)
TextBox.Font = Enum.Font.SourceSans
TextBox.FontSize = Enum.FontSize.Size28
TextBox.Text = "Name"
TextBox.TextSize = 25
    print("Clicked")
end)
local Tab = Window:NewTab("ESP")
local AimbotSection = Tab:NewSection("ESP Player")
AimbotSection:NewButton("ESP", "XEOND  X Hub", function(s)
     while wait() do
     pcall(function()
       for i,v in pairs(game.Players:GetChildren()) do
            if not v.Character.Head:FindFirstChild("ESP") then
                local BillboardGui = Instance.new("BillboardGui")
                local TextLabel = Instance.new("TextLabel")
                BillboardGui.Parent = v.Character.Head
                BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
                BillboardGui.Active = true
                BillboardGui.Name = "ESP"
                BillboardGui.AlwaysOnTop = true
                BillboardGui.LightInfluence = 1.000
                BillboardGui.Size = UDim2.new(0, 200, 0, 50)
                BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)
                TextLabel.Parent = BillboardGui
                TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                TextLabel.BackgroundTransparency = 1.000
                TextLabel.Size = UDim2.new(0, 200, 0, 50)
                TextLabel.Font = Enum.Font.GothamBold
                TextLabel.Text = v.Name
                TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
                TextLabel.TextScaled = true
                TextLabel.TextSize = 14.000
                TextLabel.TextStrokeTransparency = 0.000
                TextLabel.TextWrapped = true
            end
        end
    end) 
end
    print("Clicked")
end)
Section:NewButton(".....", ".....", function(s)
--Made by rouxhaver
--super janky
 
player = game:GetService("Players").LocalPlayer
mouse = player:GetMouse()
camera = workspace.CurrentCamera
ts = game:GetService("TweenService")
 
function createtween(part, cframe,ttime)
	local tweeninfo = TweenInfo.new(ttime)
	tween = ts:Create(part, tweeninfo, {CFrame = cframe})
	tween:Play()
	tween.Completed:Wait()
end
 
outline = Instance.new("Highlight")
 
target = nil
 
mouse.Button1Up:Connect(function()
	if mouse.Target then
		local model = mouse.Target:FindFirstAncestorOfClass("Model")
		if model and model:FindFirstChild("Humanoid") then do
				camera.CameraSubject = model.Humanoid
				target = model
			end else
			outline.Parent = nil
		end
	end
end)
 
game:GetService("RunService").RenderStepped:Connect(function()
	if player.Character:FindFirstChild("HumanoidRootPart") then
		player.Character.HumanoidRootPart.Velocity = Vector3.new(0,0,0)
		if target and target:FindFirstChild("HumanoidRootPart") then
			if target.HumanoidRootPart.CFrame.Y + 20 < player.Character.HumanoidRootPart.CFrame.Y then
				tween:Cancel()
			end
		end
	end
	if mouse.Target then
		local model = mouse.Target:FindFirstAncestorOfClass("Model")
		if model and model:FindFirstChild("Humanoid") then do
				outline.Parent = model
			end else
			outline.Parent = nil
		end
	end
end)
 
while task.wait() do
	if target ~= nil and target:FindFirstAncestorOfClass("Workspace") and target ~= player.Character and player.Character:FindFirstChild("HumanoidRootPart") and target:FindFirstChild("HumanoidRootPart") then
		character = player.Character
		hrp = character.HumanoidRootPart
		thrp = target.HumanoidRootPart
		hrp.CFrame = thrp.CFrame * CFrame.Angles(math.rad(90),0,0) + thrp.CFrame.UpVector * -10
	end
	if target ~= nil and target:FindFirstAncestorOfClass("Workspace") and target ~= player.Character and player.Character:FindFirstChild("HumanoidRootPart") and target:FindFirstChild("HumanoidRootPart") then
		character = player.Character
		hrp = character.HumanoidRootPart
		thrp = target.HumanoidRootPart
		rot = thrp.CFrame*CFrame.Angles(math.rad(25),math.rad(25),math.rad(25))
		createtween(hrp, thrp.CFrame * CFrame.Angles(math.rad(90),0,0) + thrp.CFrame.UpVector * 1000000, 100000)
	end
end
    print("Clicked")
end)
Section:NewButton(".....", ".....", function(s)
loadstring(game:HttpGet(('https://pastefy.app/VYIAk3o1/raw'),true))()
    print("Clicked")
end)
Section:NewButton(".....", ".....", function(s)
loadstring(game:HttpGet(('https://pastefy.app/VYIAk3o1/raw'),true))()
    print("Clicked")
end)
Section:NewButton(".....", ".....", function(s)
loadstring(game:HttpGet("https://raw.githubusercontent.com/0Ben1/fe/main/obf_11l7Y131YqJjZ31QmV5L8pI23V02b3191sEg26E75472Wl78Vi8870jRv5txZyL1.lua.txt"))()
    print("Clicked")
end)
Section:NewButton("_-_-_-_-_", "_-_-_-_-_", function(s)
loadstring(game:GetObjects("rbxassetid://6695644299")[1].Source)()
    print("Clicked")
end)
Section:NewButton("-----", "-----", function(s)
loadstring(game:HttpGet('https://pastebin.com/raw/nG0yZs3Z'))()
    print("Clicked")
end)
Section:NewButton("_____", "_____", function(s)
loadstring(game:HttpGet("https://eternityhub.xyz/BetterRoblox/Loader"))()
    print("Clicked")
end)
Section:NewButton("/////", "/////", function(s)
loadstring(game:HttpGet("https://raw.githubusercontent.com/0Ben1/fe./main/L"))()
    print("Clicked")
end)
Section:NewButton("666", "666", function(s)
loadstring(game:HttpGet("https://raw.githubusercontent.com/sinret/rbxscript.com-scripts-reuploads-/main/apanel", true))()
    print("Clicked")
end)
Section:NewButton("Key666", "Key666", function(s)
loadstring(game:HttpGet(('https://raw.githubusercontent.com/manimcool21/Keyboard-FE/main/Protected%20(3).lua'),true))()
    print("Clicked")
end)
Section:NewButton("?????", "?????", function()
Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 4
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed ​​= 20
    print("Clicked")
end)
Section:NewButton("!!!!!", "!!!!!", function(s)
loadstring(game:HttpGet(('https://raw.githubusercontent.com/0Ben1/fe/main/obf_5wpM7bBcOPspmX7lQ3m75SrYNWqxZ858ai3tJdEAId6jSI05IOUB224FQ0VSAswH.lua.txt'),true))()
    print("Clicked")
end)
Section:NewButton("i¡i¡i", "¿¿¿¿", function(s)
loadstring(game:HttpGet("https://raw.githubusercontent.com/ZSIOffical/I-D-K/main/mimic.lua"))()
--Keybinds:
--E = invisible 
--Fist (equip fist/combat) = stop being invisible
--H = Double jump
--F = Normal height
--Q = High Height
--Z = speed- and jump boost (only works when not invisible)
    print("Clicked")
end)

local Tab = Window:NewTab("Fast Attack"")
Section:NewButton("", "XEOND  X Hub", function(s)
local AimbotSection = Tab:NewSection("Fast Attack"")
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/GreenDeno/Venyx-UI-Library/main/source.lua"))()
local venyx = library.new("xerod X Hub | No 1", 5013109572)
 
 
local page = venyx:addPage("Test", 5012544693)
local section1 = page:addSection("Section 1")
local theme = venyx:addPage("Theme", 5012544693)
local colors = theme:addSection("Colors")
 
 
section1:addToggle("Fast Attack", _G.FastAttack, function(value)
_G.FastAttack = value
end)
 
 
local themes = {
Background = Color3.fromRGB(24, 24, 24),
Glow = Color3.fromRGB(0, 0, 0),
Accent = Color3.fromRGB(10, 10, 10),
LightContrast = Color3.fromRGB(20, 20, 20),
DarkContrast = Color3.fromRGB(14, 14, 14),  
TextColor = Color3.fromRGB(255, 255, 255)
}
 
 
for theme, color in pairs(themes) do -- all in one theme changer, i know, im cool
colors:addColorPicker(theme, color, function(color3)
venyx:setTheme(theme, color3)
end)
end
 
-- load
xeondx:SelectPage(xeondx.pages[1], true)
 
 
 
 
 
spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.FastAttack then
            local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
            local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
            Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}
            Combat.activeController.timeToNextAttack = 0
            Combat.activeController.hitboxMagnitude = 120
            Combat.activeController.increment = 3
        end
    end)
end) 
end)
 
 
spawn(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    pcall(function()
        if _G.FastAttack then
            game:GetService'VirtualUser':CaptureController()
            game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
        end
    end)
end) 
end)
    print("Clicked")
end)
for theme, color in pairs(themes) do
    Section:NewColorPicker(theme, "Change your "..theme, color, function(color3)
        Library:ChangeColor(theme, color3)
    end)

local Tab = Window:NewTab("Setting")
Section:NewButton("KeybindText", "KeybindInfo", function(s)
Section:NewKeybind("KeybindText", "KeybindInfo", Enum.KeyCode.F, function()
	Library:ToggleUI()
end)
    print("Clicked")
end)
Section:NewButton("Color", "-", function(s)
Section:NewColorPicker("Color Text", "Color Info", Color3.fromRGB(0,0,0), function(color)
    print(color)
    -- Second argument is the default color
end)
    print("Clicked")
end)
Section:NewButton("Color", "-", function(s)
local colors = {
    SchemeColor = Color3.fromRGB(0,255,255),
    Background = Color3.fromRGB(0, 0, 0),
    Header = Color3.fromRGB(0, 0, 0),
    TextColor = Color3.fromRGB(255,255,255),
    ElementColor = Color3.fromRGB(20, 20, 20)
}
    print("Clicked")
end)
Section:NewButton("Color", "-", function(s)
for theme, color in pairs(themes) do
    Section:NewColorPicker(theme, "Change your "..theme, color, function(color3)
        Library:ChangeColor(theme, color3)
    end)
end

    print("Clicked")
end)
