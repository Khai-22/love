<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Anniversary, Chel!</title>
    <style>
        :root {
            --primary-yellow: #ffdf00;
            --soft-yellow: #fff9d6;
            --gold: #d4af37;
            --dark-text: #333;
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            font-family: 'Georgia', serif;
            color: var(--dark-text);
            overflow-x: hidden;
        }

        /* Background Image Layout */
        .bg-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* REPLACE WITH YOUR UPLOADED PHOTO FILENAME */
            background: url('photo.jpg'); 
            background-size: cover;
            background-position: center;
            filter: brightness(60%);
            z-index: -1;
        }

        .wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
        }

        /* Glassmorphism Card Style */
        .card {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(8px);
            border: 3px solid var(--primary-yellow);
            border-radius: 20px;
            padding: 40px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            transition: all 0.5s ease;
        }

        h1 {
            color: var(--gold);
            font-size: 2.5rem;
            margin-bottom: 20px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        input[type="text"] {
            width: 80%;
            padding: 12px;
            font-size: 1rem;
            border: 2px solid var(--gold);
            border-radius: 25px;
            outline: none;
            text-align: center;
            margin-bottom: 20px;
        }

        button {
            background-color: var(--primary-yellow);
            color: #000;
            border: 2px solid var(--gold);
            padding: 12px 30px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 25px;
            cursor: pointer;
            transition: transform 0.2s, background-color 0.2s;
        }

        button:hover {
            transform: scale(1.05);
            background-color: var(--gold);
            color: #fff;
        }

        .error-msg {
            color: #d9534f;
            font-weight: bold;
            margin-top: 10px;
            display: none;
        }

        /* Hidden Gift Area */
        #gift-box-area {
            display: none;
        }

        .roses {
            font-size: 3rem;
            margin: 20px 0;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .letter {
            line-height: 1.8;
            font-size: 1.1rem;
            white-space: pre-line;
            text-align: left;
            margin: 20px 0;
            padding: 20px;
            background: rgba(255, 249, 214, 0.5);
            border-left: 4px solid var(--gold);
            border-radius: 5px;
        }

        .audio-controls {
            margin-top: 25px;
            padding-top: 20px;
            border-top: 1px dashed var(--gold);
        }
    </style>
</head>
<body>

    <div class="bg-container"></div>

    <div class="wrapper">
        <!-- STEP 1: Password Lock Screen -->
        <div id="lock-screen" class="card">
            <h1>Happy Anniversary, Chel! 💛</h1>
            <p>To open your gift box, please enter our anniversary date:</p>
            <!-- Tip: Tell her the format you expect, e.g., MM/DD/YYYY or DD-MM-YYYY -->
            <input type="text" id="password-input" placeholder="e.g., MM/DD/YYYY" onkeydown="if(event.key==='Enter') checkPassword()">
            <br>
            <button onclick="checkPassword()">Unlock Gift 🎁</button>
            <p id="error-message" class="error-msg">Incorrect date, my love. Try again! 😘</p>
        </div>

        <!-- STEP 2: The Gift Box Content -->
        <div id="gift-box-area" class="card">
            <h1>For You, Chel 💛</h1>
            
            <!-- Two Yellow Roses -->
            <div class="roses">💛🌹 🌹💛</div>

            <!-- The Letter -->
            <div class="letter">
                Thank God For Her. 
                
                Mi Amor, you are my greatest blessing and my favorite part of every single day. Thank you for being you and for filling my life with so much love and warmth. 
                
                Happy Anniversary! Here's to us, always.
            </div>

            <!-- Audio Player Control -->
            <div class="audio-controls">
                <p style="font-weight: bold; margin-bottom: 10px;">🎵 Press play to listen to our song:</p>
                <!-- REPLACE WITH YOUR UPLOADED AUDIO FILENAME -->
                <audio id="anniversary-music" src="audio.mp3.mp3" preload="auto"></audio>
                <button id="music-btn" onclick="toggleMusic()">▶ Play Music</button>
            </div>
        </div>
    </div>

    <script>
        // CONFIGURATION: Set your anniversary date here exactly how she should type it
        const CORRECT_PASSWORD = "29/12/2020"; 

        function checkPassword() {
            const input = document.getElementById("password-input").value.trim();
            const errorMsg = document.getElementById("error-message");

            if (input === CORRECT_PASSWORD) {
                // Hide lock screen, show gift box
                document.getElementById("lock-screen").style.display = "none";
                document.getElementById("gift-box-area").style.display = "block";
            } else {
                errorMsg.style.display = "block";
            }
        }

        function toggleMusic() {
            const audio = document.getElementById("anniversary-music");
            const btn = document.getElementById("music-btn");

            if (audio.paused) {
                audio.play().catch(error => {
                    alert("Please check that your audio file name is correct in the HTML code!");
                });
                btn.innerHTML = "⏸ Pause Music";
            } else {
                audio.pause();
                btn.innerHTML = "▶ Play Music";
            }
        }
    </script>
</body>
</html>
