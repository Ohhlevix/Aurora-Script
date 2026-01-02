local Library = loadstring(game:HttpGetAsync("https://github.com/ActualMasterOogway/Fluent-Renewed/releases/latest/download/Fluent.luau"))()

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local autoTapEnabled = false
local autoRebirthEnabled = false
local autoEggEnabled = false
local autoUpgradeEnabled = false
local selectedEgg = nil
local autoClaimEnabled = false
local selectedUpgrades = {}

local Window = Library:Window({
    Title = "Tapping Simulator Script",
    SubTitle = "By Duckie - 2026",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Resize = false,
    Theme = "Darker",
    MinimizeKey = Enum.KeyCode.LeftShift
})

local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "home" }),
    Eggs = Window:AddTab({ Title = "Eggs", Icon = "egg" }),
    Misc = Window:AddTab({ Title = "Misc", Icon = "settings" })
}

local AutoFarmSection = Tabs.Main:AddSection("Auto Farm")

AutoFarmSection:Toggle("AutoTap", {
    Title = "Auto Tap",
    Description = "Automatically taps for you",
    Default = false,
    Callback = function(Value)
        autoTapEnabled = Value
        if Value then
            task.spawn(function()
                while autoTapEnabled do
                    pcall(function()
                        local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                        if Event and Event:FindFirstChild("Events") then
                            local TapEvent = Event.Events:GetChildren()[19]
                            if TapEvent then
                                TapEvent:FireServer(true, nil, false)
                            end
                        end
                    end)
                    task.wait(0.0001)
                end
            end)
        end
    end
})

AutoFarmSection:Toggle("AutoRebirth", {
    Title = "Auto Rebirth",
    Description = "Automatically performs rebirth when available",
    Default = false,
    Callback = function(Value)
        autoRebirthEnabled = Value
        if Value then
            task.spawn(function()
                while autoRebirthEnabled do
                    pcall(function()
                        local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                        if Event and Event:FindFirstChild("Events") then
                            local RebirthEvent = Event.Events:GetChildren()[1]
                            if RebirthEvent then
                                RebirthEvent:FireServer()
                            end
                        end
                    end)
                    task.wait(1)
                end
            end)
        end
    end
})

local UpgradesSection = Tabs.Main:AddSection("Auto Upgrades")

local upgradeList = {
    "Tap Multiplier",
    "Coin Multiplier",
    "Lucky Multiplier",
    "Pet Storage",
    "Backpack"
}

local upgradeDropdown = UpgradesSection:Dropdown("SelectUpgrades", {
    Title = "Select Upgrades",
    Values = upgradeList,
    Multi = true,
    Default = {},
    Callback = function(value)
        selectedUpgrades = value
    end
})

UpgradesSection:Toggle("AutoUpgrade", {
    Title = "Auto Buy Upgrades",
    Description = "Automatically purchases selected upgrades",
    Default = false,
    Callback = function(Value)
        autoUpgradeEnabled = Value
        if Value then
            task.spawn(function()
                while autoUpgradeEnabled do
                    if next(selectedUpgrades) then
                        pcall(function()
                            local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                            if Event and Event:FindFirstChild("Events") then
                                for upgradeName, isSelected in pairs(selectedUpgrades) do
                                    if isSelected then
                                        local UpgradeEvent = Event.Events:GetChildren()[5]
                                        if UpgradeEvent then
                                            UpgradeEvent:FireServer(upgradeName)
                                            task.wait(0.5)
                                        end
                                    end
                                end
                            end
                        end)
                    end
                    task.wait(2)
                end
            end)
        end
    end
})

local EggsSection = Tabs.Eggs:AddSection("Auto Hatch")

local eggList = {
    "Basic Egg",
    "Forest Egg",
    "Beach Egg",
    "Desert Egg",
    "Space Egg",
    "Candy Egg",
    "Lava Egg",
    "Snow Egg",
    "Fantasy Egg",
    "Void Egg"
}

local eggDropdown = EggsSection:Dropdown("SelectEgg", {
    Title = "Select Egg",
    Values = eggList,
    Multi = false,
    Default = "Basic Egg",
    Callback = function(Value)
        selectedEgg = Value
    end
})

