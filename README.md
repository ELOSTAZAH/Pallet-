<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Palette Zone - Educational Books for Autistic Children</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Comic Sans MS', 'Marker Felt', 'Nunito', sans-serif;
        }

        :root {
            --canary-yellow: #fff8d0;
            --dark-blue: #0a0a2a;
            --mint-green: #a0e8d0;
            --purple: #e0b0ff;
            --pink: #ffd1dc;
            --baby-blue: #d4f0ff;
            --olive: #80c0a0;
            --lavender: #d6c2ff;
            --peach: #ffd8c9;
            --sky-blue: #a8d8ff;
            --light-pink: #ffcce0;
            --light-purple: #e8d0ff;
        }

        body {
            background: linear-gradient(135deg, var(--canary-yellow), #fff0a8);
            min-height: 100vh;
            padding: 20px;
            color: var(--dark-blue);
            position: relative;
            padding-bottom: 120px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #ffffe0;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(10, 10, 42, 0.15);
            overflow: hidden;
            border: 2px solid var(--olive);
            position: relative;
        }

        header {
            background: linear-gradient(to right, var(--mint-green), var(--lavender));
            padding: 25px;
            text-align: center;
            border-bottom: 3px solid var(--olive);
            position: relative;
            overflow: hidden;
        }

        .floating-shapes {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .shape {
            position: absolute;
            opacity: 0.4;
            animation: float 15s infinite linear;
        }

        .shape:nth-child(1) { top: 10%; left: 5%; width: 40px; height: 40px; background: #ffb3ba; border-radius: 50%; animation-delay: 0s; }
        .shape:nth-child(2) { top: 20%; right: 8%; width: 60px; height: 60px; background: #ffdfba; border-radius: 30% 70% 70% 30%; animation-delay: 1s; }
        .shape:nth-child(3) { bottom: 15%; left: 15%; width: 50px; height: 50px; background: #baffc9; border-radius: 10px; animation-delay: 2s; }
        .shape:nth-child(4) { bottom: 25%; right: 20%; width: 70px; height: 70px; background: #bae1ff; border-radius: 50%; animation-delay: 3s; }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
            100% { transform: translateY(0) rotate(360deg); }
        }

        h1 {
            font-size: 3.8rem;
            margin-bottom: 15px;
            color: var(--dark-blue);
            text-shadow: 2px 2px 4px rgba(10, 10, 42, 0.1);
            position: relative;
            z-index: 1;
        }

        .subtitle {
            font-size: 1.5rem;
            color: #2a3a74;
            max-width: 800px;
            margin: 0 auto;
            line-height: 1.6;
            position: relative;
            z-index: 1;
        }

        .book-selection {
            padding: 30px;
            text-align: center;
        }

        .book-selection h2 {
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: var(--dark-blue);
            background: linear-gradient(to right, var(--peach), var(--sky-blue));
            padding: 15px 30px;
            border-radius: 50px;
            display: inline-block;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .books-container {
            display: flex;
            justify-content: center;
            gap: 40px;
            flex-wrap: wrap;
            margin: 30px 0;
        }

        .book {
            width: 280px;
            height: 380px;
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(10, 10, 42, 0.15);
            transition: all 0.4s;
            cursor: pointer;
            position: relative;
            border: 4px solid var(--baby-blue);
        }

        .book:hover {
            transform: translateY(-15px) scale(1.05);
            box-shadow: 0 15px 35px rgba(10, 10, 42, 0.25);
        }

        .book.animals {
            background: linear-gradient(to bottom right, var(--mint-green), var(--sky-blue));
        }

        .book.fruits {
            background: linear-gradient(to bottom right, var(--peach), var(--pink));
        }

        .book.vegetables {
            background: linear-gradient(to bottom right, var(--olive), #b0e8a0);
        }

        .book-cover {
            height: 70%;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .book-cover img {
            max-width: 100%;
            max-height: 100%;
            filter: drop-shadow(0 5px 10px rgba(0,0,0,0.2));
            border-radius: 10px;
        }

        .book-info {
            height: 30%;
            background: rgba(255, 255, 255, 0.85);
            padding: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .book-title {
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 8px;
            color: var(--dark-blue);
        }

        .book-pages {
            font-size: 1.2rem;
            color: #4a5a94;
        }

        .activity-area {
            padding: 30px;
            display: none;
        }

        .activity-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding: 0 20px;
        }

        .book-name {
            font-size: 2.2rem;
            background: linear-gradient(to right, var(--purple), var(--sky-blue));
            padding: 10px 25px;
            border-radius: 50px;
            color: white;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .page-controls {
            display: flex;
            gap: 15px;
        }

        .palette-btn {
            background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee, #c2e9fb);
            border: none;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            font-size: 1.8rem;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--dark-blue);
            position: relative;
            overflow: hidden;
        }

        .palette-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, rgba(255,255,255,0) 70%);
            pointer-events: none;
        }

        .palette-btn:hover {
            transform: scale(1.1) rotate(10deg);
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
        }

        .palette-btn:active {
            transform: scale(0.95);
        }

        .progress-bar {
            width: 100%;
            height: 20px;
            background: var(--baby-blue);
            border-radius: 10px;
            margin: 15px 0 30px;
            overflow: hidden;
        }

        .progress {
            height: 100%;
            background: linear-gradient(to right, var(--mint-green), var(--sky-blue));
            border-radius: 10px;
            transition: width 0.5s;
        }

        .activity-content {
            display: flex;
            gap: 30px;
            min-height: 500px;
        }

        .instruction-panel {
            flex: 1;
            background: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 8px 20px rgba(10, 10, 42, 0.1);
            border: 3px solid var(--lavender);
        }

        .page-title {
            font-size: 2rem;
            margin-bottom: 20px;
            color: var(--dark-blue);
            text-align: center;
            padding-bottom: 15px;
            border-bottom: 3px dashed var(--mint-green);
        }

        .page-number {
            display: inline-block;
            background: var(--purple);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            text-align: center;
            line-height: 40px;
            margin-right: 10px;
        }

        .instructions {
            font-size: 1.3rem;
            line-height: 1.7;
            color: #2a3a74;
            margin-bottom: 25px;
        }

        .task-list {
            list-style-type: none;
            padding-left: 0;
        }

        .task-list li {
            margin-bottom: 15px;
            font-size: 1.2rem;
            padding: 12px;
            background: rgba(208, 228, 255, 0.3);
            border-radius: 10px;
            border-left: 4px solid var(--sky-blue);
        }

        .interactive-panel {
            flex: 1;
            background: white;
            border-radius: 20px;
            padding: 25px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: 0 8px 20px rgba(10, 10, 42, 0.1);
            border: 3px solid var(--peach);
        }

        .coloring-page {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .coloring-canvas-container {
            position: relative;
            width: 100%;
            max-width: 350px;
            height: 350px;
            margin-bottom: 20px;
        }

        .coloring-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: white;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(10, 10, 42, 0.15);
            border: 3px solid var(--mint-green);
            cursor: crosshair;
        }

        .reference-image {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 15px;
            object-fit: cover;
            opacity: 0.2;
            pointer-events: none;
        }

        .difference-game {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
        }

        .difference-images {
            display: flex;
            gap: 30px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .difference-image {
            width: 250px;
            height: 250px;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(10, 10, 42, 0.15);
            border: 3px solid var(--pink);
            object-fit: cover;
        }

        .difference-markers {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
            max-width: 500px;
        }

        .palette-marker {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee, #c2e9fb);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 3px 8px rgba(0,0,0,0.2);
            font-size: 1.2rem;
        }

        .palette-marker.found {
            background: linear-gradient(135deg, #4caf50, #8bc34a);
            transform: scale(0.8);
        }

        .word-game {
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .target-word {
            font-size: 3rem;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 20px;
            background: linear-gradient(to right, var(--peach), var(--lavender));
            padding: 15px 40px;
            border-radius: 50px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .target-image {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .word-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 15px;
            width: 100%;
            max-width: 600px;
        }

        .palette-word {
            background: linear-gradient(135deg, #a6c1ee, #fbc2eb);
            padding: 15px 10px;
            border-radius: 15px;
            text-align: center;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            color: var(--dark-blue);
            font-weight: bold;
        }

        .palette-word:hover {
            transform: translateY(-5px);
            background: linear-gradient(135deg, #fbc2eb, #a6c1ee);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }

        .palette-word.selected {
            background: linear-gradient(135deg, #4caf50, #8bc34a);
            color: white;
            transform: scale(1.05);
        }

        .tools {
            display: flex;
            gap: 20px;
            margin-top: 30px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .palette-tool-btn {
            background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee, #c2e9fb);
            color: var(--dark-blue);
            border: none;
            padding: 14px 28px;
            border-radius: 50px;
            font-size: 1.2rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            transition: all 0.3s;
            font-weight: bold;
            position: relative;
            overflow: hidden;
        }

        .palette-tool-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, rgba(255,255,255,0) 70%);
            pointer-events: none;
        }

        .palette-tool-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
        }

        .palette-tool-btn:active {
            transform: translateY(2px);
        }

        .reward-container {
            position: relative;
            height: 150px;
            margin: 20px auto;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 20px;
            width: 90%;
            border: 2px dashed var(--pink);
        }

        .reward {
            position: absolute;
            opacity: 0;
            transition: opacity 0.3s;
            font-size: 70px;
            filter: drop-shadow(0 5px 10px rgba(10, 10, 42, 0.3));
        }

        .reward.show {
            opacity: 1;
            animation: floatUp 2s ease-in-out;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) scale(0.5); opacity: 0; }
            30% { transform: translateY(-30px) scale(1); opacity: 1; }
            100% { transform: translateY(-120px) scale(0); opacity: 0; }
        }

        .star {
            color: #ffd700;
        }

        .flower {
            color: #ff69b4;
        }

        .clap {
            color: #87ceeb;
        }

        .heart {
            color: #ff6b6b;
        }

        .info-palette {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
        }

        .palette-info-btn {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee, #c2e9fb);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
            transition: all 0.4s;
            font-size: 2.5rem;
            color: var(--dark-blue);
            position: relative;
            overflow: hidden;
        }

        .palette-info-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,255,255,0.4) 0%, rgba(255,255,255,0) 70%);
            pointer-events: none;
        }

        .palette-info-btn:hover {
            transform: scale(1.1) rotate(15deg);
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
        }

        .info-content {
            position: fixed;
            bottom: -300px;
            left: 0;
            width: 100%;
            background: linear-gradient(to right, #0a0a2a, #1a1a4a);
            padding: 25px;
            text-align: center;
            color: white;
            font-size: 1.2rem;
            transition: bottom 0.5s ease;
            z-index: 999;
            box-shadow: 0 -5px 20px rgba(0,0,0,0.3);
        }

        .info-content.visible {
            bottom: 0;
        }

        .creator-info {
            margin-top: 10px;
            font-size: 1.1rem;
            color: #a0e8d0;
        }

        .close-info {
            position: absolute;
            top: 15px;
            right: 20px;
            background: transparent;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            transition: all 0.3s;
        }

        .close-info:hover {
            transform: scale(1.2);
            color: var(--mint-green);
        }

        @media (max-width: 900px) {
            .activity-content {
                flex-direction: column;
            }
            
            .difference-images {
                flex-direction: column;
                align-items: center;
            }
            
            .book {
                width: 250px;
                height: 350px;
            }
            
            h1 {
                font-size: 3rem;
            }
            
            .palette-tool-btn {
                padding: 12px 20px;
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="floating-shapes">
                <div class="shape"></div>
                <div class="shape"></div>
                <div class="shape"></div>
                <div class="shape"></div>
            </div>
            <h1>Palette Zone</h1>
            <p class="subtitle">Educational Books System for Autistic Children - Learn through repetition and fun activities</p>
        </header>
        
        <div class="book-selection">
            <h2>Choose Your Learning Book</h2>
            <div class="books-container">
                <div class="book animals" data-book="animals">
                    <div class="book-cover">
                        <img src="https://images.unsplash.com/photo-1546182990-dffeafbe841d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YW5pbWFsJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60" alt="Animals Book">
                    </div>
                    <div class="book-info">
                        <div class="book-title">Animals Book</div>
                        <div class="book-pages">30 Educational Pages</div>
                    </div>
                </div>
                
                <div class="book fruits" data-book="fruits">
                    <div class="book-cover">
                        <img src="https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60" alt="Fruits Book">
                    </div>
                    <div class="book-info">
                        <div class="book-title">Fruits Book</div>
                        <div class="book-pages">30 Educational Pages</div>
                    </div>
                </div>
                
                <div class="book vegetables" data-book="vegetables">
                    <div class="book-cover">
                        <img src="https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60" alt="Vegetables Book">
                    </div>
                    <div class="book-info">
                        <div class="book-title">Vegetables Book</div>
                        <div class="book-pages">30 Educational Pages</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="activity-area" id="activityArea">
            <div class="activity-header">
                <div class="book-name" id="bookName">Animals Book</div>
                <div class="page-controls">
                    <button class="palette-btn" id="prevPage"><i class="fas fa-arrow-left"></i></button>
                    <button class="palette-btn" id="nextPage"><i class="fas fa-arrow-right"></i></button>
                    <button class="palette-btn" id="homeBtn"><i class="fas fa-home"></i></button>
                </div>
            </div>
            
            <div class="progress-bar">
                <div class="progress" id="progressBar"></div>
            </div>
            
            <div class="activity-content">
                <div class="instruction-panel">
                    <div class="page-title"><span class="page-number" id="pageNumber">1</span> <span id="activityTitle">Coloring Activity</span></div>
                    <div class="instructions" id="instructions">
                        Color the animal following the numbered coloring guide. 
                        Match the colors to the numbers to reveal the beautiful animal!
                    </div>
                    <ul class="task-list" id="taskList">
                        <li>1 - Color the body yellow</li>
                        <li>2 - Color the mane orange</li>
                        <li>3 - Color the nose brown</li>
                        <li>4 - Color the eyes black</li>
                        <li>5 - Color the background green</li>
                    </ul>
                    <div class="tools">
                        <button class="palette-tool-btn" id="resetBtn"><i class="fas fa-undo"></i> Reset Drawing</button>
                        <button class="palette-tool-btn" id="rewardBtn"><i class="fas fa-gift"></i> Show Reward</button>
                    </div>
                </div>
                
                <div class="interactive-panel">
                    <div class="coloring-page" id="coloringPage">
                        <div class="coloring-canvas-container">
                            <img src="https://images.unsplash.com/photo-1543852786-1cf6624b9987?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8bGlvbiUyMGNvbG9yaW5nfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60" alt="Lion" class="reference-image" id="referenceImage">
                            <canvas class="coloring-canvas" id="coloringCanvas" width="350" height="350"></canvas>
                        </div>
                    </div>
                    
                    <div class="difference-game" id="differenceGame" style="display:none">
                        <div class="difference-images">
                            <img src="https://images.unsplash.com/photo-1546182990-dffeafbe841d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YW5pbWFsJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60" alt="Lion Original" class="difference-image" id="diffImage1">
                            <img src="https://images.unsplash.com/photo-1546182990-dffeafbe841d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YW5pbWFsJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60" alt="Lion with Differences" class="difference-image" id="diffImage2">
                        </div>
                        <div class="difference-markers" id="differenceMarkers">
                            <!-- Markers will be added dynamically -->
                        </div>
                    </div>
                    
                    <div class="word-game" id="wordGame" style="display:none">
                        <div class="target-word" id="targetWord">
                            <div class="target-image">🦁</div>
                            <div>LION</div>
                        </div>
                        <div class="word-grid" id="wordGrid">
                            <!-- Word items will be added dynamically -->
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="reward-container" id="rewardContainer">
                <div class="reward star">★</div>
                <div class="reward flower">✿</div>
                <div class="reward clap">👏</div>
                <div class="reward heart">❤️</div>
            </div>
        </div>
    </div>

    <div class="info-palette">
        <button class="palette-info-btn" id="infoBtn">
            <i class="fas fa-palette"></i>
        </button>
    </div>
    
    <div class="info-content" id="infoContent">
        <button class="close-info" id="closeInfo">
            <i class="fas fa-times"></i>
        </button>
        <p>Palette Zone • Educational Books System for Autistic Children</p>
        <p class="creator-info">Created by Hoda Mostafa Hamdy Aly • Contact: elostazahx@email.com</p>
    </div>

    <script>
        // Book data with actual images for all activities
        const books = {
            animals: {
                name: "Animals Book",
                images: [
                    "https://images.unsplash.com/photo-1543852786-1cf6624b9987?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8bGlvbiUyMGNvbG9yaW5nfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60", // Lion
                    "https://images.unsplash.com/photo-1557050543-4d5f4e07ef46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8ZWxlcGhhbnQlMjBjb2xvcmluZ3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Elephant
                    "https://images.unsplash.com/photo-1557050543-4d5f4e07ef46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8ZWxlcGhhbnQlMjBjb2xvcmluZ3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Giraffe
                    "https://images.unsplash.com/photo-1546182990-dffeafbe841d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YW5pbWFsJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Monkey
                    "https://images.unsplash.com/photo-1546182990-dffeafbe841d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YW5pbWFsJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60"  // Zebra
                ],
                words: ["LION", "ELEPHANT", "GIRAFFE", "MONKEY", "ZEBRA"]
            },
            fruits: {
                name: "Fruits Book",
                images: [
                    "https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60", // Apple
                    "https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60", // Banana
                    "https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60", // Orange
                    "https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60", // Grapes
                    "https://images.unsplash.com/photo-1601001815894-4bb6c81416b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZnJ1aXQlMjBib29rfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"  // Watermelon
                ],
                words: ["APPLE", "BANANA", "ORANGE", "GRAPES", "WATERMELON"]
            },
            vegetables: {
                name: "Vegetables Book",
                images: [
                    "https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Carrot
                    "https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Tomato
                    "https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Broccoli
                    "https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60", // Potato
                    "https://images.unsplash.com/photo-1518843875459-f738682238a6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmVnZXRhYmxlJTIwYm9va3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60"  // Cucumber
                ],
                words: ["CARROT", "TOMATO", "BROCCOLI", "POTATO", "CUCUMBER"]
            }
        };

        // Book and page state
        let currentBook = 'animals';
        let currentPage = 1;
        let currentImageIndex = 0;
        
        // DOM elements
        const bookSelection = document.querySelector('.book-selection');
        const activityArea = document.getElementById('activityArea');
        const bookName = document.getElementById('bookName');
        const pageNumber = document.getElementById('pageNumber');
        const activityTitle = document.getElementById('activityTitle');
        const instructions = document.getElementById('instructions');
        const taskList = document.getElementById('taskList');
        const coloringPage = document.getElementById('coloringPage');
        const differenceGame = document.getElementById('differenceGame');
        const wordGame = document.getElementById('wordGame');
        const referenceImage = document.getElementById('referenceImage');
        const diffImage1 = document.getElementById('diffImage1');
        const diffImage2 = document.getElementById('diffImage2');
        const targetWord = document.getElementById('targetWord');
        const wordGrid = document.getElementById('wordGrid');
        const differenceMarkers = document.getElementById('differenceMarkers');
        const progressBar = document.getElementById('progressBar');
        const infoContent = document.getElementById('infoContent');
        const infoBtn = document.getElementById('infoBtn');
        const closeInfo = document.getElementById('closeInfo');
        
        // Toggle info panel
        infoBtn.addEventListener('click', () => {
            infoContent.classList.add('visible');
        });
        
        closeInfo.addEventListener('click', () => {
            infoContent.classList.remove('visible');
        });
        
        // Update progress bar
        function updateProgress() {
            const progress = (currentPage / 30) * 100;
            progressBar.style.width = `${progress}%`;
        }
        
        // Book selection
        document.querySelectorAll('.book').forEach(book => {
            book.addEventListener('click', () => {
                currentBook = book.dataset.book;
                bookName.textContent = books[currentBook].name;
                bookSelection.style.display = 'none';
                activityArea.style.display = 'block';
                currentPage = 1;
                loadPage(1);
                updateProgress();
            });
        });
        
        // Home button
        document.getElementById('homeBtn').addEventListener('click', () => {
            activityArea.style.display = 'none';
            bookSelection.style.display = 'block';
        });
        
        // Navigation buttons
        document.getElementById('prevPage').addEventListener('click', () => {
            if (currentPage > 1) {
                loadPage(currentPage - 1);
                updateProgress();
            }
        });
        
        document.getElementById('nextPage').addEventListener('click', () => {
            if (currentPage < 30) {
                loadPage(currentPage + 1);
                updateProgress();
            }
        });
        
        // Load page based on number
        function loadPage(page) {
            currentPage = page;
            pageNumber.textContent = page;
            
            // Calculate which image we're using (5 images for 30 pages = 6 pages per image)
            currentImageIndex = Math.floor((page - 1) / 6);
            
            // Determine activity type based on page number pattern
            const pageType = (page - 1) % 6;
            
            // Set the current image for all activities
            const currentImage = books[currentBook].images[currentImageIndex];
            referenceImage.src = currentImage;
            diffImage1.src = currentImage;
            diffImage2.src = currentImage;
            
            if (pageType === 0 || pageType === 1) {
                // Coloring pages
                coloringPage.style.display = 'flex';
                differenceGame.style.display = 'none';
                wordGame.style.display = 'none';
                activityTitle.textContent = "Coloring Activity";
                
                // Set book-specific content
                if (currentBook === 'animals') {
                    instructions.textContent = `Color the ${books.animals.words[currentImageIndex].toLowerCase()} following the numbered coloring guide. Match the colors to the numbers to reveal the beautiful animal!`;
                    taskList.innerHTML = `
                        <li>1 - Color the body yellow</li>
                        <li>2 - Color the mane orange</li>
                        <li>3 - Color the nose brown</li>
                        <li>4 - Color the eyes black</li>
                        <li>5 - Color the background green</li>
                    `;
                } else if (currentBook === 'fruits') {
                    instructions.textContent = `Color the ${books.fruits.words[currentImageIndex].toLowerCase()} following the numbered coloring guide. Use bright colors to make it look delicious!`;
                    taskList.innerHTML = `
                        <li>1 - Color the fruit red</li>
                        <li>2 - Color the leaves green</li>
                        <li>3 - Color the stem brown</li>
                        <li>4 - Color the background blue</li>
                        <li>5 - Color the details yellow</li>
                    `;
                } else if (currentBook === 'vegetables') {
                    instructions.textContent = `Color the ${books.vegetables.words[currentImageIndex].toLowerCase()} following the numbered coloring guide. Make it look fresh and healthy!`;
                    taskList.innerHTML = `
                        <li>1 - Color the vegetable orange</li>
                        <li>2 - Color the leaves green</li>
                        <li>3 - Color the soil brown</li>
                        <li>4 - Color the background blue</li>
                        <li>5 - Color the details yellow</li>
                    `;
                }
                
            } else if (pageType === 2 || pageType === 3) {
                // Spot the difference
                coloringPage.style.display = 'none';
                differenceGame.style.display = 'flex';
                wordGame.style.display = 'none';
                activityTitle.textContent = "Spot the Differences";
                instructions.textContent = "Look carefully at the two pictures. Can you find all 15 differences? Click on the numbers below as you find each difference.";
                
                // Create difference markers
                differenceMarkers.innerHTML = '';
                for (let i = 1; i <= 15; i++) {
                    const marker = document.createElement('div');
                    marker.className = 'palette-marker';
                    marker.textContent = i;
                    marker.addEventListener('click', () => {
                        marker.classList.add('found');
                        showReward();
                    });
                    differenceMarkers.appendChild(marker);
                }
                
            } else {
                // Word association
                coloringPage.style.display = 'none';
                differenceGame.style.display = 'none';
                wordGame.style.display = 'flex';
                activityTitle.textContent = "Word Association Game";
                instructions.textContent = "Find and select all the words that match the target word. Click on each matching word to select it!";
                
                // Set book-specific content
                const target = books[currentBook].words[currentImageIndex];
                let emoji = "🦁";
                
                if (currentBook === 'animals') {
                    if (target === "LION") emoji = "🦁";
                    else if (target === "ELEPHANT") emoji = "🐘";
                    else if (target === "GIRAFFE") emoji = "🦒";
                    else if (target === "MONKEY") emoji = "🐒";
                    else if (target === "ZEBRA") emoji = "🦓";
                } else if (currentBook === 'fruits') {
                    if (target === "APPLE") emoji = "🍎";
                    else if (target === "BANANA") emoji = "🍌";
                    else if (target === "ORANGE") emoji = "🍊";
                    else if (target === "GRAPES") emoji = "🍇";
                    else if (target === "WATERMELON") emoji = "🍉";
                } else if (currentBook === 'vegetables') {
                    if (target === "CARROT") emoji = "🥕";
                    else if (target === "TOMATO") emoji = "🍅";
                    else if (target === "BROCCOLI") emoji = "🥦";
                    else if (target === "POTATO") emoji = "🥔";
                    else if (target === "CUCUMBER") emoji = "🥒";
                }
                
                targetWord.innerHTML = `
                    <div class="target-image">${emoji}</div>
                    <div>${target}</div>
                `;
                
                // Create word grid
                wordGrid.innerHTML = '';
                const words = [];
                
                // Add 5 target words
                for (let i = 0; i < 5; i++) {
                    words.push(target);
                }
                
                // Add 10 random words
                const allWords = currentBook === 'animals' ? 
                    ["LION", "TIGER", "BEAR", "WOLF", "DEER", "FOX", "RABBIT", "PANDA", "KOALA", "GORILLA"] :
                    currentBook === 'fruits' ? 
                    ["APPLE", "PEAR", "KIWI", "MANGO", "CHERRY", "LEMON", "PEACH", "PLUM", "GRAPE", "BERRY"] :
                    ["CARROT", "POTATO", "ONION", "GARLIC", "PEPPER", "CABBAGE", "LETTUCE", "RADISH", "BEET", "PUMPKIN"];
                
                for (let i = 0; i < 10; i++) {
                    const randomIndex = Math.floor(Math.random() * allWords.length);
                    words.push(allWords[randomIndex]);
                }
                
                // Shuffle words
                words.sort(() => Math.random() - 0.5);
                
                // Add words to grid
                words.forEach(word => {
                    const wordItem = document.createElement('div');
                    wordItem.className = 'palette-word';
                    wordItem.textContent = word;
                    wordItem.addEventListener('click', () => {
                        if (word === target) {
                            wordItem.classList.toggle('selected');
                            if (wordItem.classList.contains('selected')) {
                                showReward();
                            }
                        }
                    });
                    wordGrid.appendChild(wordItem);
                });
            }
        }
        
        // Canvas drawing functionality
        const canvas = document.getElementById('coloringCanvas');
        const ctx = canvas.getContext('2d');
        let isDrawing = false;
        let lastX = 0;
        let lastY = 0;
        
        // Set canvas background to white
        ctx.fillStyle = 'white';
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        canvas.addEventListener('mousedown', startDrawing);
        canvas.addEventListener('mousemove', draw);
        canvas.addEventListener('mouseup', stopDrawing);
        canvas.addEventListener('mouseout', stopDrawing);
        
        function startDrawing(e) {
            isDrawing = true;
            [lastX, lastY] = [e.offsetX, e.offsetY];
        }
        
        function draw(e) {
            if (!isDrawing) return;
            
            ctx.strokeStyle = '#ff6b6b';
            ctx.lineWidth = 8;
            ctx.lineJoin = 'round';
            ctx.lineCap = 'round';
            
            ctx.beginPath();
            ctx.moveTo(lastX, lastY);
            ctx.lineTo(e.offsetX, e.offsetY);
            ctx.stroke();
            
            [lastX, lastY] = [e.offsetX, e.offsetY];
        }
        
        function stopDrawing() {
            isDrawing = false;
        }
        
        // Reset drawing
        document.getElementById('resetBtn').addEventListener('click', () => {
            ctx.fillStyle = 'white';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
        });
        
        // Reward system
        const rewardBtn = document.getElementById('rewardBtn');
        const rewardContainer = document.getElementById('rewardContainer');
        const rewards = document.querySelectorAll('.reward');
        
        rewardBtn.addEventListener('click', showReward);
        
        function showReward() {
            const rewardTypes = ['star', 'flower', 'clap', 'heart'];
            const randomReward = Math.floor(Math.random() * 4);
            
            // Hide all rewards
            rewards.forEach(reward => {
                reward.classList.remove('show');
            });
            
            // Show random reward
            setTimeout(() => {
                rewards[randomReward].classList.add('show');
            }, 10);
            
            // Hide reward after animation
            setTimeout(() => {
                rewards[randomReward].classList.remove('show');
            }, 2000);
        }
        
        // Initial setup
        updateProgress();
    </script>
</body>
</html>
