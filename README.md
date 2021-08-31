# swgoh-tb-data-files #
This repo is a public archive for json files and other resources to help developers create tools for Territory Battle events in Star Wars Galaxy of Heroes. Most data within the files were pulled straight from the game code, the rest were manually added while referncing the provided in-game data.


## platoons.json ##
This file contains the following structure for each territory for all Geo and Hoth Territory Battles.
```js
  {
    "tb_id": <string>   // "id" Territory Battle identifier
    "zone_id": <string>   // "zoneId" Territory identifier
    "unit_type": <string>   // "character" or "ship"
    "area_pos": <string>   // Territory position on map "NA", "Top", "Middle", "Bottom"
    "image": <string>   // Name of provided image to display ability application
    "ability_name": <string>   // "abilityNameKey" of ability being activated or deactivated
    "platoon_1_row_1": [
                         0: <string> // "baseId" of unit in 1st column of the first row
                         1: <string> // "baseId" of unit in 2nd column of the first row
                         2: <string> // "baseId" of unit in 3rd column of the first row
                         3: <string> // "baseId" of unit in 4th column of the first row
                         4: <string> // "baseId" of unit in 5th column of the first row
                       ]
    "platoon_1_row_2": //....
  }
  
  /* Platoon Order
     [ Platoon_1 ]    [ Platoon_4 ]
     [ Platoon_2 ]    [ Platoon_5 ]
     [ Platoon_3 ]    [ Platoon_6 ]
     
     row_1  | 0 | 1 | 2 | 3 | 4 |
     row_2  | 0 | 1 | 2 | 3 | 4 |
     row_3  | 0 | 1 | 2 | 3 | 4 |
  */
```


## territoryBattles.json ##
This file contains all of the most important information from Territory Battles except enemy information. The file contains the following structure.
```js
  "t01D": {   // Key is Territory Battle "id"
    "id": <string>  // Territory Battle "id" repeat
    "nameKey": <string>   // Territory Battle name with planet
    "name": <string>   // Territory Battle name
    "map": <string>   // Territory Battle planet 
    "phaseCount": <integer>   // Number of phases
    "phaseDuration": <integer>   // Time allowed per phase
    "obtainableStars": <integer>   // Total stars obtainable
    "requirements": {
       "unitAlignment": <string>   // Alignment of units used for missions
       "playerLevel": <integer>   // Allowed Player Level to participate
       "guildGP": <integer>   // Required Guild GP
       "units": []   
       "categories": []
    }
    "grantedAbilities": [
      0: {
        "applyTo": {
          "category": <string>   // Heroes or faction
          "units": [
            0: {
              "name": <string>   // Unit in-game name
              "baseId": <string>   // ID used for units in the code
              "image": <string>   // Game file asset name
            }
          ]
        }
        "ability": [
          0: {
            "nameKey": <string>   // Ability name
            "descKey": <string>   // Ability description
            "image": <string>   // Game file asset name
          }
        ]
      }
    ]
    "zones": {
      "phase01_conflict01": {   // Key is territory "zoneId"
        "territoryId": <string>   // Territory identifier
        "territoryName": <string>   // Territory name
        "territoryDesc": <string>   // Territory description
        "combatType": <integer>   // 1 is character 2 is ships
        "starPointsRequirements": {
          1: <integer>   // Points needed for 1 star
          2: <integer>   // Points needed for 2 star
          3: <integer>   // Points needed for 3 star
        }
        "unlockRequirements": { // Requirements to access territory. Object or null
          "territory_completed": [
            0: <string>   // Territory id
          ]
        }
        "combatMissions": {
          "phase01_conflict01_strike01": {   // Key is mission id
            "missionID": <string>   // Mission identifier
            "missionName": <string>   // Mission Name
            "missionDesc": <string>   // Mission description
            "requirements": {
              "categories": [
                0: <string>   // Required unit tags such as factions or alignment 
              ]
              "units": [
                0: {
                  "name": <string>   // Unit in-game name
                  "baseId": <string>   // ID used for units in the code
                  "image": <string>   // Game file asset name
                }
              ]
              "unitRarity": <integer>   // Minimum required unit stars
              "unitLevel": <integer>   // Minimum required unit level
              "gearLevel": <integer>   // Minimum required unit level
              "relicLevel": <integer>   // Minimum required relic level 1 = none, 2 = Relic Level 1
              "galacticPower": <integer>    // Minimum required unit level
            }
            "waves": <integer>   // Number of waves
            "waveRewards": [
              0: <integer>   // Points earned for zero waves
              1: <integer>   // Points earned for comleting 1 wave
              //...
            ]
          }
        }
        "specialMissions": {
          "phase03_conflict03_covert01": {   // Key is mission id
            "missionID": <string>   // Mission identifier
            "missionName": <string>   // Mission Name
            "missionDesc": <string>   // Mission description
            "requirements": {
              "categories": [
                0: <string>   // Required unit tags such as factions or alignment 
              ]
              "units": [
                0: {
                  "name": <string>   // Unit in-game name
                  "baseId": <string>   // ID used for units in the code
                  "image": <string>   // Game file asset name
                }
              ]
              "unitRarity": <integer>   // Minimum required unit stars
              "unitLevel": <integer>   // Minimum required unit level
              "gearLevel": <integer>   // Minimum required unit level
              "relicLevel": <integer>   // Minimum required relic level 1 = none, 2 = Relic Level 1
              "galacticPower": <integer>    // Minimum required unit level
            }
            "waves": <integer>   // Number of waves
            "completionRewards": {
              "name": <string>   // Reward in-game name, shards just display name of unit
              "quantity": <integer>   // Quantity
              "image": <string>   // Game file asset name, shards just give portrait
            }
        
        }
        "platoons": {
          "unitRarity": <integer>   // Required unit stars
          "abilityName": <string>   // Name of Platoon ability
          "abilityDesc": <string>   // Description of platoon ability as seen on Overview screen
          "abilityTierDesc": [   // Breakdown of ability names and descriptions by ability tier
            0: {
              "name": <string>   // Ability name
              "desc": <string>   // Ability description
            }
          ]
          "zoneToApply": [  // The territories the ability will apply to
            0: <string>   // Territory identifier
          ]
          "zoneToApplyImage": <string>   / The image file name for the zones getting the ability
          "missions": {
            "platoon1": {
              "completionRewards": <integer>   // Points earned for applying all units
              "requiredUnits": {
                "row1": [
                  0: {
                    "name": <string>   // Unit in-game name
                    "baseId": <string>   // ID used for units in the code
                    "image": <string>   // Game file asset name                    
                  }
                ]
                "row2":
                "row3":
              }
            }
          }
        }
      }
    }
    "rankRewards": {
      1: {
        "rank": <integer>   // Rank based on number of Stars
        "rewards": [
          0: {
            "name": <string>   // Reward in-game name
            "quantity": <integer>   // Quantity
            "image": <string>   // Game file asset name
          }
        ]
        "boxContents": [
          0: {
            "name": <string>   // Name of gear piece
            "quantity": <integer>   // Value is 0 for reward preview, actual drop quantity is stored server side in-game
            "image": <string>   // Game file asset name for only gear image no background or border
            "color": <string>   // Border color of gear piece
          }
        ]
      }
    }
  }
```
