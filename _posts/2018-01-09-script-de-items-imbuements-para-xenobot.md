---
layout: post
title: 'Script de items imbuements para xenobot'
date: 2018-01-09 11:23:42
categories: script
tags: bot xenobot tibia
featured_image: 'v1515517638/tibia_gjkf1g.jpg'
lead_text: 'Mi script para cambiar de arma cuando hay 2 o mas monstruos en el área.'
seo: 'script, xenobot, aurera global, script xenobot'
---
![Xenobot](https://xenobot.net/images/banner.png)


## Items Imbuements

Por lo general en mis tiempos libres yo juego tibia, ahora estoy en un OT Server que se llama  [Aurea Global](https://aurera-global.com). Ese servidor implementó los **Items Imbuements** que le agregan efectos a los items, el que yo más uso es el **Frost (Powerful)** que convierte el 50% de daño físico en hielo, estos efectos tienen un tiempo de uso de **20 horas**, cada vez que uses el items va restando horas de uso, entonces si vas a cazar y la caza dura **4 horas** cuando regreses te quedarían **solo 16 horas**.

Me dí cuenta que hay momentos en la caza que no necesito el item, como por ejemplo: cuando mato de a dos o menos monstruos.

Como yo uso [Xenobo](https://xenobot.net) se me ocurro la idea de hacer un script que me ayudara a equipar el arma cuando **sí** la necesite, este script ha reducido mis gastos y mantenido drásticamente el tiempo de uso de mis items.


### Script

```lua
--[[
	[v0.1.2.alpha.1] - 03-01-2018
	https://github.com/thevacs 
	
	Copyright(c) 2018 Stack Developer 
	
	Script basado en Aurera Global aurera-global.com
]]--

local sword_1 = 'stonecutter axe' -- Axe normal.
local sword_2 = 'crystalline axe' -- Axe con imbuement.
local monstruos_min = 3 -- Cantidad de monstruos mínima para equipar el axe.

--- Cantidad de monstruos en el área
-- @param monstruoList lista de monstruos
-- @return numero de monstruos en el área
function CantidadMonstruo(monstruoList)
    monstruoList = monstruoList or {} 
    local cantidad = 0
    for i = CREATURES_LOW, CREATURES_HIGH do
        local creature = Creature.GetFromIndex(i)
        if (creature:isValid()) and creature:ID() ~= Self.ID() and not creature:isPlayer() then
            if (creature:isOnScreen() and creature:isVisible() and creature:isAlive()) then
                if(#monstruoList == 0) then
					cantidad = cantidad + 1
                elseif(table.find(monstruoList, creature:Name(), true)) then
                    cantidad = cantidad + 1
                end
            end
        end
    end
    return cantidad
end



Module.New('_AXE', function(module)
	
	swordID_1 = Item.GetItemIDFromDualInput(sword_1)
	swordID_2 = Item.GetItemIDFromDualInput(sword_2)
	
	if(CantidadMonstruo() >= monstruos_min) then
	
		if (Self.Weapon().id ~= swordID_2 and Self.ItemCount(swordID_2) >= 1 and  ( not Self.isInPz() ) ) then
		
			Self.Equip(swordID_2, "weapon")
		
		elseif ( Self.isInPz() or ( not Self.isInFight()) ) then
		
			Self.Dequip("weapon") 
		end
		
	else
		Self.Equip(swordID_1, "weapon")
	end
	
end)
```

![version][version-badge]
![version2][version-xenobot]
![version3][version-tibia]

[version-badge]: https://img.shields.io/badge/Script-v0.1.2.alpha.1-blue.svg
[version-xenobot]: https://img.shields.io/badge/Xenobot-%3D>%2015.11.28.1267-brightgreen.svg
[version-tibia]:https://img.shields.io/badge/Tibia%20Client-%3D%2011-brightgreen.svg

