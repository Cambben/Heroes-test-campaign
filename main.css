<html><head><base href="https://websim.io/"><title>Empire Conquest: Strategy Game</title>
<style>
  body, html {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    height: 100%;
    background-color: #f0f0f0;
  }
  .page {
    display: none;
    padding: 20px;
    height: calc(100% - 60px);
    overflow-y: auto;
  }
  #navbar {
    background-color: #333;
    overflow: hidden;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  #navbar a {
    float: left;
    display: block;
    color: #f2f2f2;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
  }
  #navbar a:hover {
    background-color: #ddd;
    color: black;
  }
  #navbar a.active {
    background-color: #4CAF50;
    color: white;
  }
  #map-container {
    width: 100%;
    height: 500px;
    background-color: #7CFC00;
    position: relative;
    overflow: hidden;
  }
  .control-point {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    position: absolute;
    cursor: pointer;
    transition: all 0.3s;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px;
    font-weight: bold;
    color: white;
    text-shadow: 1px 1px 2px black;
  }
  .control-point.neutral {
    background-color: #888;
  }
  .control-point.player {
    background-color: #4CAF50;
  }
  .control-point.opponent {
    background-color: #f44336;
  }
  #timer {
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 24px;
    background-color: rgba(255, 255, 255, 0.7);
    padding: 5px 10px;
    border-radius: 5px;
  }
  .unit-button, .building-button {
    margin: 10px;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
  }
  .progress-bar {
    width: 100%;
    height: 20px;
    background-color: #e0e0e0;
    border-radius: 10px;
    margin-top: 10px;
  }
  .progress {
    width: 0;
    height: 100%;
    background-color: #4CAF50;
    border-radius: 10px;
    transition: width 0.5s;
  }
  #battlefield {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  .army-container {
    width: 45%;
    background-color: #ddd;
    padding: 10px;
    border-radius: 5px;
  }
  .unit {
    display: inline-block;
    margin: 5px;
    padding: 5px;
    background-color: #fff;
    border-radius: 3px;
  }
  #battle-log {
    margin-top: 20px;
    height: 200px;
    overflow-y: scroll;
    border: 1px solid #ccc;
    padding: 10px;
  }
  #control-status {
    margin-top: 20px;
    font-size: 18px;
  }
  #army-deployment {
    margin-top: 20px;
  }
  #army-deployment input {
    width: 80px;
    margin-right: 10px;
  }
  #control-point-select {
    margin-right: 10px;
  }
</style>
</head>
<body>
<div id="navbar">
  <a href="#base" class="nav-link active" onclick="changePage('base')">Base</a>
  <a href="#map" class="nav-link" onclick="changePage('map')">Map</a>
  <a href="#army" class="nav-link" onclick="changePage('army')">Army</a>
  <a href="#combat" class="nav-link" onclick="changePage('combat')">Combat</a>
</div>

<div id="base" class="page" style="display:block;">
  <h1>Welcome to Your Base</h1>
  <p>Manage your resources and build your empire from here.</p>
  <h2>Resources</h2>
  <p>Food: <span id="food-count">0</span></p>
  <p>Stone: <span id="stone-count">0</span></p>
  <h2>Buildings</h2>
  <button class="building-button" onclick="buildStructure('house')">Build House (10 stone)</button>
  <button class="building-button" onclick="buildStructure('farm')">Build Farm (5 stone)</button>
  <p>Houses: <span id="house-count">0</span></p>
  <p>Farms: <span id="farm-count">0</span></p>
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

<script>
const resources = { food: 0, stone: 0 };
const buildings = { house: 0, farm: 0 };
const army = { soldier: 0, archer: 0, knight: 0 };
const controlPoints = [
  { id: 1, controller: 'neutral', army: { soldier: 0, archer: 0, knight: 0 } },
  { id: 2, controller: 'neutral', army: { soldier: 0, archer: 0, knight: 0 } },
  { id: 3, controller: 'neutral', army: { soldier: 0, archer: 0, knight: 0 } },
  { id: 4, controller: 'neutral', army: { soldier: 0, archer: 0, knight: 0 } },
  { id: 5, controller: 'neutral', army: { soldier: 0, archer: 0, knight: 0 } }
];
let playerControlledPoints = 0;
let timeLeft = 600; // 10 minutes in seconds
let farmProgress = 0;

function changePage(pageId) {
  const pages = document.getElementsByClassName('page');
  for (let page of pages) {
    page.style.display = 'none';
  }
  document.getElementById(pageId).style.display = 'block';
  
  const links = document.getElementsByClassName('nav-link');
  for (let link of links) {
    link.classList.remove('active');
  }
  event.currentTarget.classList.add('active');

  if (pageId === 'map') {
    initializeMap();
    startControlCheck();
  }
  if (pageId !== 'map' && controlPoints.length > 0) {
    controlPoints.forEach(point => {
      point.controller = 'neutral';
      point.army = { soldier: 0, archer: 0, knight: 0 };
    });
    playerControlledPoints = 0;
    updateControlStatus();
  }
}

