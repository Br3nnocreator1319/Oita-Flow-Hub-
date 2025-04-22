local OitaFlowHub = {}

local firstSeaMissions = {
    ["Pirate Starter Island"] = {
        ["Derrotar Bandidos"] = {location = Vector3.new(123, 456, 789), requirement = "Nível 0-10"}
    },
    ["Marine Starter Island"] = {
        ["Derrotar Trainees"] = {location = Vector3.new(111, 222, 333), requirement = "Nível 0-10"}
    },
    ["Jungle"] = {
        ["Derrotar Macacos"] = {location = Vector3.new(222, 333, 444), requirement = "Nível 15-20"},
        ["Derrotar Gorilas"] = {location = Vector3.new(555, 666, 777), requirement = "Nível 20-25"},
        ["Derrotar Gorilla King"] = {location = Vector3.new(888, 999, 111), requirement = "Nível 25-30"}
    },
    ["Pirate Village"] = {
        ["Derrotar Piratas"] = {location = Vector3.new(444, 555, 666), requirement = "Nível 30-40"},
        ["Derrotar Brutos"] = {location = Vector3.new(777, 888, 999), requirement = "Nível 40-50"},
        ["Derrotar Bobby"] = {location = Vector3.new(999, 111, 222), requirement = "Nível 50-60"}
    },
    ["Desert"] = {
        ["Derrotar Desert Bandits"] = {location = Vector3.new(333, 444, 555), requirement = "Nível 60-75"},
        ["Derrotar Desert Officers"] = {location = Vector3.new(666, 777, 888), requirement = "Nível 75-90"}
    },
    ["Frozen Village"] = {
        ["Derrotar Snow Bandits"] = {location = Vector3.new(101, 202, 303), requirement = "Nível 90-100"},
        ["Derrotar Snowmen"] = {location = Vector3.new(404, 505, 606), requirement = "Nível 100-110"},
        ["Derrotar Yeti"] = {location = Vector3.new(707, 808, 909), requirement = "Nível 110-120"}
    },
    ["Marine Fortress"] = {
        ["Derrotar Chief Petty Officers"] = {location = Vector3.new(123, 234, 345), requirement = "Nível 120-135"},
        ["Derrotar Vice Admiral"] = {location = Vector3.new(456, 567, 678), requirement = "Nível 135-150"}
    },
    ["Skylands"] = {
        ["Derrotar Sky Bandits"] = {location = Vector3.new(111, 222, 333), requirement = "Nível 150-175"},
        ["Derrotar Dark Masters"] = {location = Vector3.new(444, 555, 666), requirement = "Nível 175-200"}
    },
    ["Prison"] = {
        ["Derrotar Prisoners"] = {location = Vector3.new(101, 202, 303), requirement = "Nível 190-210"},
        ["Derrotar Dangerous Prisoners"] = {location = Vector3.new(404, 505, 606), requirement = "Nível 210-225"},
        ["Derrotar Warden"] = {location = Vector3.new(707, 808, 909), requirement = "Nível 220+"},
        ["Derrotar Chief Warden"] = {location = Vector3.new(101, 202, 303), requirement = "Nível 225+"},
        ["Derrotar Swan"] = {location = Vector3.new(404, 505, 606), requirement = "Nível 225+"}
    },
    ["Colosseum"] = {
        ["Derrotar Toga Warriors"] = {location = Vector3.new(333, 444, 555), requirement = "Nível 225-250"},
        ["Derrotar Gladiators"] = {location = Vector3.new(666, 777, 888), requirement = "Nível 250-275"}
    },
    ["Magma Village"] = {
        ["Derrotar Military Soldiers"] = {location = Vector3.new(123, 234, 345), requirement = "Nível 300-325"},
        ["Derrotar Military Spies"] = {location = Vector3.new(456, 567, 678), requirement = "Nível 325-350"},
        ["Derrotar Magma Admiral"] = {location = Vector3.new(789, 890, 901), requirement = "Nível 350-375"}
    },
    ["Underwater City"] = {
        ["Derrotar Fishman Warriors"] = {location = Vector3.new(111, 222, 333), requirement = "Nível 375-400"},
        ["Derrotar Fishman Commandos"] = {location = Vector3.new(444, 555, 666), requirement = "Nível 400-425"},
        ["Derrotar Fishman Lord"] = {location = Vector3.new(777, 888, 999), requirement = "Nível 425-450"}
    },
    ["Upper Skylands"] = {
        ["Derrotar God's Guards"] = {location = Vector3.new(101, 202, 303), requirement = "Nível 450-475"},
        ["Derrotar Shandas"] = {location = Vector3.new(404, 505, 606), requirement = "Nível 475-500"},
        ["Derrotar Wysper"] = {location = Vector3.new(707, 808, 909), requirement = "Nível 500-525"},
        ["Derrotar Royal Squads"] = {location = Vector3.new(101, 202, 303), requirement = "Nível 525-550"},
        ["Derrotar Royal Soldiers"] = {location = Vector3.new(404, 505, 606), requirement = "Nível 550-575"},
        ["Derrotar Thunder God"] = {location = Vector3.new(707, 808, 909), requirement = "Nível 575-625"}
    },
    ["Fountain City"] = {
        ["Derrotar Galley Pirates"] = {location = Vector3.new(123, 234, 345), requirement = "Nível 625-650"},
        ["Derrotar Galley Captains"] = {location = Vector3.new(456, 567, 678), requirement = "Nível 650-675"},
        ["Derrotar Cyborg"] = {location = Vector3.new(789, 890, 901), requirement = "Nível 675-700"}
    }
}

