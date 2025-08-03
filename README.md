# Air-Pollution-Monitor
air pollution monitoring
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Sign Up</title>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-auth.js"></script>

  <style>
    body {
  font-family: Arial, sans-serif;
  background-image: url("pollution-bg.jpg"); /* local image */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}



    .signup-box {
      background: white;
      padding: 40px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
      text-align: center;
      width: 300px;
    }

    .signup-box input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .signup-box button {
      padding: 10px 20px;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      width: 100%;
    }

    .signup-box p {
      margin-top: 10px;
    }

    .signup-box a {
      color: #28a745;
      text-decoration: none;
    }
  </style>
</head>
<body>

  <div class="signup-box">
    <h2>Register</h2>
    <input type="email" id="email" placeholder="Email" required /><br>
    <input type="password" id="password" placeholder="Password" required /><br>
    <input type="password" id="confirmPassword" placeholder="Confirm Password" required /><br>
    <button onclick="signup()">Sign Up</button>
    <p>Already have an account? <a href="login.html">Login here</a></p>
  </div>

  <script>
    // Firebase config – same as your project
    const firebaseConfig = {
      apiKey: "AIzaSyCIajd8dByDlJ5fsI2NDtIktJxqXklTTjo",
      authDomain: "air-pollution-montoring.firebaseapp.com",
      projectId: "air-pollution-montoring",
      databaseURL: "https://air-pollution-montoring-default-rtdb.asia-southeast1.firebasedatabase.app",
      storageBucket: "air-pollution-montoring.appspot.com",
      messagingSenderId: "150287112615",
      appId: "1:150287112615:web:c110401a426819d681be82"
    };

    firebase.initializeApp(firebaseConfig);

    function signup() {
      const email = document.getElementById("email").value.trim();
      const password = document.getElementById("password").value;
      const confirmPassword = document.getElementById("confirmPassword").value;

      if (!email || !password || !confirmPassword) {
        alert("⚠️ Please fill all fields");
        return;
      }

      if (password !== confirmPassword) {
        alert("⚠️ Passwords do not match");
        return;
      }

      firebase.auth().createUserWithEmailAndPassword(email, password)
        .then((userCredential) => {
          alert("✅ Account created! You can now login.");
          window.location.href = "login.html"; // Redirect to login page
        })
        .catch((error) => {
          alert("❌ " + error.message);
        });
    }
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Login Page</title>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-auth.js"></script>

  <style>
    body {
  font-family: Arial, sans-serif;
  background-image: url("pollution-bg.jpg"); /* local image */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}



    .login-box {
      background: white;
      padding: 40px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
      text-align: center;
      width: 300px;
    }

    .login-box input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .login-box button {
      padding: 10px 20px;
      background: #28a745;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      width: 100%;
    }

    .login-box p {
      margin-top: 10px;
    }

    .login-box a {
      color: #007bff;
      text-decoration: none;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>Login</h2>
    <input type="email" id="email" placeholder="Email" /><br>
    <input type="password" id="password" placeholder="Password" /><br>
    <button onclick="login()">Login</button>
    <p>Don't have an account? <a href="signup.html">Register here</a></p>
  </div>

  <script>
    const firebaseConfig = {
      apiKey: "AIzaSyCIajd8dByDlJ5fsI2NDtIktJxqXklTTjo",
      authDomain: "air-pollution-montoring.firebaseapp.com",
      projectId: "air-pollution-montoring",
      databaseURL: "https://air-pollution-montoring-default-rtdb.asia-southeast1.firebasedatabase.app",
      storageBucket: "air-pollution-montoring.appspot.com",
      messagingSenderId: "150287112615",
      appId: "1:150287112615:web:c110401a426819d681be82"
    };

    firebase.initializeApp(firebaseConfig);

    function login() {
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      if (email === "" || password === "") {
        alert("⚠️ Enter both email and password.");
        return;
      }

      firebase.auth().signInWithEmailAndPassword(email, password)
        .then((userCredential) => {
          alert("✅ Login successful!");
          window.location.href = "DASHBOARD.html"; // dashboard
        })
        .catch((error) => {
          alert("❌ " + error.message);
        });
    }
  </script>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Air Quality Dashboard</title>

  <!-- Firebase -->
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-database.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-auth.js"></script>

  <!-- Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #e0f7fa, #fff);
      padding: 20px;
      animation: fadeIn 1s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    h1 {
      text-align: center;
      color: #2c3e50;
    }

    .card-container {
      display: flex;
      justify-content: center;
      gap: 30px;
      flex-wrap: wrap;
      margin-top: 30px;
    }

    .card {
      width: 250px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      padding: 20px;
      text-align: center;
      transition: transform 0.3s ease;
    }

    .card:hover {
      transform: translateY(-5px);
    }

    .value {
      font-size: 40px;
      color: #00796b;
    }

    .label {
      font-size: 18px;
      color: #555;
    }

    #chartContainer {
      max-width: 800px;
      margin: 40px auto;
    }

    button {
      margin: 20px auto;
      display: block;
      padding: 10px 20px;
      border: none;
      background: #e53935;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #c62828;
    }
  </style>
