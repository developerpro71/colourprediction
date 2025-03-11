<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prediction Pattern</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #3a7bd5, #00d2ff);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            text-align: center;
            background-color: rgba(0, 0, 0, 0.7);
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            width: 350px;
        }
        h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        p {
            font-size: 1.2rem;
            margin-bottom: 40px;
        }
        .input-field {
            margin-bottom: 20px;
            font-size: 1rem;
            padding: 10px;
            width: 100%;
            border-radius: 5px;
            border: 1px solid #ccc;
            color: #333;
        }
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        button {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 1rem;
            cursor: pointer;
            border-radius: 5px;
            transition: all 0.3s ease;
            pointer-events: none; /* Disable buttons initially */
            opacity: 0.5; /* Dim the buttons initially */
        }
        button.active {
            pointer-events: auto;
            opacity: 1; /* Enable and make buttons visible when input is correct */
        }
        button:hover {
            background-color: #45a049;
            transform: scale(1.1);
        }
        button:active {
            background-color: #3e8e41;
        }
        .prediction-result {
            font-size: 1.3rem;
            font-weight: bold;
            margin-top: 20px;
            color: #FFD700;
        }
        .loading {
            font-size: 1.2rem;
            color: #FFF;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Prediction Pattern</h1>
        <p>Enter a 3-digit period number:</p>
        <input id="periodInput" class="input-field" type="number" maxlength="3" placeholder="Enter period number">
        <button id="getPredictionBtn">Get Prediction</button>
        <div id="loadingMessage" class="loading" style="display: none;">Connecting...</div>
        <div class="prediction-result" id="predictionResult"></div>
        <div class="buttons">
            <button id="telegramBtn">Telegram</button>
            <button id="registerBtn">Register ®</button>
        </div>
    </div>

    <script>
        // Pattern for prediction (hidden from the user)
        const predictionPattern = ['BIG', 'SMALL', 'SMALL', 'BIG', 'SMALL', 'BIG', 'BIG'];
        
        // Get elements
        const periodInput = document.getElementById('periodInput');
        const getPredictionBtn = document.getElementById('getPredictionBtn');
        const telegramBtn = document.getElementById('telegramBtn');
        const registerBtn = document.getElementById('registerBtn');
        const predictionResult = document.getElementById('predictionResult');
        const loadingMessage = document.getElementById('loadingMessage');

        // Enable buttons when a valid 3-digit number is entered
        periodInput.addEventListener('input', function() {
            const periodValue = periodInput.value;
            if (periodValue.length === 3 && !isNaN(periodValue)) {
                getPredictionBtn.classList.add('active');
                telegramBtn.classList.add('active');
                registerBtn.classList.add('active');
            } else {
                getPredictionBtn.classList.remove('active');
                telegramBtn.classList.remove('active');
                registerBtn.classList.remove('active');
            }
        });

        // Get Prediction button click handler
        getPredictionBtn.addEventListener('click', function() {
            const periodValue = parseInt(periodInput.value);
            if (periodValue && periodValue >= 100 && periodValue <= 999) {
                // Show "Connecting..." message
                loadingMessage.style.display = 'block';
                predictionResult.style.display = 'none';

                // Simulate a delay (for loading effect)
                setTimeout(function() {
                    // Calculate the prediction based on the pattern
                    const index = (periodValue - 100) % predictionPattern.length;  // Ensure it cycles through the pattern
                    predictionResult.textContent = `Prediction: ${predictionPattern[index]}`;
                    // Hide loading message and show prediction
                    loadingMessage.style.display = 'none';
                    predictionResult.style.display = 'block';
                }, 2000); // 2 seconds delay for the loading effect
            } else {
                predictionResult.textContent = "Invalid period number. Please enter a 3-digit number.";
            }
        });

        // Telegram Button
        telegramBtn.addEventListener('click', function() {
            window.location.href = "https://t.me/GodXAshuraOfficial"; // Telegram link
        });

        // Register Button
        registerBtn.addEventListener('click', function() {
            window.location.href = "https://51game7.in/#/register?invitationCode=538543796865"; // Register link
        });
    </script>
</body>
</html>
