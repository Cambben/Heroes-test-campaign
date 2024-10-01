<html><head>
  <title>Empire Conquest: Strategy Game</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
<div id="navbar">
  <a href="#base" class="nav-link active" onclick="changePage('base')">Base</a>
  <a href="#map" class="nav-link" onclick="changePage('map')">Map</a>
  <a href="#army" class="nav-link" onclick="changePage('army')">Army</a>
  <a href="#combat" class="nav-link" onclick="changePage('combat')">Combat</a>
  <a href="#hero" class="nav-link" onclick="changePage('hero')">Hero</a>
</div>

<div id="base" class="page" style="display:block;">
  <h1>Welcome to Your Base</h1>
  <p>Manage your resources and build your empire from here.</p>
  <h2>Resources</h2>
  <p>Food: <span id="food-count">200</span></p>
  <p>Stone: <span id="stone-count">0</span></p>
  <h2>Buildings</h2>
  <button class="building-button" onclick="buildStructure('house')">Build House (10 stone)</button>
  <button class="building-button" onclick="buildStructure('farm')">Build Farm (5 stone)</button>
  <p>Houses: <span id="house-count">0</span></p>
  <p>Farms: <span id="farm-count">3</span></p>
  <div id="farm-production">
    <h3>Farm Production</h3>
    <div class="progress-bar">
      <div id="farm-progress" class="progress"></div>
    </div>
  </div>
</div>

<div id="map" class="page">
  <h1>Control Point Map</h1>
  <p>Send your armies to capture and hold control points. The more points you control, the faster you gather resources!</p>
  <div id="map-container">
    <div id="timer">10:00</div>
    <div id="control-points"></div>
  </div>
  <div id="control-status">
    <p>Points Controlled: <span id="points-controlled">0</span>/5</p>
    <p>Resource Generation: <span id="resource-generation">0</span> food and stone per minute</p>
  </div>
  <div id="army-deployment">
    <h2>Deploy Army</h2>
    <select id="control-point-select">
      <option value="">Select a control point</option>
    </select>
    <input type="number" id="soldiers-to-send" placeholder="Soldiers" min="0">
    <input type="number" id="archers-to-send" placeholder="Archers" min="0">
    <input type="number" id="knights-to-send" placeholder="Knights" min="0">
    <button onclick="sendArmy()">Send Army</button>
  </div>
</div>

<div id="army" class="page">
  <h1>Your Army</h1>
  <p>Recruit and manage your military units here.</p>
  <button class="unit-button" onclick="recruitUnit('soldier')">Recruit Soldier (10 food)</button>
  <button class="unit-button" onclick="recruitUnit('archer')">Recruit Archer (15 food)</button>
  <button class="unit-button" onclick="recruitUnit('knight')">Recruit Knight (25 food)</button>
  <h2>Army Composition</h2>
  <p>Soldiers: <span id="soldier-count">0</span></p>
  <p>Archers: <span id="archer-count">0</span></p>
  <p>Knights: <span id="knight-count">0</span></p>
  <p>Total Army Strength: <span id="army-strength">0</span></p>
</div>

<div id="combat" class="page">
  <h1>Combat Arena</h1>
  <p>Engage in battle with another player's army!</p>
  <button onclick="initiateBattle()">Start Battle</button>
  <div id="battlefield">
    <div class="army-container" id="player-army">
      <h3>Your Army</h3>
    </div>
    <div class="army-container" id="opponent-army">
      <h3>Opponent's Army</h3>
    </div>
  </div>
  <div id="battle-log"></div>
</div>

<div id="hero" class="page">
  <h1>Your Hero</h1>
  <p>Name: <span id="hero-name">Sir Lancelot</span></p>
  <p>Level: <span id="hero-level">1</span></p>
  <p>Experience: <span id="hero-exp">0</span> / <span id="hero-exp-next">100</span></p>
  <div class="progress-bar">
    <div id="hero-exp-bar" class="progress"></div>
  </div>
  <h2>Actions</h2>
  <p>Actions available: <span id="hero-actions">2</span></p>
  <p>Next action in: <span id="hero-action-timer">5:00</span></p>
  <h2>Specializations</h2>
  <div id="hero-specializations">
    <button onclick="addSpecialization('actions')">More Actions</button>
    <button onclick="addSpecialization('production')">Increased Production</button>
    <button onclick="addSpecialization('combat')">Combat Prowess</button>
  </div>
  <h3>Current Specializations</h3>
  <ul id="hero-spec-list"></ul>
</div>

<script src="script.js"></script>
</body></html>