</head>
<body>

  <h1>Air Quality Monitoring Dashboard</h1>

  <div class="card-container">
    <div class="card">
      <div class="value" id="tempValue">-- °C</div>
      <div class="label">Temperature</div>
    </div>
    <div class="card">
      <div class="value" id="humidityValue">-- %</div>
      <div class="label">Humidity</div>
    </div>
    <div class="card">
      <div class="value" id="airValue">-- ppm</div>
      <div class="label">Air Quality</div>
    </div>
  </div>

  <div id="chartContainer">
    <canvas id="aqChart"></canvas>
  </div>

  <button onclick="logout()">Logout</button>

  <script>
  const firebaseConfig = {
    apiKey: "AIzaSyCIajd8dByDlJ5fsI2NDtIktJxqXklTTjo",
    authDomain: "air-pollution-montoring.firebaseapp.com",
    databaseURL: "https://air-pollution-montoring-default-rtdb.asia-southeast1.firebasedatabase.app",
    projectId: "air-pollution-montoring",
    storageBucket: "air-pollution-montoring.appspot.com",
    messagingSenderId: "150287112615",
    appId: "1:150287112615:web:c110401a426819d681be82"
  };

  firebase.initializeApp(firebaseConfig);
  const db = firebase.database();

  firebase.auth().onAuthStateChanged((user) => {
    if (!user) {
      window.location.href = "login.html";
    }
  });

  function logout() {
    firebase.auth().signOut().then(() => {
      alert("Logged out");
      window.location.href = "login.html";
    });
  }

  // Element refs
  const tempEl = document.getElementById("tempValue");
  const humidityEl = document.getElementById("humidityValue");
  const airEl = document.getElementById("airValue");

  // Chart.js setup
  const ctx = document.getElementById('aqChart').getContext('2d');
  const aqChart = new Chart(ctx, {
    type: 'line',
    data: {
      labels: [],
      datasets: [
        {
          label: 'Temperature (°C)',
          data: [],
          backgroundColor: 'rgba(0,150,136,0.1)',
          borderColor: '#009688',
          borderWidth: 2,
          tension: 0.4
        },
        {
          label: 'Air Quality (ppm)',
          data: [],
          backgroundColor: 'rgba(255,82,82,0.1)',
          borderColor: '#e53935',
          borderWidth: 2,
          tension: 0.4
        },
        {
          label: 'Humidity (%)',
          data: [],
          backgroundColor: 'rgba(33,150,243,0.1)',
          borderColor: '#2196f3',
          borderWidth: 2,
          tension: 0.4
        }
      ]
    },
    options: {
      responsive: true,
      scales: {
        x: {
          title: { display: true, text: 'Time' }
        },
        y: {
          title: { display: true, text: 'Value' }
        }
      }
    }
  });

  // Value holders
  let lastTemp = null;
  let lastAir = null;
  let lastHumidity = null;

  // Firebase listeners
  db.ref("/sensor/temperature").on("value", snapshot => {
    const val = snapshot.val();
    tempEl.innerText = val + " °C";
    lastTemp = val;
    tryUpdateChart();
  });

  db.ref("/sensor/air_quality").on("value", snapshot => {
    const val = snapshot.val();
    airEl.innerText = val + " ppm";
    lastAir = val;
    tryUpdateChart();
  });

  db.ref("/sensor/humidity").on("value", snapshot => {
    const val = snapshot.val();
    humidityEl.innerText = val + " %";
    lastHumidity = val;
    tryUpdateChart();
  });

  // Chart update function
  function tryUpdateChart() {
    if (lastTemp !== null && lastAir !== null && lastHumidity !== null) {
      const time = getTime();

      // Maintain max 15 points
      if (aqChart.data.labels.length >= 15) {
        aqChart.data.labels.shift();
        aqChart.data.datasets[0].data.shift();
        aqChart.data.datasets[1].data.shift();
        aqChart.data.datasets[2].data.shift();
      }

      aqChart.data.labels.push(time);
      aqChart.data.datasets[0].data.push(lastTemp);
      aqChart.data.datasets[1].data.push(lastAir);
      aqChart.data.datasets[2].data.push(lastHumidity);
      aqChart.update();
    }
  }

  function getTime() {
    const now = new Date();
    return now.getHours() + ":" + now.getMinutes() + ":" + now.getSeconds();
  }
</script>



</body>
</html>


