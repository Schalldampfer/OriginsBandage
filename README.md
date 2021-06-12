# OriginsBandage
OriginsBandage for 1.0.7 by Schalldampfer

OriginsMod has Triple/Double Bandage, but it's not active in Epochins (DayZ Epoch + OriginsMod combination).
This will add functionality to pack/unpacking bandages and use them.

# Installation:
0. Install [clickActions&deployAnything](https://github.com/oiad/deployAnything) by salival
1. Copy&paste whole scripts folder into `DayZ_Epoch_XX.Map\`.
There will be `DayZ_Epoch_XX.Map\scripts\additions\` folder.
2. Add functions:
Add those codes into your customized `compiles.sqf` or `init.sqf`'s
```sqf
	if (!isDedicated) then {
```
block.
```sqf
	//Bandage
	combineBandage = compile preprocessFileLineNumbers "scripts\additions\combineBandage.sqf";
	unpackBandage = compile preprocessFileLineNumbers "scripts\additions\unpackBandage.sqf";
	fnc_use_item = compile preprocessFileLineNumbers "scripts\additions\use_item.sqf";
```
Note:
fnc_use_item is the function used by OriginsMod items.
If you want to add other objects, check this script.
In default, my `use_item.sqf` will log its usage by other items than Bandages into client RPT file.

3. Add click actions:
Add those codes into `DZE_CLICK_ACTIONS` array in `DayZ_Epoch_XX.Map\scripts\clickActions\config.sqf`
to activate combining and unpacking Bandages.
```sqf
	//Origins Bandage
	["ItemBandage","Combine Bandage","call combineBandage","true"],
	["ItemBandL2","Combine Bandage","call combineBandage","true"],
	["ItemBandL3","Combine Bandage","call combineBandage","true"],
	["ItemBandL2","Unpack Bandage","'ItemBandL2' call unpackBandage","true"],
	["ItemBandL3","Unpack Bandage","'ItemBandL3' call unpackBandage","true"],
```

#Battleye
In scripts.txt, add exceptions (DO NOT REPLACE!) like
```
addMagazine !"for \"_i\" from 1 to _numNewBand3 do {player addMagazine \"ItemBandL3\"};" !"for \"_i\" from 1 to _numNewBand2 do {player addMagazine \"ItemBandL2\"};" !"for \"_i\" from 1 to _numNewBand1 do {player addMagazine \"ItemBandage\"};" !"player removeMagazine _item;\n\n\n{player addMagazine _x;} forEach _output;"
```
for combining and unpacking Bandages.