EggsSection:Toggle("AutoHatchEgg", {
    Title = "Auto Hatch Eggs",
    Description = "Automatically hatches selected egg",
    Default = false,
    Callback = function(Value)
        autoEggEnabled = Value
        if Value then
            task.spawn(function()
                while autoEggEnabled do
                    if selectedEgg then
                        pcall(function()
                            local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                            if Event and Event:FindFirstChild("Events") then
                                local EggEvent = Event.Events:GetChildren()[10]
                                if EggEvent then
                                    EggEvent:FireServer(selectedEgg, 1)
                                end
                            end
                        end)
                    end
                    task.wait(0.5)
                end
            end)
        end
    end
})

local PetSection = Tabs.Eggs:AddSection("Pet Management")

PetSection:Toggle("AutoEquipBest", {
    Title = "Auto Equip Best Pets",
    Description = "Automatically equips your strongest pets",
    Default = false,
    Callback = function(Value)
        if Value then
            task.spawn(function()
                pcall(function()
                    local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                    if Event and Event:FindFirstChild("Events") then
                        local EquipEvent = Event.Events:GetChildren()[12]
                        if EquipEvent then
                            EquipEvent:FireServer("EquipBest")
                        end
                    end
                end)
            end)
        end
    end
})

PetSection:Button({
    Title = "Craft All Pets",
    Description = "Combines all pets of same tier",
    Callback = function()
        pcall(function()
            local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
            if Event and Event:FindFirstChild("Events") then
                local CraftEvent = Event.Events:GetChildren()[15]
                if CraftEvent then
                    CraftEvent:FireServer("CraftAll")
                end
            end
        end)
    end
})

local CodesSection = Tabs.Misc:AddSection("Codes")

local codes = {
    "90M", "70M", "65M", "60M", "55M", "50M", "40M", "35M", "30M",
    "VOID", "MAGMA", "FANTASY", "SPACE", "SPOOKY",
    "UPD23", "UPD20", "UPD19", "UPD18", "UPD17", "UPD16", "UPD15", "UPD12",
    "RELEASE", "TESTING", "UPDATE2", "UPDATE3", "UPDATE4",
    "SECRETFREEPETCODE", "FREEPETCODE2", "FREEPETCODE123",
    "IDIDNTEXPECTYOUTOBEABLETOREADBACKWARDS"
}

CodesSection:Button({
    Title = "Redeem All Codes",
    Description = "Redeems all available codes",
    Callback = function()
        task.spawn(function()
            for _, code in ipairs(codes) do
                pcall(function()
                    local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                    if Event and Event:FindFirstChild("Events") then
                        local CodeEvent = Event.Events:GetChildren()[8]
                        if CodeEvent then
                            CodeEvent:FireServer(code)
                            task.wait(0.5)
                        end
                    end
                end)
            end
        end)
    end
})

CodesSection:Toggle("AutoClaimDaily", {
    Title = "Auto Claim Daily Rewards",
    Description = "Automatically claims daily rewards",
    Default = false,
    Callback = function(Value)
        autoClaimEnabled = Value
        if Value then
            task.spawn(function()
                while autoClaimEnabled do
                    pcall(function()
                        local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                        if Event and Event:FindFirstChild("Events") then
                            local ClaimEvent = Event.Events:GetChildren()[20]
                            if ClaimEvent then
                                ClaimEvent:FireServer()
                            end
                        end
                    end)
                    task.wait(60)
                end
            end)
        end
    end
})

local MiscSection = Tabs.Misc:AddSection("Misc Features")

MiscSection:Button({
    Title = "Claim All Islands",
    Description = "Unlocks all available islands",
    Callback = function()
        task.spawn(function()
            local islands = {
                "Flower Island", "Beach Island", "Desert Island", 
                "Space Island", "Candy Island", "Lava Island", 
                "Snow Island", "Fantasy Island", "Void Island"
            }
            for _, island in ipairs(islands) do
                pcall(function()
                    local Event = ReplicatedStorage:FindFirstChild("73bd9f38-0e90-4df4-bdd9-dfc8d55ec1e1")
                    if Event and Event:FindFirstChild("Events") then
                        local IslandEvent = Event.Events:GetChildren()[3]
                        if IslandEvent then
                            IslandEvent:FireServer(island)
                            task.wait(0.3)
                        end
                    end
                end)
            end
        end)
    end
})

MiscSection:Toggle("AntiAFK", {
    Title = "Anti AFK",
    Description = "Prevents you from being kicked for inactivity",
    Default = true,
    Callback = function(Value)
        if Value then
            local VirtualUser = game:GetService("VirtualUser")
            LocalPlayer.Idled:Connect(function()
                VirtualUser:CaptureController()
                VirtualUser:ClickButton2(Vector2.new())
            end)
        end
    end
})

Window:SelectTab(1)