function initializeMap() {
  const mapContainer = document.getElementById('map-container');
  mapContainer.innerHTML = '<div id="timer">10:00</div><div id="control-points"></div>';
  const controlPointsContainer = document.getElementById('control-points');
  const controlPointSelect = document.getElementById('control-point-select');
  
  controlPoints.forEach((point, index) => {
    const controlPoint = document.createElement('div');
    controlPoint.className = 'control-point neutral';
    controlPoint.style.left = Math.random() * (mapContainer.offsetWidth - 60) + 'px';
    controlPoint.style.top = Math.random() * (mapContainer.offsetHeight - 60) + 'px';
    controlPoint.innerHTML = point.id;
    controlPointsContainer.appendChild(controlPoint);

    const option = document.createElement('option');
    option.value = index;
    option.textContent = `Control Point ${point.id}`;
    controlPointSelect.appendChild(option);
  });
  
  updateControlStatus();
}

function sendArmy() {
  const pointIndex = document.getElementById('control-point-select').value;
  const soldiers = parseInt(document.getElementById('soldiers-to-send').value) || 0;
  const archers = parseInt(document.getElementById('archers-to-send').value) || 0;
  const knights = parseInt(document.getElementById('knights-to-send').value) || 0;

  if (pointIndex === "") {
    alert("Please select a control point.");
    return;
  }

  if (soldiers + archers + knights === 0) {
    alert("Please send at least one unit.");
    return;
  }

  if (soldiers > army.soldier || archers > army.archer || knights > army.knight) {
    alert("You don't have enough units.");
    return;
  }

  army.soldier -= soldiers;
  army.archer -= archers;
  army.knight -= knights;

  controlPoints[pointIndex].army.soldier += soldiers;
  controlPoints[pointIndex].army.archer += archers;
  controlPoints[pointIndex].army.knight += knights;

  controlPoints[pointIndex].controller = 'player';

  updateArmyDisplay();
  updateControlPointDisplay();
  updateControlStatus();

  alert(`Army sent to Control Point ${controlPoints[pointIndex].id}`);
}

function updateControlPointDisplay() {
  const controlPointElements = document.querySelectorAll('.control-point');
  controlPoints.forEach((point, index) => {
    controlPointElements[index].className = `control-point ${point.controller}`;
  });
}

function updateControlStatus() {
  const playerControlledPoints = controlPoints.filter(point => point.controller === 'player').length;
  document.getElementById('points-controlled').textContent = playerControlledPoints;
  const resourceGeneration = playerControlledPoints * 2; // 2 resources per control point per minute
  document.getElementById('resource-generation').textContent = resourceGeneration;
}

let controlCheckInterval;

function startControlCheck() {
  controlCheckInterval = setInterval(checkControlPoints, 300000); // 5 minutes in milliseconds
}

function checkControlPoints() {
  controlPoints.forEach(point => {
    if (point.controller !== 'player') {
      const opponentStrength = Math.floor(Math.random() * 50) + 10; // Random opponent strength
      const playerStrength = point.army.soldier + point.army.archer * 2 + point.army.knight * 3;
      
      if (playerStrength > opponentStrength) {
        point.controller = 'player';
      } else {
        point.controller = 'opponent';
        point.army = { soldier: 0, archer: 0, knight: 0 };
      }
    }
  });

  updateControlPointDisplay();
  updateControlStatus();
}

// Modify the existing updateTimer function
function updateTimer() {
  const minutes = Math.floor(timeLeft / 60);
  const seconds = timeLeft % 60;
  document.getElementById('timer').textContent = 
    `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
  
  if (timeLeft === 0) {
    clearInterval(timerInterval);
    clearInterval(farmInterval);
    clearInterval(resourceInterval);
    clearInterval(controlCheckInterval);
    endGame();
  } else {
    timeLeft--;
    generateResources();
  }
}

// Modify the existing generateResources function
function generateResources() {
  const playerControlledPoints = controlPoints.filter(point => point.controller === 'player').length;
  const resourcesPerPoint = 2 / 60; // 2 resources per minute, divided by 60 for per-second rate
  const generatedResources = playerControlledPoints * resourcesPerPoint;
  resources.food += generatedResources;
  resources.stone += generatedResources;
  updateResourceDisplay();
}

// Initialize game
updateResourceDisplay();
updateArmyDisplay();
const timerInterval = setInterval(updateTimer, 1000);
const farmInterval = setInterval(updateFarmProduction, 1000);
const resourceInterval = setInterval(generateResources, 1000);
</script>
</body></html>
