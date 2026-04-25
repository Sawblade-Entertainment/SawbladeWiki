# Developer Logs

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