getgenv().punch = false
getgenv().tptoworld = false


local library = loadstring(game:HttpGet(('https://raw.githubusercontent.com/AikaV3rm/UiLib/master/Lib.lua')))()

local w = library:CreateWindow("AutoFarm") -- Creates the window

local b = w:CreateFolder("Uses") -- Creates the folder(U will put here your buttons,etc)

b:Label("v1",{
    TextSize = 25; -- Self Explaining
    TextColor = Color3.fromRGB(255,255,255); -- Self Explaining
    BgColor = Color3.fromRGB(69,69,69); -- Self Explaining
    
}) 


b:Toggle("Auto Punch",function(bool)
    getgenv().punch = bool
    print('Auto Punch is: ', bool)
    if bool then
        autopunch()
    end
end)


b:Toggle("Auto TP to World",function(bool)
    getgenv().tptoworld = bool
    print('Auto TP is: ', bool)
    if bool then
        autoTP()
    end
end)


b:DestroyGui()





function autopunch()
spawn(function()
while punch == true do

local args = {
    [1] = {
        [1] = "Activate_Punch"
    }
}

game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
wait()
end
end)
end


function autoTP()
    spawn(function()

    while tptoworld == true do

local args = {
    [1] = {
        [1] = "WarpPlrToOtherMap",
        [2] = "Next"
    }
}

game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
wait()

end
end)
endgest-Punch-Simulator
