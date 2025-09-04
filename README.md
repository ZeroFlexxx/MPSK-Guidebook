# Multiplayer Shooter Kit Guidebook

___Getting Started___
___________________

Finding the Player

* Navigate to the Content Drawer and open the Multiplayer_Shooter_Kit folder
* Open the Blueprints folder
* Open the Player folder
* You will find the Character blueprint there called "BP_Player"
* The Character HUD, Controller, Save Object, and Game Modes are also within that folder

Finding the Weapon

* Also within the Blueprints folder you will see a Weapons folder
* The weapon actors are in the Firearms folder
* The third person weapon is "BP_Weapon"
* The first person weapon is "BP_Weapon_FP"

Finding the Levels

* Also within the Blueprints folder you will see a Levels folder
* The Levels are in that folder
* Within that folder there are three other folders
* One has the UI for the Main Menu and Character/Game Menu
* Another has Spawn actors
* And another has custom meshes for the arena in the multiplayer and single player levels

Finding the Animations

* Navigate to the Demo folder
* This folder has both the First Person and Third Person meshes and animations
* It also has demo props, sounds, and weapon assets to use

Finding the Controls

* Navigate to the Input folder
* All input actions and the Input Mapping Context are within this folder
___________________

___Next Steps___
___________________

Finding the Instructions

* Within the Multiplayer_Shooter_Kit folder you should see a blueprint called "Instructional"
* This blueprint is the starting point for learning the rest of the project

<img width="822" height="844" alt="image" src="https://github.com/user-attachments/assets/ab9772e3-b007-4c12-90c9-ff7dcf442004" />

Finally

* Open your character blueprint and ensure you have view of the main event graph:

<img width="727" height="819" alt="image" src="https://github.com/user-attachments/assets/122fd684-9dfd-4392-b11c-b41e7989944b" />

___________________

___Blueprint Fixes___
___________________

Grenade RPC Issue

* Navigate to the Grenade blueprint and open up the Explode event

<img width="1264" height="528" alt="image" src="https://github.com/user-attachments/assets/b671e6a2-69e1-49c0-88f2-9660e7befc48" />

* Copy this exactly as it is shown - the Explode event should be a multicast and the Damage event needs to run on the server

<img width="944" height="742" alt="image" src="https://github.com/user-attachments/assets/cf94e250-c0e6-4ec0-bec6-d1a313a37856" />

* Head over to the Begin Play Event and copy exactly what is shown below

<img width="1046" height="156" alt="image" src="https://github.com/user-attachments/assets/fa591738-3654-4be9-9136-898b4ad1dec7" />

* Now open up the player blueprint and look for the grenad logic

<img width="764" height="731" alt="image" src="https://github.com/user-attachments/assets/29e73057-e4f6-43cf-ad22-63fb30de1681" />

* G calls the Server Event "Throw Grenade", which then calls the Multicast "MC Grenade"
* We use a cooldown timer as an argument, that you can set to whatever value you would like
* Before we call the server event, we perform local changed within the Collapsed Node that says "Throw Grenade then Cool Down

<img width="1013" height="590" alt="image" src="https://github.com/user-attachments/assets/44d7fd92-6780-4f40-9f0d-9ff7ccc1cde7" />

* We call the server first to make sure that everything is in sync for the throw, then we perform a local change for the first person character

<img width="1053" height="584" alt="image" src="https://github.com/user-attachments/assets/6d0fe412-0458-4aa2-9bd3-2dadf90669be" />

* Set Up the First Person sequence as shown below

<img width="1041" height="615" alt="image" src="https://github.com/user-attachments/assets/9435670a-5d66-477f-9fc5-019728c78505" />

* The server event should look as follows

<img width="994" height="261" alt="image" src="https://github.com/user-attachments/assets/9d473490-f340-4a61-b4b6-aee72dd4e42a" />

* Finally set up the multicast for the player

<img width="861" height="298" alt="image" src="https://github.com/user-attachments/assets/7224b2d5-e014-4078-b9c8-30f4c2421d2e" />