local activeCodes = {
    ["FIGHT4FRUIT"] = "20 minutos de 2x experiência",
    ["NOEXPLOITER"] = "20 minutos de 2x experiência",
    ["ADMINJACKED"] = "Reset de Estatísticas",
    ["NOOB2ADMIN"] = "20 minutos de 2x experiência",
    ["CODESLIDE"] = "20 minutos de 2x experiência",
    ["fruitconcepts"] = "20 minutos de 2x experiência",
    ["krazydares"] = "20 minutos de 2x experiência",
    ["kittgaming"] = "20 minutos de 2x experiência",
    ["TRIPLEABUSE"] = "20 minutos de 2x experiência",
    ["KITT_RESET"] = "Reset de Estatísticas",
    ["Sub2CaptainMaui"] = "20 minutos de 2x experiência",
    ["Sub2Fer999"] = "20 minutos de 2x experiência",
    ["Enyu_is_Pro"] = "20 minutos de 2x experiência",
    ["Magicbus"] = "20 minutos de 2x experiência",
    ["JCWK"] = "20 minutos de 2x experiência",
    ["Starcodeheo"] = "20 minutos de 2x experiência",
    ["Bluxxy"] = "20 minutos de 2x experiência",
    ["SUB2GAMERROBOT_EXP1"] = "30 minutos de 2x experiência",
    ["Sub2NoobMaster123"] = "20 minutos de 2x experiência",
    ["Sub2UncleKizaru"] = "Reset de Estatísticas",
    ["Sub2Daigrock"] = "20 minutos de 2x experiência",
    ["Axiore"] = "20 minutos de 2x experiência",
    ["TantaiGaming"] = "20 minutos de 2x experiência",
    ["StrawHatMaine"] = "20 minutos de 2x experiência",
    ["Sub2OfficialNoobie"] = "20 minutos de 2x experiência",
    ["TheGreatAce"] = "20 minutos de 2x experiência"
}

return {missions = firstSeaMissions, codes = activeCodes}
local OitaFlowHub = {}

local seaLocations = {
    ["First Sea"] = Vector3.new(100, 200, 300),
    ["Second Sea"] = Vector3.new(400, 500, 600),
    ["Third Sea"] = Vector3.new(700, 800, 900)
}

function OitaFlowHub:TeleportToSea(seaName)
    if seaLocations[seaName] then
        local player = game.Players.LocalPlayer
        if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            player.Character.HumanoidRootPart.CFrame = CFrame.new(seaLocations[seaName])
        end
    end
end

function OitaFlowHub:ShowMissions(missions)
    for island, missionList in pairs(missions) do
        for missionName, details in pairs(missionList) do
            print("- " .. missionName .. " (Local: " .. tostring(details.location) .. ", Requisito: " .. details.requirement .. ")")
        end
    end
end

function OitaFlowHub:ShowCodes(codes)
    for code, description in pairs(codes) do
        print("- Código: " .. code .. " | Benefício: " .. description)
    end
end

function OitaFlowHub:RedeemCode(code, codes)
    if codes[code] then
        print("Resgatando código: " .. code .. " | Benefício: " .. codes[code])
    end
end

function OitaFlowHub:ShowMenu(missions, codes)
    print("[1] Exibir Missões")
    print("[2] Teletransportar para Missão")
    print("[3] Exibir Códigos")
    print("[4] Resgatar Código")
    print("[5] Teletransportar entre Mares")
    print("[6] Sair")

    local option = 1
    if option == 1 then
        self:ShowMissions(missions)
    elseif option == 2 then
        self:TeleportToSea("Second Sea")
    elseif option == 3 then
        self:ShowCodes(codes)
    elseif option == 4 then
        self:RedeemCode("FIGHT4FRUIT", codes)
    elseif option == 5 then
        self:TeleportToSea("Third Sea")
    end
end

return OitaFlowHub
