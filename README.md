# MentalUp
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MentalUp</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>MentalUp</h1>
    <button id="toggleNight">🌙 Modo Noche</button>
  </header>

  <main>
    <section id="menu">
      <h2>Selecciona un minijuego</h2>
      <button onclick="startGame('memoria')">Memoria Visual</button>
      <button onclick="startGame('calculo')">Cálculo Exprés</button>
      <button onclick="startGame('logica')">Lógica y Patrones</button>
      <button onclick="startGame('palabras')">Palabras Rápidas</button>
    </section>

    <section id="game" class="hidden">
      <h2 id="gameTitle"></h2>
      <div id="gameContent"></div>
      <button onclick="endGame()">Salir</button>
    </section>

    <section id="stats">
      <h2>Estadísticas</h2>
      <canvas id="weeklyChart"></canvas>
      <div id="badges"></div>
    </section>
  </main>

  <footer>
    <p>© 2025 MentalUp</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

---

### 🎨 style.css
```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background: #f2f2f2;
  color: #333;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header, footer {
  background: #4a90e2;
  color: white;
  padding: 1rem;
  text-align: center;
}

main {
  flex: 1;
  padding: 1rem;
}

button {
  margin: 0.5rem;
  padding: 0.7rem 1rem;
  border: none;
  border-radius: 10px;
  background: #4a90e2;
  color: white;
  font-size: 1rem;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  background: #357ab7;
}

.hidden {
  display: none;
}

/* 🎨 Modo noche */
body.night {
  background: #1a1a1a;
  color: #eee;
}

body.night header, body.night footer {
  background: #222;
}

body.night button {
  background: #555;
}
body.night button:hover {
  background: #777;
}
```

---

### ⚙️ script.js
```javascript
// Botón modo noche
document.getElementById("toggleNight").addEventListener("click", () => {
  document.body.classList.toggle("night");
});

function startGame(type) {
  document.getElementById("menu").classList.add("hidden");
  document.getElementById("game").classList.remove("hidden");

  const gameTitle = document.getElementById("gameTitle");
  const gameContent = document.getElementById("gameContent");
  gameContent.innerHTML = "";

  if (type === "memoria") {
    gameTitle.textContent = "Memoria Visual";
    gameContent.innerHTML = "<p>Recuerda la secuencia de colores...</p>";
  } else if (type === "calculo") {
    gameTitle.textContent = "Cálculo Exprés";
    gameContent.innerHTML = "<p>Resuelve operaciones rápidamente...</p>";
  } else if (type === "logica") {
    gameTitle.textContent = "Lógica y Patrones";
    gameContent.innerHTML = "<p>Encuentra la figura que falta...</p>";
  } else if (type === "palabras") {
    gameTitle.textContent = "Palabras Rápidas";
    gameContent.innerHTML = "<p>Forma palabras con las letras dadas...</p>";
  }
}

function endGame() {
  document.getElementById("menu").classList.remove("hidden");
  document.getElementById("game").classList.add("hidden");
}

// 📊 Gráfica semanal con Chart.js
window.addEventListener("load", () => {
  const ctx = document.getElementById("weeklyChart");
  new Chart(ctx, {
    type: 'line',
    data: {
      labels: ["Lun", "Mar", "Mié", "Jue", "Vie", "Sáb", "Dom"],
      datasets: [{
        label: "Progreso semanal",
        data: [2, 4, 5, 6, 7, 8, 9],
        borderColor: "#4a90e2",
        backgroundColor: "rgba(74,144,226,0.3)",
        fill: true,
        tension: 0.3
}]
    }
  });
});
```
