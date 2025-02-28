# Traffic-Density-prediction
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Traffic Density Prediction Dashboard</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            width: 80%;
            background: white;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-top: 20px;
            border-radius: 10px;
        }
        canvas {
            width: 100% !important;
            height: 400px !important;
        }
        .traffic-light {
            width: 50px;
            height: 150px;
            background: black;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            border-radius: 10px;
            margin-top: 20px;
        }
        .light {
            width: 40px;
            height: 40px;
            background: gray;
            border-radius: 50%;
        }
        .controls {
            margin-top: 20px;
            display: flex;
            gap: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Traffic Density Prediction</h2>
        <canvas id="trafficChart"></canvas>
        <div class="traffic-light" id="trafficLight">
            <div class="light" id="red"></div>
            <div class="light" id="yellow"></div>
            <div class="light" id="green"></div>
        </div>
        <div class="controls">
            <button onclick="changeLight('red')">Red</button>
            <button onclick="changeLight('yellow')">Yellow</button>
            <button onclick="changeLight('green')">Green</button>
        </div>
    </div>

    <script>
        const ctx = document.getElementById('trafficChart').getContext('2d');
        const trafficChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['00:00', '06:00', '12:00', '18:00', '24:00'],
                datasets: [{
                    label: 'Traffic Density',
                    data: [30, 70, 50, 90, 40],
                    borderColor: 'blue',
                    fill: false,
                }]
            },
            options: {
                responsive: true,
                scales: {
                    y: {
                        beginAtZero: true
                    }
                }
            }
        });

        function changeLight(color) {
            document.getElementById('red').style.background = color === 'red' ? 'red' : 'gray';
            document.getElementById('yellow').style.background = color === 'yellow' ? 'yellow' : 'gray';
            document.getElementById('green').style.background = color === 'green' ? 'green' : 'gray';
        }
    </script>
</body>
</html>

