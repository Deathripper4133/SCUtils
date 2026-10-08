# Squad Community Utility Mod (SCUtils)

SCUtils is a library of simple utility functions.

## Table of Contents
- [0. BP ModInfo](#0-bp_modinfo)
    - [0.1 Basic Information](#01-basic-information)
    - [0.2 Advanced Information](#02-advanced-information)
    - [0.3 Automation](#03-automation)
    - [0.4 Get Functions](#04-get-functions)
- [1. BPC GS Server Info](#1-bpc-gs-server-info)
    - [Server Mod Info Replication](#11-server-mod-info-replication)
    - [Client Mod Info Setup](#12-client-mod-info-setup)
    - [Client Validate Server Mod Info](#13-client-validate-server-mod-infos)
- [2. BPC Player Controller](#2-bpc-player-controller)
    - [Client Report Version Errors](#21-client-report-version-errors)
        - [Mod Version](#21a-mod-version-error)
        - [Game Version](#21b-game-version-error)
- [3. BPFL Utility](#3-bpfl-util)
    - [Logging](#31-logging)
    - [Add Component(s) by Class](#32-add-components-by-class)
    - [Get Server Info Component](#33-get-server-info-component)
    - [Get Controller SCU Component](#34-get-controller-scu-component)
- [Credits](#credits)


## 0. BP ModInfo
The ModInfo BP contains basic information of a mod that'll help users understand what they are using. The main purpose is Mod and Game version compatibility checking. Secondary information can be included such as an in-game widget for configuration of mod data.

#### 0.1 Basic Information 
This info should immediately convey what this mod is and does to the user.
- Mod Icon [ texture reference ]
- Name [ string ] 
- Description [ multi-line string ]
- Version [ string ]
    - Versions are arbitrary and can range from simple integer versions (1,2,3...) to more complex versions (20.8.5+PUBLIC)
- Author [ string ]

>Since versions are arbitrary there is no way to differentiate which version is newer. A simple 'is exactly equal' is used. <br>
>Name, Description, Version and Author must be set otherwise BP will fail to validate.

![Basic Info](https://raw.githubusercontent.com/Deathripper4133/SCUtils/refs/heads/main/.gitassets/Images/0.1-BasicInfo.png "Basic Info")



#### 0.2 Advanced Information
This section contains information that the user does not need directly such as:
- Game Version
- Issues support link 
- Website link
- Settings Widget

>Game version must be set otherwise BP will fail to validate

![Advanced Info](https://raw.githubusercontent.com/Deathripper4133/SCUtils/refs/heads/main/.gitassets/Images/0.2-AdvandedInfo.png "Advanced Info")


#### 0.3 Automation
Some functions have been provided to automate the initial setup process
- Auto Populate
- Clear Values
- Set Game Version

![Automation](https://raw.githubusercontent.com/Deathripper4133/SCUtils/refs/heads/main/.gitassets/Images/0.3-Automation.png "Automation")

#### 0.4 Get Functions
All variables are private and cannot be changed at runtime, as such there are Get functions for those variables.


| Get Function            | Return Type                            |
| ----------------------- | -------------------------------------- |
| Version                 | String                                 |
| Author                  | String                                 |
| Name                    | String                                 |
| Issues                  | String                                 |
| Load Settings Widget    | Class -> User Widget                   |
| Settings Widget         | Soft Class -> User Widget              |
| Website                 | String                                 |
| Mod Icon                | Soft Object -> Texture 2D              |
| Load Mod Icon           | Object -> Texture 2D                   |
| Description             | String                                 |
| Game Version            | String                                 |


## 1. BPC GS Server Info

#### 1.1 Server Mod Info Replication
Server collects and replicates its BP Mod Info Soft Object References + Mod Version String, this allows clients to load the local object and compare the strings
#### 1.2 Client Mod Info Setup
Client collects local BP Mod Infos in order to display information locally in external `Mod Menus`
#### 1.3 Client validate Server Mod Infos
Upon replication of `Server BP Mod Infos` Client will load and compare mod version






## 2. BPC Player Controller

#### 2.1 Client Report Version Errors
Client will build a "report" of any version errors found and replicate up to server
##### 2.1a Mod Version Error
Mod version errors will replicate up to server and notify player
##### 2.1b Game Version Error
Game version errors will <b>NOT</b> replicate to server and will <b>ONLY</b> notify player


## 3. BPFL Util

#### 3.1 Logging
Simple logger that will log to SquadGame.log and PrintString when in PIE. This logger grabs the root folder of the current object and displays it with the accompanied message. Making it easier for Modders/Users to distinguish where the logs are coming from.
#### 3.2 Add Component(s) by Class
Will attempt to add component(s) by the specified Actor Component class if the component does not already exist on the actor
#### 3.3 Get Server Info Component
Returns `BPC_GS_ServerInfo` component. Making it easier to change the component location without affecting existing code.
#### 3.4 Get Controller SCU Component
Returns SCU Component on player controller. Making it easier to change the component location without affecting existing code.



## Credits


- [SCSDK Community](https://discord.gg/yGQGHnXS5m)
- [Deathripper](https://github.com/Deathripper4133) - Project Manager
- [Stepan Sidorovich](https://github.com/stepansi) - Contributor
