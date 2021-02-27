# Man
Manual for GTFO Data blocks

## Writing Guide
- data block order is alphabetical
- json objects are in chronological order of typical generation
- A Json object is documented as a declared C variable with single line comment
- `List Blocks` typically describes what the data block file is for
- Boolean comments are written as a question to describe what it wants
- enums and vectors have lists below their declaration with optional comments for each value
- when persistentID are declared a comment should say what data block typically uses it
- when persistentID are required for UINT32 say what file it comes from

## GameData_ArchetypeDataBlock_bin

List Headers //unused

List Blocks //Contains display text and weapon settings such as damage and shot types

String PublicName //Name of weapon, displayed in loadout selection

String Description //Description of weapon, displayed in loadout selection

eWeaponFireMode FireMode //Determines how the weapon or sentry will shoot
- 0 - Semi
- 1 - Burst
- 2 - Auto
- 3 - SemiBurst
- 4 - SentryGunSemi
- 5 - SentryGunAuto
- 6 - SentryGunBurst
- 7 - SentryGunShotgunSemi

UInt32 RecoilDataID //pulls recoil settings from GameData_PlayerDataBlock_bin.json

Single Damage //Base damage of weapon per bullet

Vector2 DamageFalloff //When damage should weaken based on distance. 100 units is the raycast limit
- x //Start of falloff
- y //End of falloff

Single StaggerDamageMulti //Multiplies stagger dealt to an enemy

Single PrecisionDamageMulti //Multiplies damage done to an enemies weakspot, such as the head. Not to be mistaken with the rear of an enemy. Charger variants do not have weakspots

Int32 DefaultClipSize //The amount of shots a weapon has in a clip before having to reload

Single DefaultReloadTime //Time it takes to reload

Single CostOfBullet //Calculates reserve ammo based on settings in GameData_PlayerDataBlock_bin.json (expand this)

Single ShotDelay //Time between shots

Boolean PiercingBullets //Should a bullet pierce enemies? A bullet can pierce an enemy only once

Int32 PiercingDamageCountLimit //How many enemies to pierce. Maximum of 5. The first enemy hit will count as a pierce, set greater than 1 for it's intended effect.

Single HipFireSpread //Adjust cone of bullet spread when hip firing

Singlee AimSpread //Adjust cone of bullet spread when using Aim Down Sights

Single EquipTransitionTime //Total time it takes to pull a weapon out when switching

WeaponAnimSequenceItem EquipSequence //Contains TriggerTime, Type and StringData

Single TriggerTime //(expand this)

eWeaponAnimSequenceItemType Type //(expand this)
- 0 - StockAnim
- 1 - RightHandAnim
- 2 - WeaponMovementAnim
- 3 - FrontPartAnim
- 4 - LeftHandAnim
- 5 - LeftHandMagAnim
- 6 - ReceiverAnim
- 7 - Sound
- 8 - DoUpdateAmmo
- 9 - Empty

String StringData //(expand this)

Single AimTransitionTime //Total time it takes to Aim Down Sights

WeaponAnimSequeenceItem AimSequence //Contains TriggerTime and Type

Single TriggerTime //(expand this)

eWeaponAnimSequenceItemType Type //(expand this)
- 0 - StockAnim
- 1 - RightHandAnim
- 2 - WeaponMovementAnim
- 3 - FrontPartAnim
- 4 - LeftHandAnim
- 5 - LeftHandMagAnim
- 6 - ReceiverAnim
- 7 - Sound
- 8 - DoUpdateAmmo
- 9 - Empty

Single BurstDelay //How long to charge until shooting

Int32 BurstShotCount //How many bullets are shot in sequence

Int32 ShotgunBulletCount //How many bullets are shot ALL AT ONCE

Int32 ShotgunConeSize //Adjust maximum cone size of bullet spread

Int32 ShotgunBulletSpread //How tight do the bullets stay together

Single SpecialChargeupTime //(expand this)

Single SpecialCooldownTime //(expand this)

Single SpecialSemiBurstCountTimeout //(expand this)

Single Sentry_StartFireDelay //How long it takes until the sentry begins shooting a target

Single Sentry_RotationSpeed //How quickly a sentry will rotate towards a target

Single Sentry_DetectionMaxRange //How far away a sentry will aim at a target

Single Sentry_DetectionMaxAngle //How much the sentry will rotate to get a target

Boolean Sentry_FireTowardsTargetInsteadOfForward //(expand this)

String name //internal name, not displayed anywhere

Boolean internalEnabled //Is this usable by the client?

UInt32 persistentID //Used in GameData_PlayerOfflineGearDataBlock_bin.json

## GameData_BigPickupDistributionDataBlock_bin

List Headers //Unused

List Blocks //Contains settings for key items such as batteries, turbines and Babies

Int32 SpawnsPerZone //How many of these will spawn in a zone

BigPickupSpawnData SpawnData //Contains ItemID and Weight

UInt32 ItemID //(expand this)

Single Weight //(expand this)

String name //internal name, not displayed anywhere

Boolean internalEnabled //Is this usable by the client?

UInt32 persistentID //(expand this)

## GameData_ChainedPuzzleDataBlock_bin

List Headers //Unused

List Blocks //Contains alarm settings such as what scans to use and how enemies spawn

String PublicAlarmName //Text displayed when looking at doors typically

Boolean TriggerAlarmOnActivate //Should enemies spawn

UInt32 SurvivalWaveSettings //persistentID from GameData_SurvivalWaveSettingsDataBlock_bin.json

