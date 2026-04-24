# Developer Logs

---

## 4/23/2026
**Lobby Screen** <br>
- Lobby music <br>
- Simple loading/teleport screen <br>
- Compatible with all input devices <br>
- Supports up to 4 players <br>
- Supports public/private lobbies <br>

![Lobby Computer](https://cdn.discordapp.com/attachments/1496872842363670710/1496875246589055077/image.png?ex=69eb7935&is=69ea27b5&hm=ed8e98efd0006bbd0eddaf5da995b21495ad6c9f95e43605a99f18712d9c7dcd&)

**Maps** <br>
- Basic four sided tiles <br>
- Each side has an Open/Close socket <br>
- Simple tile weights (probability to generate) <br>
- Wave Function Collapse based generation <br>
- Structures can generate between maze beats (the neon white room for example) <br>
- Maze beats can transition without a structure <br>
- Structures can generate inside of mazes (circular pool for example) <br>
- No tile is unreachable from any other tile <br>

![EarlyMapShot1](https://cdn.discordapp.com/attachments/1496872842363670710/1496879439227912312/image.png?ex=69eb7d1c&is=69ea2b9c&hm=91d919d9ff83e2aca0eea3b2e2f956a27217c5c6d89361181f98103524000693&)

![EarlyMapShot2](https://cdn.discordapp.com/attachments/1496872842363670710/1496879439898873906/image.png?ex=69eb7d1d&is=69ea2b9d&hm=ecf318f9105296092f611845e8612f11ec37a9a1303aba0bdb670d806d812874&)

![EarlyMapShot3](https://cdn.discordapp.com/attachments/1496872842363670710/1496879440326561943/image.png?ex=69eb7d1d&is=69ea2b9d&hm=6e1c4793c07af6c5f0cb74ab060fe4ab1d575818bd1a236858222d6122a0b1fb&)

![EarlyMapShot4](https://cdn.discordapp.com/attachments/1496872842363670710/1496879441077604496/image.png?ex=69eb7d1d&is=69ea2b9d&hm=60b4d7c359196881a341b8dcba663d465c52b1b82abcca9eb77f2a8aff3845af&)

![EarlyMapShot5](https://cdn.discordapp.com/attachments/1496872842363670710/1496879441799024762/image.png?ex=69eb7d1d&is=69ea2b9d&hm=62df30477432dc47948cd1b6c78d0a3cf840911a465e6264ebd24459c9cd538d&)

![EarlyMapShot6](https://cdn.discordapp.com/attachments/1496872842363670710/1496879442318983329/image.png?ex=69eb7d1d&is=69ea2b9d&hm=e5ee9c994ff0a0240e6f4ed1228b721dc7dc6eb62cefa3ad3dddc95103d475db&)

**TODO** <br>
- Create detailed tiles with more complex sockets and weights <br>
    - Example, Floor1Open left socket, Floor2Open right socket could be applied to a tile transitioning in between two hallways with different elevation. <br>
- The idea for improvement here is adding more detail per tile, narrowing the hallways, and making the rooms feel open but uniform (with some backrooms style irregularities of course) <br>

![EarlyMapOverview](https://cdn.discordapp.com/attachments/1496872842363670710/1496881034384511026/Screenshot_2026-04-23_at_9.14.03_AM.png?ex=69eb7e99&is=69ea2d19&hm=8add685877f49fc84f4566c570bf799286b7fede1bdeebc9902f164657ce5726&)

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