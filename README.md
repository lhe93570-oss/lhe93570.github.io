# lhe93570.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Scoreboard</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #1a1a2e;
            color: white;
            margin: 0;
        }
        .scoreboard {
            display: flex;
            gap: 40px;
            background: #16213e;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            border: 2px solid #0f3460;
        }
        .team {
            text-align: center;
        }
        h2 { margin-bottom: 10px; color: #e94560; }
        .score {
            font-size: 80px;
            font-weight: bold;
            margin: 20px 0;
            font-family: 'Courier New', Courier, monospace;
        }
        .controls button {
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            background: #0f3460;
            color: white;
            border: none;
            border-radius: 5px;
            transition: 0.2s;
        }
        .controls button:hover { background: #e94560; }
        .reset-container {
            position: absolute;
            bottom: 20px;
        }
        #reset-btn {
            background: #533483;
            border: none;
            color: white;
            padding: 10px 30px;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="scoreboard">
        <div class="team">
            <h2>HOME</h2>
            <div id="home-score" class="score">0</div>
            <div class="controls">
                <button onclick="changeScore('home', 1)">+1</button>
                <button onclick="changeScore('home', -1)">-1</button>
            </div>
        </div>

        <div class="team">
            <h2>AWAY</h2>
            <div id="away-score" class="score">0</div>
            <div class="controls">
                <button onclick="changeScore('away', 1)">+1</button>
                <button onclick="changeScore('away', -1)">-1</button>
            </div>
        </div>
    </div>

    <div class="reset-container">
        <button id="reset-btn" onclick="resetScores()">Reset Match</button>
    </div>

    <script>
        let scores = {
            home: 0,
            away: 0
        };

        function changeScore(team, amount) {
            scores[team] += amount;
            // Prevent negative scores
            if (scores[team] < 0) scores[team] = 0;
            
            document.getElementById(`${team}-score`).innerText = scores[team];
        }

        function resetScores() {
            scores.home = 0;
            scores.away = 0;
            document.getElementById('home-score').innerText = 0;
            document.getElementById('away-score').innerText = 0;
        }
    </script>
</body>
</html>