UInt32 SurvivalWavePopulation //persistentID from GameData_SurvivalWavePopulationDataBlock_bin.json

Boolean DisableSurvivalWaveOnComplete //Should enemies stop spawning

Boolean UseRandomPositions //(expand this)

Single WantedDistanceFromStartPos //How far away the inital scan is

Single WantedDistanceBetweenPuzzleComponents //How far to spread scans out

ChainedPuzzleComponent ChainedPuzzle //Contains PuzzleType

UInt32 PuzzleType //persistentID from GameData_ChainedPuzzleTypeDataBlock_bin.json

Boolean OnlyShowHUDWhenPlayerIsClose //(expand this)

UInt32 AlarmSoundStart //(expand this) Pulls from "GTFO\GTFO_Data\StreamingAssets\GeneratedSoundBanks\Wwise_IDs.cs"

UInt32 AlarmSoundStop //(expand this) Pulls from "GTFO\GTFO_Data\StreamingAssets\GeneratedSoundBanks\Wwise_IDs.cs"

String name //internal name, not displayed anywhere

Boolean internalEnabled //Is this usable by the client

UInt32 persistentID //(expand this)

## GameData_ChainedPuzzleTypeDataBlock_bin

List Headers //Unused

List Blocks //Contains scan types for alarms

String Prefab //Pulls from your mom

String name //internal name, not displayed anywhere

UInt32 persistentID //Used in GameData_ChainedPuzzleDataBlock_bin.json

## GameData_CommodityDataBlock_bin

List Headers //Unused

List Blocks //Currently unused

String PublicName //(expand this)

eCommodityType Type //(expand this)
- 0 - LiquidSample
- 1 - Data
- 8 - Artifact
- 9 - PhysicalSample

eCommodityPackSize PackSize //(expand this)
- 3 - Small
- 4 - Medium
- 5 - Large

UInt32 Item //(expand this)

ePlayfabCurrency PlayfabCurrency //(expand this)
- 7 - CurrA
- 8 - CurrB
- 9 - CurrC

Int32 PlayfabCurrencyValue //(expand this)

String name //internal name, not displayed anywhere

UInt32 persistentID //(expand this)

## GameData_ComplexResourceSetDataBlock_bin

List Headers //Unused

List Blocks //(expand this)

Complex ComplexType //(expand this)
- 5 - Mining
- 6 - Service
- 7 - Tech

SubComplex PrimareSubComplexUsed //(expand this)
- 0 - Refinery
- 1 - Storage
- 2 - DataCenter
- 3 - Lab
- 4 - All
- 5 - Maintenance
- 6 - Mining_Reactor
- 7 - Plug_SubComplex_Transition
- 8 - Tech_Reactor
- 9 - DigSite

AssetBundleName BundleName //(expand this)
- 2 - None
- 3 - Complex_Shared
- 4 - Complex_Mining
- 5 - Complex_Tech
- 6 - Complex_Service
- 7 - Startup
- 8 - Gear_Weapon_Front = 20
- 9 - Gear_Weapon_Receiver = 30
- 10 - Gear_Weapon_Stock = 40
- 11 - Gear_Weapon_Sight = 50
- 12 - Gear_Weapon_Mag = 60
- 13 - Gear_Weapon_Flashlight = 70
- 14 - Gear_Tool_Main = 80
- 15 - Gear_Tool_Grip = 90
- 16 - Gear_Tool_Delivery = 100
- 17 - Gear_Tool_Payload = 110
- 18 - Gear_Tool_Targeting = 120
- 19 - Gear_Tool_Screen = 130
- 20 - Gear_Melee_Head = 140
- 21 - Gear_Melee_Neck = 150
- 22 - Gear_Melee_Handle = 160
- 23 - Gear_Melee_Pommel = 170
- 24 - Gear_Material = 200
- 25 - Enemies = 300

LevelGenConfig LevelGenConfig //Contains GridSize, CellDimension, AltitudeOffset, TransitionDirection and LevelProgression

Int32 GridSize //(expand this)

Single CellDimension //(expand this)

Single AltitudeOffset //(expand this)

LG_FloorTransitionDirection TransitionDirection //(expand this)
- 5 - FloorUp
- 6 - FloorDown

LG_LevelProgression LevelProgression //(expand this)
- 2 - StartLevel
- 3 - MidLevel
- 4 - EndLevel

ResourceData ResourceData //Contains Prefab, SubComplex and Shard

String Prefab //(expand this)

SubComplex SubComplex //(expand this)
- 0 - Refinery
- 1 - Storage
- 2 - DataCenter
- 3 - Lab
- 4 - All
- 5 - Maintenance
- 6 - Mining_Reactor
- 7 - Plug_SubComplex_Transition
- 8 - Tech_Reactor
- 9 - DigSite

AssetBundleShard Shard //(expand this)
- 27 - S1
- 28 - S2
- 29 - S3
- 30 - S4
- 31 - S5
- 32 - S6
- 33 - S7
- 34 - S8
- 35 - S9
- 36 - S10
- 37 - S11
- 38 - S12
- 39 - S13
- 40 - S14
- 41 - S15
- 42 - S16
- 43 - S17
- 44 - S18
- 45 - S19
- 46 - S20

String name //internal name, not displayed anywhere

Boolean internalEnabled //Is this usable by the client?

UInt32 persistentID //(expand this)

## GameData_ConsumableDistributionDataBlock_bin
