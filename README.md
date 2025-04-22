<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>Zirak</title>
<style>
        @font-face {
            font-family: 'LazyFight';
            src: url('LazyFight.ttf') format('truetype');
            font-weight: normal;
            font-style: normal;
        }
        
        body {
            margin: 0;
            padding: 0;
            background-color: #000;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            cursor: none;
            font-family: Arial, sans-serif;
            transition: background-color 0.5s ease;
        }
        
        body.light-theme {
            background-color: #f5f5f5;
        }
        
        #happiness-slider-container {
            position: relative;
            z-index: 15;
            margin-bottom: 30px;
            width: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        #happiness-label {
            color: #ffd700;
            font-size: 1.2rem;
            margin-bottom: 10px;
            text-align: center;
            transition: color 0.5s ease;
        }
        
        body.light-theme #happiness-label {
            color: #000;
            text-shadow: 0 0 5px #0ff, 0 0 10px #0ff;
        }
        
        #happiness-slider {
            -webkit-appearance: none;
            width: 100%;
            height: 15px;
            border-radius: 5px;
            background: #111;
            outline: none;
            position: relative;
            overflow: visible;
            border: 2px solid #ffd700;
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
            transition: border-color 0.5s ease, box-shadow 0.5s ease;
        }
        
        body.light-theme #happiness-slider {
            border-color: #000;
            box-shadow: 0 0 10px rgba(0, 255, 255, 0.7);
            background: #eee;
        }
        
        #happiness-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #ffd700, #ffec80, #ffd700);
            cursor: pointer;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.8);
            transition: all 0.3s ease;
        }
        
        body.light-theme #happiness-slider::-webkit-slider-thumb {
            background: linear-gradient(45deg, #000, #333, #000);
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.9);
        }
        
        #happiness-slider::-moz-range-thumb {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: linear-gradient(45deg, #ffd700, #ffec80, #ffd700);
            cursor: pointer;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.8);
            transition: all 0.3s ease;
        }
        
        body.light-theme #happiness-slider::-moz-range-thumb {
            background: linear-gradient(45deg, #000, #333, #000);
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.9);
        }
        
        #happiness-slider::-webkit-slider-thumb:hover {
            transform: scale(1.2);
            box-shadow: 0 0 20px rgba(255, 215, 0, 1);
        }
        
        body.light-theme #happiness-slider::-webkit-slider-thumb:hover {
            box-shadow: 0 0 25px rgba(0, 255, 255, 1);
        }
        
        #happiness-slider::-moz-range-thumb:hover {
            transform: scale(1.2);
            box-shadow: 0 0 20px rgba(255, 215, 0, 1);
        }
        
        body.light-theme #happiness-slider::-moz-range-thumb:hover {
            box-shadow: 0 0 25px rgba(0, 255, 255, 1);
        }
        
        #happiness-value {
            color: #ffd700;
            font-size: 1rem;
            margin-top: 10px;
            text-align: center;
            transition: color 0.5s ease;
        }
        
        body.light-theme #happiness-value {
            color: #000;
            text-shadow: 0 0 5px #0ff, 0 0 10px #0ff;
        }
        
        #motivation-message {
            color: #ffd700;
            font-size: 0.9rem;
            margin-top: 5px;
            text-align: center;
            min-height: 20px;
            opacity: 0;
            transition: opacity 0.5s ease, color 0.5s ease;
        }
        
        body.light-theme #motivation-message {
            color: #000;
            text-shadow: 0 0 5px #0ff;
        }
        
        #title-container {
            position: relative;
            z-index: 10;
            display: flex;
            justify-content: center;
        }
        
        .letter {
            font-size: 10vw;
            font-weight: bold;
            text-align: center;
            margin: 0 0.05em;
            cursor: none;
            text-transform: uppercase;
            position: relative;
            background: linear-gradient(to right, #ffd700, #ffec80, #ffd700);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            transition: all 0.3s ease;
            text-shadow: 0 0 5px rgba(255, 215, 0, 0.3);
        }
        
        body.light-theme .letter {
            background: none;
            color: #000 !important;
            -webkit-background-clip: unset;
            background-clip: unset;
            text-shadow: 0 0 3px #00f, 0 0 6px #00f;
    
            background: none;
            color: #000 !important;
            -webkit-background-clip: unset;
            background-clip: unset;
            text-shadow: none;
        }
        
        .letter:hover {
            background: linear-gradient(to right, #4285F4, #34A853, #FBBC05, #EA4335);
            -webkit-background-clip: text;
            background-clip: text;
            text-shadow: 0 0 15px rgba(66, 133, 244, 0.7), 
                         0 0 20px rgba(52, 168, 83, 0.7),
                         0 0 25px rgba(251, 188, 5, 0.7),
                         0 0 30px rgba(234, 67, 53, 0.7);
            transform: scale(1.05);
        }
        
        body.light-theme .letter:hover {
            background: linear-gradient(to right, #ffd700, #ffec80, #ffd700);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent !important;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.7),
                         0 0 20px rgba(255, 215, 0, 0.7),
                         0 0 30px rgba(255, 215, 0, 0.7);
        }
        
        .shine-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, 
                rgba(255, 255, 255, 0.9) 0%, 
                rgba(255, 255, 255, 0) 70%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            opacity: 0;
            pointer-events: none;
            transform: scale(0.5);
            transition: transform 0.5s ease, opacity 0.5s ease;
        }
        
        body.light-theme .shine-overlay {
            background: radial-gradient(circle at center, 
                rgba(0, 0, 0, 0.9) 0%, 
                rgba(0, 0, 0, 0) 70%);
        }
        
        .letter.continuous-shine .shine-overlay {
            opacity: 1;
            transform: scale(1);
            animation: continuous-shine 2s infinite alternate;
        }
        
        @keyframes continuous-shine {
            0% { opacity: 0.7; }
            50% { opacity: 1; }
            100% { opacity: 0.7; }
        }
        
        /* Cursor Styling */
        .cursor {
            width: 10px;
            height: 10px;
            position: absolute;
            z-index: 100;
            pointer-events: none;
            background-color: #ffd700;
            border-radius: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.8);
            transition: background-color 0.5s ease, box-shadow 0.5s ease;
        }
        
        body.light-theme .cursor {
            background-color: #000;
            box-shadow: 0 0 10px rgba(0, 255, 255, 0.8);
        }
        
        .trail-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 99;
        }
        
        .cursor-trail {
            position: absolute;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: #ffd700;
            opacity: 0.8;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 8px rgba(255, 215, 0, 0.6);
            pointer-events: none;
            transition: transform 0.2s ease, opacity 0.3s ease, background-color 0.5s ease, box-shadow 0.5s ease;
        }
        
        body.light-theme .cursor-trail {
            background-color: #000;
            box-shadow: 0 0 8px rgba(0, 255, 255, 0.6);
        }
        
        .glow {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, rgba(255,215,0,0.05) 0%, rgba(0,0,0,0) 70%);
            pointer-events: none;
            z-index: 1;
            transition: background 0.5s ease;
        }

        body.light-theme .glow {
            background: radial-gradient(circle at center, rgba(0,255,255,0.05) 0%, rgba(0,0,0,0) 70%);
        }
        
        #custom-button {
            margin-top: 50px;
            width: 60px;
            height: 60px;
            background: transparent;
            border: 2px solid #ffd700;
            border-radius: 50%;
            position: relative;
            z-index: 15;
            cursor: pointer;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.5);
            transition: all 0.3s ease;
            display: flex;
            justify-content: center;
            align-items: center;
            text-decoration: none;
            overflow: hidden;
        }
        
        body.light-theme #custom-button {
            border-color: #000;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.7);
        }
        
        #custom-button::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,215,0,0.8) 0%, rgba(255,215,0,0) 70%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        body.light-theme #custom-button::before {
            background: radial-gradient(circle, rgba(0,255,255,0.8) 0%, rgba(0,255,255,0) 70%);
        }
        
        #custom-button:hover::before {
            opacity: 0.5;
        }
        
        #custom-button:active::before {
            opacity: 1;
        }
        
        #custom-button:hover {
            transform: scale(1.1);
            box-shadow: 0 0 25px rgba(255, 215, 0, 0.8), 0 0 35px rgba(255, 215, 0, 0.5);
        }
        
        body.light-theme #custom-button:hover {
            box-shadow: 0 0 25px rgba(0, 255, 255, 0.9), 0 0 35px rgba(0, 255, 255, 0.7);
        }
        
        .button-text {
            font-family: 'LazyFight', Arial, sans-serif;
            font-size: 30px;
            color: #ffd700;
            text-shadow: 0 0 5px rgba(255, 215, 0, 0.5);
            transition: all 0.3s ease;
            font-weight: bold;
            position: relative;
            z-index: 2;
        }
        
        body.light-theme .button-text {
            color: #000;
            text-shadow: 0 0 5px rgba(0, 255, 255, 0.7);
        }
        
        #custom-button:hover .button-text {
            color: #fff;
            text-shadow: 0 0 8px rgba(255, 255, 255, 0.8);
            animation: rotate-r 1s infinite linear;
        }
        
        body.light-theme #custom-button:hover .button-text {
            color: #fff;
            text-shadow: 0 0 8px rgba(0, 255, 255, 0.9);
        }
        
        @keyframes rotate-r {
            0% { transform: rotate(0deg); }
            25% { transform: rotate(5deg) scale(1.1); }
            50% { transform: rotate(0deg) scale(1.2); }
            75% { transform: rotate(-5deg) scale(1.1); }
            100% { transform: rotate(0deg); }
        }
        
        /* Quote Styling */
        #quote-container {
            position: relative;
            margin-top: 20px;
            max-width: 80%;
            text-align: center;
            z-index: 10;
        }
        
        #quote-text {
            color: #ffd700;
            font-size: 1.2rem;
            font-style: italic;
            min-height: 3em;
            display: inline;
            transition: color 0.5s ease;
        }
        
        body.light-theme #quote-text {
            color: #000;
            text-shadow: 0 0 5px #0ff;
        }
        
        #quote-author {
            color: #cca000;
            font-size: 1rem;
            margin-top: 10px;
            opacity: 0;
            transition: opacity 1s ease, color 0.5s ease;
        }
        
        body.light-theme #quote-author {
            color: #333;
            text-shadow: 0 0 3px #0ff;
        }
        
        .typing-cursor {
            display: inline-block;
            width: 3px;
            height: 1.2em;
            background-color: #ffd700;
            margin-left: 2px;
            vertical-align: middle;
            animation: blink 1s step-end infinite;
            transition: background-color 0.5s ease;
        }
        
        body.light-theme .typing-cursor {
            background-color: #000;
        }
        
        @keyframes blink {
            from, to { opacity: 1; }
            50% { opacity: 0; }
        }
        
        /* Music Controls */
        #music-controls-container {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 20;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 10px;
        }
        
        #music-controls {
            display: flex;
            align-items: center;
            background: rgba(0,0,0,0.7);
            padding: 10px;
            border-radius: 20px;
            border: 1px solid #ffd700;
            transition: border-color 0.5s ease;
        }
        
        body.light-theme #music-controls {
            background: rgba(255,255,255,0.7);
            border-color: #000;
        }
        
        #file-input-container {
            background: rgba(0,0,0,0.7);
            padding: 10px;
            border-radius: 20px;
            border: 1px solid #ffd700;
            transition: background 0.5s ease, border-color 0.5s ease;
        }
        
        body.light-theme #file-input-container {
            background: rgba(255,255,255,0.7);
            border-color: #000;
        }
        
        #play-pause-btn {
            background: transparent;
            border: 2px solid #ffd700;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #ffd700;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }
        
        body.light-theme #play-pause-btn {
            border-color: #000;
            color: #000;
            box-shadow: 0 0 10px rgba(0, 255, 255, 0.7);
        }
        
        #play-pause-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.8);
        }
        
        body.light-theme #play-pause-btn:hover {
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.9);
        }
        
        #volume-control {
            margin-left: 10px;
            width: 80px;
        }
        
        #volume-slider {
            -webkit-appearance: none;
            width: 100%;
            height: 4px;
            border-radius: 2px;
            background: #333;
            outline: none;
            transition: background 0.5s ease;
        }
        
        body.light-theme #volume-slider {
            background: #ccc;
        }
        
        #volume-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: #ffd700;
            cursor: pointer;
            box-shadow: 0 0 5px rgba(255, 215, 0, 0.8);
            transition: all 0.3s ease;
        }
        
        body.light-theme #volume-slider::-webkit-slider-thumb {
            background: #000;
            box-shadow: 0 0 5px rgba(0, 255, 255, 0.9);
        }
        
        #select-music-btn {
            background: transparent;
            border: 2px solid #ffd700;
            border-radius: 20px;
            padding: 5px 10px;
            color: #ffd700;
            cursor: pointer;
            font-size: 0.8rem;
            transition: all 0.3s ease;
        }
        
        body.light-theme #select-music-btn {
            border-color: #000;
            color: #000;
        }
        
        #select-music-btn:hover {
            background: rgba(255,215,0,0.1);
        }
        
        body.light-theme #select-music-btn:hover {
            background: rgba(0,255,255,0.1);
        }
        
        #music-file {
            display: none;
        }
        
        /* Loading State */
        #loading {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            color: #ffd700;
            font-size: 1.5rem;
            transition: background 0.5s ease, color 0.5s ease;
        }
        
        body.light-theme #loading {
            background: #f5f5f5;
            color: #000;
            text-shadow: 0 0 5px #0ff;
        }
        
        /* Theme Toggle */
        #theme-toggle {
            position: fixed;
            top: 20px;
            left: 20px;
            z-index: 20;
            background: transparent;
            border: 2px solid #ffd700;
            border-radius: 20px;
            padding: 5px 10px;
            color: #ffd700;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        body.light-theme #theme-toggle {
            border-color: #000;
            color: #000;
            text-shadow: 0 0 5px #0ff;
        }
        
        #theme-toggle:hover {
            background: rgba(255,215,0,0.1);
        }
        
        body.light-theme #theme-toggle:hover {
            background: rgba(0,255,255,0.1);
        }
        
        /* Accessibility */
        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border-width: 0;
        }
        
        /* Neon Effect for Letters */
        @keyframes neon-glow {
            0%, 100% {
                text-shadow: 0 0 10px #4285F4, 
                             0 0 20px #34A853, 
                             0 0 30px #FBBC05, 
                             0 0 40px #EA4335;
            }
            25% {
                text-shadow: 0 0 15px #34A853, 
                             0 0 25px #FBBC05, 
                             0 0 35px #EA4335, 
                             0 0 45px #4285F4;
            }
            50% {
                text-shadow: 0 0 20px #FBBC05, 
                             0 0 30px #EA4335, 
                             0 0 40px #4285F4, 
                             0 0 50px #34A853;
            }
            75% {
                text-shadow: 0 0 25px #EA4335, 
                             0 0 35px #4285F4, 
                             0 0 45px #34A853, 
                             0 0 55px #FBBC05;
            }
        }
        
        @keyframes neon-glow-light {
            0%, 100% {
                text-shadow: 0 0 10px #0ff, 
                             0 0 20px #f0f, 
                             0 0 30px #0ff, 
                             0 0 40px #f0f;
            }
            25% {
                text-shadow: 0 0 15px #f0f, 
                             0 0 25px #0ff, 
                             0 0 35px #f0f, 
                             0 0 45px #0ff;
            }
            50% {
                text-shadow: 0 0 20px #0ff, 
                             0 0 30px #f0f, 
                             0 0 40px #0ff, 
                             0 0 50px #f0f;
            }
            75% {
                text-shadow: 0 0 25px #f0f, 
                             0 0 35px #0ff, 
                             0 0 45px #f0f, 
                             0 0 55px #0ff;
            }
        }
        
        .letter.neon-effect {
            animation: neon-glow 3s infinite linear;
            background: linear-gradient(to right, #4285F4, #34A853, #FBBC05, #EA4335);
            -webkit-background-clip: text;
            background-clip: text;
        }
        
        body.light-theme .letter.neon-effect {
            animation: neon-glow-light 3s infinite linear;
            background: linear-gradient(to right, #0ff, #f0f, #0ff, #f0f);
        }
    </style>
</head>
<body>
<div id="loading">Loading...</div>
<button aria-label="Toggle light/dark mode" id="theme-toggle">🌓</button>
<div id="music-controls-container">
<div id="file-input-container">
<button id="select-music-btn">Select Music</button>
<input accept="audio/*" id="music-file" type="file"/>
</div>
<div id="music-controls">
<button aria-label="Play/pause music" id="play-pause-btn">▶</button>
<div id="volume-control">
<label class="sr-only" for="volume-slider">Volume control</label>
<input aria-label="Volume control" id="volume-slider" max="100" min="0" type="range" value="70"/>
</div>
</div>
</div>
<div class="glow"></div>
<div id="happiness-slider-container">
<div id="happiness-label">Happiness Level</div>
<input aria-labelledby="happiness-label" class="slider" id="happiness-slider" max="100" min="0" type="range" value="50"/>
<div id="happiness-value">50% Happy</div>
<div id="motivation-message"></div>
</div>
<div id="title-container">
<div class="letter">
            Z
            <div class="shine-overlay">Z</div>
</div>
<div class="letter">
            I
            <div class="shine-overlay">I</div>
</div>
<div class="letter">
            R
            <div class="shine-overlay">R</div>
</div>
<div class="letter">
            A
            <div class="shine-overlay">A</div>
</div>
<div class="letter">
            K
            <div class="shine-overlay">K</div>
</div>
</div>
<div id="quote-container">
<span id="quote-text"></span>
<span aria-hidden="true" class="typing-cursor"></span>
<div id="quote-author"></div>
</div>
<a aria-label="Visit Roblox profile" href="https://www.roblox.com/de/users/2313695036/profile" id="custom-button" target="_blank">
<div class="button-text">R</div>
</a>
<div aria-hidden="true" class="cursor"></div>
<div aria-hidden="true" class="trail-container"></div>
<audio id="background-music" loop=""></audio>
<script>
        // Loading state
        window.addEventListener('load', function() {
            setTimeout(function() {
                document.getElementById('loading').style.opacity = '0';
                setTimeout(function() {
                    document.getElementById('loading').style.display = 'none';
                }, 500);
            }, 1000);
        });

        const cursor = document.querySelector('.cursor');
        const trailContainer = document.querySelector('.trail-container');
        const glow = document.querySelector('.glow');
        const letters = document.querySelectorAll('.letter');
        const happinessSlider = document.getElementById('happiness-slider');
        const happinessValue = document.getElementById('happiness-value');
        const motivationMessage = document.getElementById('motivation-message');
        const backgroundMusic = document.getElementById('background-music');
        const playPauseBtn = document.getElementById('play-pause-btn');
        const volumeSlider = document.getElementById('volume-slider');
        const themeToggle = document.getElementById('theme-toggle');
        const selectMusicBtn = document.getElementById('select-music-btn');
        const musicFileInput = document.getElementById('music-file');
        
        const maxTrails = 8;
        const trails = [];
        
        let mouseX = 0;
        let mouseY = 0;
        let mousePositions = [];
        let isPlaying = false;
        let animationFrameId = null;
        
        // Set YouTube music (using YouTube embed as audio source)
        function setYouTubeAudio() {
            // Extract video ID from URL
            const youtubeUrl = 'https://www.youtube.com/watch?v=GsrxXOd8sIs';
            const videoId = youtubeUrl.split('v=')[1];
            
            // Create embed URL
            const embedUrl = `https://www.youtube.com/embed/${videoId}?enablejsapi=1&autoplay=0`;
            
            // Create iframe (hidden)
            const iframe = document.createElement('iframe');
            iframe.id = 'youtube-player';
            iframe.style.display = 'none';
            iframe.src = embedUrl;
            document.body.appendChild(iframe);
            
            // This is a simplified approach - in a real implementation you would need
            // to use the YouTube Iframe API for proper control
            console.log('YouTube music loaded. Note: Full control requires YouTube API implementation.');
        }
        
        // Initialize YouTube music
        setYouTubeAudio();
        
        // Motivational messages
        const motivationalMessages = [
            "You're stronger than you think!",
            "Every day is a new beginning.",
            "You've got this! Keep going!",
            "Your potential is limitless.",
            "Tomorrow will be better!",
            "Believe in yourself!",
            "You are amazing just as you are.",
            "Small steps lead to big victories.",
            "Keep your head up, champion!",
            "The best is yet to come."
        ];
        
        // Happiness slider functionality
        happinessSlider.addEventListener('input', function() {
            const value = this.value;
            happinessValue.textContent = `${value}% Happy`;
            
            const hue = Math.min(50 + value/2, 60);
            const lightness = 50 + value/5;
            
            this.style.boxShadow = `0 0 ${10 + value/10}px rgba(255, 215, 0, ${0.5 + value/200})`;
            this.style.borderColor = `hsl(${hue}, 100%, ${lightness}%)`;
        });
        
        happinessSlider.addEventListener('mouseup', function() {
            const value = this.value;
            if (value < 50) {
                const randomMessage = motivationalMessages[Math.floor(Math.random() * motivationalMessages.length)];
                motivationMessage.textContent = randomMessage;
                motivationMessage.style.opacity = "1";
            } else {
                motivationMessage.style.opacity = "0";
            }
        });
        
        happinessSlider.addEventListener('touchend', function() {
            const value = this.value;
            if (value < 50) {
                const randomMessage = motivationalMessages[Math.floor(Math.random() * motivationalMessages.length)];
                motivationMessage.textContent = randomMessage;
                motivationMessage.style.opacity = "1";
            } else {
                motivationMessage.style.opacity = "0";
            }
        });
        
        // Claude-like cursor trail effect with requestAnimationFrame
        function updateCursor() {
            cursor.style.left = mouseX + 'px';
            cursor.style.top = mouseY + 'px';
            
            glow.style.background = `radial-gradient(circle at ${mouseX}px ${mouseY}px, rgba(255,215,0,0.1) 0%, rgba(0,0,0,0) 70%`;
            
            createClaudeTrail();
            
            animationFrameId = requestAnimationFrame(updateCursor);
        }
        
        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
            
            mousePositions.unshift({ x: mouseX, y: mouseY, time: Date.now() });
            
            if (mousePositions.length > 20) {
                mousePositions.pop();
            }
            
            if (!animationFrameId) {
                updateCursor();
            }
        });
        
        function createClaudeTrail() {
            while (trailContainer.firstChild) {
                trailContainer.removeChild(trailContainer.firstChild);
            }
            
            if (mousePositions.length < 2) return;
            
            const now = Date.now();
            
            for (let i = 1; i < Math.min(maxTrails + 1, mousePositions.length); i++) {
                const pos = mousePositions[i];
                const age = now - pos.time;
                
                if (age > 200) continue;
                
                const opacity = Math.max(0, 1 - age / 200);
                const size = Math.max(3, 8 - (i * 0.7));
                
                const trail = document.createElement('div');
                trail.classList.add('cursor-trail');
                trail.style.left = pos.x + 'px';
                trail.style.top = pos.y + 'px';
                trail.style.width = size + 'px';
                trail.style.height = size + 'px';
                trail.style.opacity = opacity;
                
                trailContainer.appendChild(trail);
            }
        }
        
        // Letter hover effects with Gemini colors and neon glow
        letters.forEach(letter => {
            letter.addEventListener('mouseenter', () => {
                letter.classList.add('neon-effect');
                letter.style.transform = 'scale(1.1)';
            });
            
            letter.addEventListener('mouseleave', () => {
                letter.classList.remove('neon-effect');
                letter.style.transform = 'scale(1)';
                letter.style.textShadow = '0 0 5px rgba(255, 215, 0, 0.3)';
            });
            
            // Touch events for mobile
            letter.addEventListener('touchstart', () => {
                letter.classList.add('neon-effect');
                letter.style.transform = 'scale(1.1)';
            });
            
            letter.addEventListener('touchend', () => {
                letter.classList.remove('neon-effect');
                letter.style.transform = 'scale(1)';
            });
        });
        
        // Quote Typing Effect
        const quotes = [
            { text: "The true meaning of life is to plant trees, under whose shade you do not expect to sit.", author: "Nelson Henderson" },
            { text: "Be the change that you wish to see in the world.", author: "Mahatma Gandhi" },
            { text: "He who fights can lose, but he who doesn't fight has already lost.", author: "Bertolt Brecht" },
            { text: "Life is what happens when you're busy making other plans.", author: "John Lennon" },
            { text: "The future belongs to those who believe in the beauty of their dreams.", author: "Eleanor Roosevelt" },
            { text: "The man who moved a mountain was the one who began carrying away small stones.", author: "Chinese Proverb" },
            { text: "The greatest discovery of all time is that a person can change their future by merely changing their attitude.", author: "Oprah Winfrey" },
            { text: "It does not matter how slowly you go as long as you do not stop.", author: "Confucius" },
            { text: "Don't dream your life, live your dream.", author: "Unknown" },
            { text: "Success is the sum of small efforts, repeated day in and day out.", author: "Robert Collier" }
        ];
        
        const quoteText = document.getElementById('quote-text');
        const quoteAuthor = document.getElementById('quote-author');
        let currentQuoteIndex = -1;
        let charIndex = 0;
        let typingTimeout = null;
        
        function typeEffect() {
            if (typingTimeout) {
                clearTimeout(typingTimeout);
            }
            
            currentQuoteIndex = (currentQuoteIndex + 1) % quotes.length;
            charIndex = 0;
            quoteText.textContent = '';
            quoteAuthor.style.opacity = '0';
            
            typeNextChar();
        }
        
        function typeNextChar() {
            const currentQuote = quotes[currentQuoteIndex].text;
            
            if (charIndex < currentQuote.length) {
                quoteText.textContent += currentQuote.charAt(charIndex);
                charIndex++;
                typingTimeout = setTimeout(typeNextChar, 80);
            } else {
                quoteAuthor.textContent = '- ' + quotes[currentQuoteIndex].author;
                quoteAuthor.style.opacity = '1';
                typingTimeout = setTimeout(typeEffect, 5000);
            }
        }
        
        setTimeout(typeEffect, 1000);
        
        // Button effects
        const customButton = document.getElementById('custom-button');
        const buttonText = document.querySelector('.button-text');
        
        customButton.addEventListener('mouseenter', () => {
            buttonText.style.animation = 'rotate-r 1s infinite linear';
        });
        
        customButton.addEventListener('mouseleave', () => {
            buttonText.style.animation = 'none';
        });
        
        customButton.addEventListener('mousedown', () => {
            buttonText.style.transform = 'scale(1.3)';
            buttonText.style.textShadow = '0 0 15px #fff, 0 0 25px #ffd700';
        });
        
        customButton.addEventListener('mouseup', () => {
            buttonText.style.transform = '';
            buttonText.style.textShadow = '';
        });
        
        // Music player functionality
        playPauseBtn.addEventListener('click', () => {
            if (backgroundMusic.src) {
                if (isPlaying) {
                    backgroundMusic.pause();
                    playPauseBtn.textContent = '▶';
                } else {
                    backgroundMusic.play();
                    playPauseBtn.textContent = '❚❚';
                }
                isPlaying = !isPlaying;
            } else {
                alert('Please select a music file first.');
            }
        });
        
        volumeSlider.addEventListener('input', () => {
            backgroundMusic.volume = volumeSlider.value / 100;
        });
        
        // File selection for music
        selectMusicBtn.addEventListener('click', () => {
            musicFileInput.click();
        });
        
        musicFileInput.addEventListener('change', (e) => {
            const file = e.target.files[0];
            if (file) {
                const url = URL.createObjectURL(file);
                backgroundMusic.src = url;
                backgroundMusic.volume = volumeSlider.value / 100;
                
                if (!isPlaying) {
                    backgroundMusic.play();
                    playPauseBtn.textContent = '❚❚';
                    isPlaying = true;
                }
            }
        });
        
        // Theme toggle
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('light-theme');
            
            if (document.body.classList.contains('light-theme')) {
                document.body.style.backgroundColor = '#f5f5f5';
                themeToggle.textContent = '🌙';
                
                // Update cursor glow in light mode
                glow.style.background = `radial-gradient(circle at ${mouseX}px ${mouseY}px, rgba(0,255,255,0.1) 0%, rgba(0,0,0,0) 70%`;
            } else {
                document.body.style.backgroundColor = '#000';
                themeToggle.textContent = '🌓';
                
                // Update cursor glow in dark mode
                glow.style.background = `radial-gradient(circle at ${mouseX}px ${mouseY}px, rgba(255,215,0,0.1) 0%, rgba(0,0,0,0) 70%`;
            }
        });
        
        // Clean up animation frame on unmount
        window.addEventListener('beforeunload', () => {
            if (animationFrameId) {
                cancelAnimationFrame(animationFrameId);
            }
        });
    </script>
</body>
</html>
