# Developer Logs
---
## 4/30/2026
*Input Controller*

Working almost exactly like the ContextActionService. In fact it extends off the functionality of ContextActionService directly. Unlike the built-in service, here we can get analog inputs and have a little more control over the programatic generation of mobile buttons.<br><br>
This library does not require another script to create a listener. All inputs events are handled internally and the values are retrieved with the following methods:<br><br>
```
InputController:GetPressed(action: string): boolean<br>
InputController:GetAnalog(action: string): Vector2<br>
InputController:GetAxis(action: string): number<br>
```
<br>
_Use cases_<br>
GetPressed Whether or not an action is pressed (true or false)<br>
GetAnalog: Return a bidirectional action's value (like Joystick or WASD)<br>
GetAxis: Return the value of an action (key pressed 0 OR 1, trigger pulled any value 0 TO 1)<br>
![Action Script|700](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-30-2026/ActionScript.png)

Custom GUI generated from the config seen above. Custom analog inputs included, additionally the "AuxAction" allows for a custom action to be set when the player drags the virtual joystick far beyond the boundary of the image. In this case (and in most likely cases) this will be "sprint".<br>
_Mobile Layout Pictured Below_<br>
![Mobile Layout|700](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-30-2026/MobileLayout.gif)

---
## 4/27/2026
*Spatial Memory Mechanic*

Spatial memory, in this context, refers to a mechanic where different map tiles can record and playback "memories". These memories are recently recorded player movements stored in a shared database. A players movement will be recorded at random, and only if they meet the minimum movement distance required within the timeframe of capture. There will be a minimum required distance from players when playing these memories back.<br><br>
This mechanic is meant to explore the idea of a physical place holding memories like people do. The player will experience this as a silhouette too far away to distinguish or a shadow in the corner of their eye.<br><br>
Here is a close up of a memory in action (a proper model will replace the black box in the final product):<br>
![Memory Glimpse](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-27-2026/MemoryGlimpse.gif)

Test settings<br>
- MINIMUM_TRAVEL = 3 (Studs)<br>
- RECORD_STEPS = 5 (Positions saved)<br>
- RECORD_TIME = 1 (Seconds)<br>

---

## 4/26/2026
**Time Slip Mechanic**

Time slip is ran every SLIP_CHECK_INTERVAL seconds, on players ISOLATION_DISTANCE studs away from others, with a SLIP_CHANCE percentage based probability of occurring.<br><br>
When a slip does occur a player is place randomly into Past, Present, or Future. They can be placed into the same period they were already.<br><br>
You will only see and collide with objects or players in the same time period as you. If you stick together you won't lose your friends.<br>
![Time Slip Example|140](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-26-2026/TimePeriodSlip.gif)

In the gif above you can see:

- Green orb is a future object<br>
- Orange orb is a present object<br>
- Red orb is a past object<br>

- Test settings<br>
    - ISOLATION_DISTANCE = 0<br>
    - SLIP_CHANCE = 100<br>
    - SLIP_CHECK_INTERVAL = 1<br>
    
---

## 4/23/2026
**Lobby Screen** <br>
- Lobby music <br>
- Simple loading/teleport screen <br>
- Compatible with all input devices <br>
- Supports up to 4 players <br>
- Supports public/private lobbies <br>

![Lobby Computer](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/LobbyComputer.png)

**Maps** <br>
- Basic four sided tiles <br>
- Each side has an Open/Close socket <br>
- Simple tile weights (probability to generate) <br>
- Wave Function Collapse based generation <br>
- Structures can generate between maze beats (the neon white room for example) <br>
- Maze beats can transition without a structure <br>
- Structures can generate inside of mazes (circular pool for example) <br>
- No tile is unreachable from any other tile <br>

![EarlyMapShot1](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot1.png)

![EarlyMapShot2](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot2.png)

![EarlyMapShot3](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot3.png)

![EarlyMapShot4](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot4.png)

![EarlyMapShot5](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot5.png)

![EarlyMapShot6](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/HallShot6.png)

**TODO** <br>
- Create detailed tiles with more complex sockets and weights <br>
    - Example, Floor1Open left socket, Floor2Open right socket could be applied to a tile transitioning in between two hallways with different elevation. <br>
- The idea for improvement here is adding more detail per tile, narrowing the hallways, and making the rooms feel open but uniform (with some backrooms style irregularities of course) <br>

![EarlyMapOverview](https://raw.githubusercontent.com/Sawblade-Entertainment/SawbladeWiki/refs/heads/main/images/4-23-2026/MapOverview.png)

**Level Generation** <br>
- This is an overview of the current prototype level <br>
- From right to left it goes: <br>
    - Story beat 1: Default palette <br>
    - Neon Room: Premade structure <br>
    - Story beat 2: Pool palette <br>
    - Story beat 3: Hotel palette <br>
- This level is generated from a simple config <br>
- Maze beats have a graphing formula that defines their shape <br>
- Exit tile location can be set or randomized <br>
- Beat order can be changed without editing the beat itself, they will automatically possition themselves according to the last beat <br>

**Level Generation Script** <br>
- 1 second without redoes <br>
- 2 seconds with redoes <br>
_A redo occurs when an entrance does not connect to the exit or a structure's is unreachable_

**Notes**
This does not mean the final product will load within a second, as we add more tile types it's expected to take longer. The ideal maximum load time would be 15 seconds. I'm hopeful we can manage to stay well below that.