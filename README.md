<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auto Monetag Ads</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: linear-gradient(135deg, #1e2a78, #162544);
            color: #fff;
            margin: 0;
            padding: 0;
        }
        .container {
            margin: 50px auto;
            max-width: 400px;
            padding: 20px;
            background: #2d375a;
            border-radius: 12px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
        }
        h1 {
            font-size: 22px;
            margin-bottom: 10px;
        }
        .progress-circle {
            width: 100px;
            height: 100px;
            background: #444;
            border-radius: 50%;
            margin: 20px auto;
            position: relative;
        }
        .progress-circle span {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 20px;
            color: #fff;
        }
        button {
            padding: 10px 20px;
            margin: 10px 5px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background: #007bff;
            color: white;
        }
        button:disabled {
            background: #555;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Auto MoneTag Ads</h1>
        <p>Watched Ads: <span id="watched-count">0</span></p>
        <p>Earned Points: <span id="earned-points">0</span></p>
        <div class="progress-circle">
            <span id="progress-percent">0%</span>
        </div>
        <button onclick="showAd()">Watch Ad</button>
        <button onclick="startAutoAds()">Auto Show Ads</button>
        <button onclick="stopAutoAds()">Stop Auto Ads</button>
    </div>

    <script>
        let watchedAds = 0;
        let earnedPoints = 0;
        let autoAdsInterval;

        // Show a single ad
        function showAd() {
            displayMonetagAd();
            updateStats(1, 10);
        }

        // Start auto-showing ads
        function startAutoAds() {
            if (!autoAdsInterval) {
                autoAdsInterval = setInterval(() => {
                    displayMonetagAd();
                    updateStats(1, 10);
                }, 3000); // Show ad every 3 seconds
            }
        }

        // Stop auto-showing ads
        function stopAutoAds() {
            clearInterval(autoAdsInterval);
            autoAdsInterval = null;
        }

        // Update stats
        function updateStats(ads, points) {
            watchedAds += ads;
            earnedPoints += points;
            document.getElementById('watched-count').textContent = watchedAds;
            document.getElementById('earned-points').textContent = earnedPoints;

            const percent = Math.min((watchedAds / 10) * 100, 100); // Assume 10 ads = 100%
            document.getElementById('progress-percent').textContent = `${percent}%`;
        }

        // Integrate Monetag Ad
        function displayMonetagAd() {
            // Include Monetag's SDK script
            const script = document.createElement('script');
            script.src = "https://zireemilsoude.net/4/8575212";
            script.onload = () => {
                monetag.init({
                    publisherId: '2711094' // Replace with actual Monetag publisher ID
                });
                monetag.displayAd(); // Display the ad
            };
            document.body.appendChild(script);
        }
    </script>
</body>
</html>
