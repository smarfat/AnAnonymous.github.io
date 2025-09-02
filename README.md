<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Love</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        header {
            text-align: center;
            padding: 50px 0;
            position: relative;
        }

        .header-content {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            animation: fadeInDown 1.5s ease;
            max-width: 800px;
            margin: 0 auto;
        }

        .header-title {
            font-size: 3.5rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            animation: fadeInDown 1.5s ease;
        }

        .header-subtitle {
            font-size: 1.5rem;
            margin-bottom: 30px;
            opacity: 0.9;
            animation: fadeInUp 1.5s ease;
        }

        .header-quote {
            font-style: italic;
            font-size: 1.2rem;
            opacity: 0.8;
            margin-top: 20px;
            animation: fadeIn 2s ease;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .heart {
            color: #ff4458;
            font-size: 2rem;
            animation: pulse 1.5s infinite;
            display: inline-block;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .love-letter {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            animation: fadeIn 2s ease;
        }

        .letter-content {
            font-size: 1.2rem;
            line-height: 1.8;
            margin-bottom: 20px;
        }

        .signature {
            text-align: right;
            font-style: italic;
            font-size: 1.3rem;
        }

        .photo-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin: 50px 0;
        }

        .photo-frame {
            position: relative;
            height: 250px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transition: transform 0.5s ease;
        }

        .photo-frame:hover {
            transform: scale(1.05);
        }

        .photo-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .photo-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.6);
            color: white;
            padding: 10px;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .photo-frame:hover .photo-caption {
            transform: translateY(0);
        }

        .reasons {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin: 50px 0;
        }

        .reason-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(5px);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            animation: slideInUp 0.8s ease forwards;
            opacity: 0;
        }

        .reason-card:nth-child(1) { animation-delay: 0.2s; }
        .reason-card:nth-child(2) { animation-delay: 0.4s; }
        .reason-card:nth-child(3) { animation-delay: 0.6s; }
        .reason-card:nth-child(4) { animation-delay: 0.8s; }
        .reason-card:nth-child(5) { animation-delay: 1.0s; }
        .reason-card:nth-child(6) { animation-delay: 1.2s; }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .reason-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .reason-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #ff4458;
        }

        .timeline {
            position: relative;
            margin: 50px 0;
            padding: 20px 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            top: 0;
            left: 50%;
            width: 4px;
            height: 100%;
            background: rgba(255, 255, 255, 0.3);
            transform: translateX(-50%);
        }

        .timeline-item {
            position: relative;
            margin-bottom: 30px;
            width: 50%;
        }

        .timeline-item:nth-child(odd) {
            left: 0;
            padding-right: 40px;
            text-align: right;
        }

        .timeline-item:nth-child(even) {
            left: 50%;
            padding-left: 40px;
        }

        .timeline-content {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(5px);
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .timeline-dot {
            position: absolute;
            top: 20px;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #ff4458;
            box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.2);
        }

        .timeline-item:nth-child(odd) .timeline-dot {
            right: -10px;
        }

        .timeline-item:nth-child(even) .timeline-dot {
            left: -10px;
        }

        .interactive-message {
            text-align: center;
            margin: 50px 0;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .message-input {
            width: 100%;
            max-width: 500px;
            padding: 15px;
            border-radius: 50px;
            border: none;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-size: 1rem;
            margin-bottom: 20px;
            backdrop-filter: blur(5px);
        }

        .message-input::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .send-btn {
            background: #ff4458;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 68, 88, 0.3);
        }

        .send-btn:hover {
            background: #ff3366;
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 68, 88, 0.4);
        }

        .message-display {
            margin-top: 30px;
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-style: italic;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
        }

        .countdown-container {
            text-align: center;
            margin: 50px 0;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .countdown-title {
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .countdown {
            font-size: 1.5rem;
            font-weight: bold;
        }

        .floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .heart-float {
            position: absolute;
            bottom: -20px;
            color: rgba(255, 68, 88, 0.7);
            font-size: 20px;
            animation: floatUp 10s linear infinite;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .music-player {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            border-radius: 50px;
            padding: 15px;
            display: flex;
            align-items: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            z-index: 100;
            width: 300px;
        }

        .music-info {
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            margin-right: 10px;
        }

        .music-title {
            font-size: 0.9rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .music-artist {
            font-size: 0.7rem;
            opacity: 0.8;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .music-controls {
            display: flex;
            align-items: center;
        }

        .music-control {
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            margin: 0 5px;
            transition: transform 0.2s ease;
        }

        .music-control:hover {
            transform: scale(1.2);
        }

        .progress-container {
            width: 100%;
            height: 4px;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 2px;
            margin-top: 8px;
            cursor: pointer;
        }

        .progress-bar {
            height: 100%;
            background: #ff4458;
            border-radius: 2px;
            width: 0%;
            transition: width 0.1s linear;
        }

        .volume-container {
            display: flex;
            align-items: center;
            margin-left: 10px;
        }

        .volume-slider {
            width: 50px;
            height: 4px;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 2px;
            outline: none;
            cursor: pointer;
        }

        footer {
            text-align: center;
            padding: 30px 0;
            margin-top: 50px;
            font-size: 1.1rem;
        }

        .footer-heart {
            color: #ff4458;
            animation: pulse 1.5s infinite;
        }

        .distance-section {
            text-align: center;
            margin: 50px 0;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .distance-title {
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .distance-content {
            font-size: 1.2rem;
            line-height: 1.8;
        }

        .notification {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            border-radius: 10px;
            padding: 15px 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .notification.show {
            opacity: 1;
        }

        @media (max-width: 768px) {
            .header-title {
                font-size: 2.5rem;
            }
            
            .header-subtitle {
                font-size: 1.2rem;
            }
            
            .timeline::before {
                left: 30px;
            }
            
            .timeline-item {
                width: 100%;
                padding-left: 60px !important;
                padding-right: 0 !important;
                left: 0 !important;
                text-align: left !important;
            }
            
            .timeline-dot {
                left: 20px !important;
                right: auto !important;
            }
            
            .reasons {
                grid-template-columns: 1fr;
            }
            
            .music-player {
                width: 250px;
                flex-direction: column;
                padding: 10px;
            }
            
            .music-info {
                margin-right: 0;
                margin-bottom: 10px;
            }
            
            .volume-container {
                margin-left: 0;
                margin-top: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="floating-hearts" id="floating-hearts"></div>
    
    <div class="container">
        <header>
            <div class="header-content">
                <h1 class="header-title">A Love Beyond Distance <span class="heart"><i class="fas fa-heart"></i></span></h1>
                <p class="header-subtitle">From Syed Mohammad Arfatur Rahman to Syeda Komol Hoque Ilma</p>
                <p class="header-quote">"Distance means so little when someone means so much"</p>
            </div>
        </header>

        <section class="love-letter">
            <div class="letter-content">
                <p>My dearest Ilma,</p>
                <p>Though we haven't yet met in person, my heart has already found its home in you. In this digital age where connections span across distances, ours feels like something truly special and destined.</p>
                <p>Every message we share, every conversation we have, brings me closer to you in spirit. Your words paint a picture of someone so beautiful, inside and out, and I find myself falling more deeply with each passing day.</p>
                <p>The miles between us are merely numbers on a map, for you are always in my thoughts and in my heart. I dream of the day when I can finally look into your eyes, hear your voice in person, and take your hand in mine.</p>
                <p>Until that day comes, know that my love for you grows stronger with every sunrise and every sunset. Distance cannot diminish what we share; it only makes our eventual reunion that much more precious.</p>
            </div>
            <div class="signature">
                Forever yours, across any distance,<br>
                Syed Mohammad Arfatur Rahman
            </div>
        </section>

        <section class="distance-section">
            <h2 class="distance-title">Our Connection Knows No Bounds</h2>
            <div class="distance-content">
                <p>Though we are separated by miles, our hearts beat as one. Every day brings us closer to the moment when we will finally meet face to face.</p>
                <p>Until then, we continue to build this beautiful connection through words, dreams, and the promise of what's to come.</p>
            </div>
        </section>

        <section class="photo-gallery">
            <div class="photo-frame">
                <img src="https://picsum.photos/seed/distance1/400/300.jpg" alt="Dreaming of you">
                <div class="photo-caption">Dreaming of our first meeting</div>
            </div>
            <div class="photo-frame">
                <img src="https://picsum.photos/seed/distance2/400/300.jpg" alt="Our connection">
                <div class="photo-caption">Our connection across the miles</div>
            </div>
            <div class="photo-frame">
                <img src="https://picsum.photos/seed/distance3/400/300.jpg" alt="Waiting for you">
                <div class="photo-caption">Counting moments until we meet</div>
            </div>
            <div class="photo-frame">
                <img src="https://picsum.photos/seed/distance4/400/300.jpg" alt="Our future">
                <div class="photo-caption">The future we're building together</div>
            </div>
        </section>

        <section class="reasons">
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-comments"></i></div>
                <h3>Your Words</h3>
                <p>The way you express yourself through words captivates me. Every message from you brightens my day and makes me feel closer to you, despite the distance between us.</p>
            </div>
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-brain"></i></div>
                <h3>Your Mind</h3>
                <p>Your intelligence and the way you see the world inspire me. Our conversations are the highlight of my days, and I learn something new from you every time we talk.</p>
            </div>
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-heart"></i></div>
                <h3>Your Kindness</h3>
                <p>Even through digital communication, your compassion and warmth shine through. Your kindness knows no bounds, and it's one of the many things I adore about you.</p>
            </div>
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-laugh"></i></div>
                <h3>Your Joy</h3>
                <p>Your happiness and positive outlook on life are contagious. Even when we're miles apart, your joy lifts my spirits and brings a smile to my face.</p>
            </div>
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-star"></i></div>
                <h3>Your Dreams</h3>
                <p>The passion you have for your dreams and goals inspires me to be better. I can't wait to support you in person as you chase everything you desire in life.</p>
            </div>
            <div class="reason-card">
                <div class="reason-icon"><i class="fas fa-infinity"></i></div>
                <h3>Your Love</h3>
                <p>The love and affection you show me, even from afar, makes me feel like the luckiest person in the world. Distance cannot diminish the love we share.</p>
            </div>
        </section>

        <section class="timeline">
            <h2 style="text-align: center; margin-bottom: 40px;">Our Journey So Far</h2>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>First Connection</h3>
                    <p>The moment our paths first crossed, even if digitally, I felt something special begin to bloom.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>Our First Conversation</h3>
                    <p>Nervous, excited, and completely captivated by you from our very first exchange of words.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>Falling in Love</h3>
                    <p>Every conversation, every shared thought, made me fall deeper and deeper in love with the person you are.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>"I Love You"</h3>
                    <p>The three most meaningful words I've ever said, and I'll never stop saying them, no matter the distance between us.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-dot"></div>
                <div class="timeline-content">
                    <h3>Dreaming of Our First Meeting</h3>
                    <p>Every day brings us closer to the moment when we will finally meet face to face and begin the next chapter of our story.</p>
                </div>
            </div>
        </section>

        <section class="countdown-container">
            <h2 class="countdown-title">Counting Down to Our Future</h2>
            <div class="countdown" id="countdown">Loading...</div>
        </section>

        <section class="interactive-message">
            <h2>Send a message across the miles</h2>
            <p>Type a message to see it displayed with love</p>
            <input type="text" class="message-input" id="message-input" placeholder="Type your message of love here...">
            <button class="send-btn" id="send-message">Send Love</button>
            <div class="message-display" id="message-display"></div>
        </section>

        <footer>
            <p>Made with <span class="footer-heart"><i class="fas fa-heart"></i></span> by Syed Mohammad Arfatur Rahman for Syeda Komol Hoque Ilma</p>
            <p>© 2025 Our Love Story | Bridging Distances with Love</p>
        </footer>
    </div>

    <div class="music-player">
        <div class="music-info">
            <div class="music-title" id="music-title">Perfect</div>
            <div class="music-artist" id="music-artist">Ed Sheeran</div>
            <div class="progress-container" id="progress-container">
                <div class="progress-bar" id="progress-bar"></div>
            </div>
        </div>
        <div class="music-controls">
            <button class="music-control" id="prev-btn"><i class="fas fa-step-backward"></i></button>
            <button class="music-control" id="play-btn"><i class="fas fa-play"></i></button>
            <button class="music-control" id="pause-btn" style="display: none;"><i class="fas fa-pause"></i></button>
            <button class="music-control" id="next-btn"><i class="fas fa-step-forward"></i></button>
        </div>
        <div class="volume-container">
            <i class="fas fa-volume-up"></i>
            <input type="range" class="volume-slider" id="volume-slider" min="0" max="100" value="70">
        </div>
    </div>

    <div class="notification" id="notification"></div>

    <!-- Audio element for music playback -->
    <audio id="audio-player"></audio>

    <script>
        // Music playlist with local files
        const playlist = [
            {
                title: "Perfect",
                artist: "Ed Sheeran",
                src: "music/perfect.mp3"  // Local file in the music folder
            },
            {
                title: "Thinking Out Loud",
                artist: "Ed Sheeran",
                src: "music/thinking-out-loud.mp3"  // Local file in the music folder
            },
            {
                title: "All of Me",
                artist: "John Legend",
                src: "music/all-of-me.mp3"  // Local file in the music folder
            }
        ];

        let currentTrack = 0;
        let isPlaying = false;

        // DOM elements
        const audioPlayer = document.getElementById('audio-player');
        const playBtn = document.getElementById('play-btn');
        const pauseBtn = document.getElementById('pause-btn');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const musicTitle = document.getElementById('music-title');
        const musicArtist = document.getElementById('music-artist');
        const progressBar = document.getElementById('progress-bar');
        const progressContainer = document.getElementById('progress-container');
        const volumeSlider = document.getElementById('volume-slider');
        const notification = document.getElementById('notification');

        // Load the first track
        function loadTrack(trackIndex) {
            const track = playlist[trackIndex];
            musicTitle.textContent = track.title;
            musicArtist.textContent = track.artist;
            audioPlayer.src = track.src;
            audioPlayer.load();
        }

        // Show notification
        function showNotification(message) {
            notification.textContent = message;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Play the current track
        function playTrack() {
            audioPlayer.play()
                .then(() => {
                    isPlaying = true;
                    playBtn.style.display = 'none';
                    pauseBtn.style.display = 'inline-block';
                    showNotification(`Now playing: ${playlist[currentTrack].title} by ${playlist[currentTrack].artist}`);
                    
                    // Create more hearts when music is playing
                    const musicHeartInterval = setInterval(() => {
                        if (isPlaying) {
                            createHeart();
                        } else {
                            clearInterval(musicHeartInterval);
                        }
                    }, 800);
                })
                .catch(error => {
                    showNotification("Playback failed. Make sure the music files are in the correct location.");
                    console.error("Playback failed:", error);
                });
        }

        // Pause the current track
        function pauseTrack() {
            audioPlayer.pause();
            isPlaying = false;
            pauseBtn.style.display = 'none';
            playBtn.style.display = 'inline-block';
        }

        // Play the previous track
        function prevTrack() {
            currentTrack = (currentTrack - 1 + playlist.length) % playlist.length;
            loadTrack(currentTrack);
            if (isPlaying) {
                playTrack();
            }
        }

        // Play the next track
        function nextTrack() {
            currentTrack = (currentTrack + 1) % playlist.length;
            loadTrack(currentTrack);
            if (isPlaying) {
                playTrack();
            }
        }

        // Update progress bar
        function updateProgress() {
            const { duration, currentTime } = audioPlayer;
            if (duration) {
                const progressPercent = (currentTime / duration) * 100;
                progressBar.style.width = `${progressPercent}%`;
            }
        }

        // Set progress
        function setProgress(e) {
            const width = this.clientWidth;
            const clickX = e.offsetX;
            const duration = audioPlayer.duration;
            if (duration) {
                audioPlayer.currentTime = (clickX / width) * duration;
            }
        }

        // Set volume
        function setVolume() {
            audioPlayer.volume = this.value / 100;
        }

        // Event listeners
        playBtn.addEventListener('click', playTrack);
        pauseBtn.addEventListener('click', pauseTrack);
        prevBtn.addEventListener('click', prevTrack);
        nextBtn.addEventListener('click', nextTrack);
        audioPlayer.addEventListener('timeupdate', updateProgress);
        audioPlayer.addEventListener('ended', nextTrack);
        progressContainer.addEventListener('click', setProgress);
        volumeSlider.addEventListener('input', setVolume);

        // Load the first track
        loadTrack(currentTrack);

        // Floating hearts animation
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart-float');
            heart.innerHTML = '<i class="fas fa-heart"></i>';
            
            // Random position along the x-axis
            const xPos = Math.random() * window.innerWidth;
            heart.style.left = xPos + 'px';
            
            // Random size
            const size = Math.random() * 15 + 10;
            heart.style.fontSize = size + 'px';
            
            // Random animation duration
            const duration = Math.random() * 5 + 10;
            heart.style.animationDuration = duration + 's';
            
            document.getElementById('floating-hearts').appendChild(heart);
            
            // Remove heart after animation completes
            setTimeout(() => {
                heart.remove();
            }, duration * 1000);
        }
        
        // Create hearts periodically
        setInterval(createHeart, 1000);
        
        // Interactive message functionality
        const messageInput = document.getElementById('message-input');
        const sendButton = document.getElementById('send-message');
        const messageDisplay = document.getElementById('message-display');
        
        function displayMessage() {
            const message = messageInput.value.trim();
            if (message) {
                messageDisplay.innerHTML = `"${message}" <span class="heart"><i class="fas fa-heart"></i></span>`;
                messageInput.value = '';
                
                // Create a burst of hearts when message is sent
                for (let i = 0; i < 10; i++) {
                    setTimeout(createHeart, i * 100);
                }
            }
        }
        
        sendButton.addEventListener('click', displayMessage);
        messageInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                displayMessage();
            }
        });
        
        // Add some interactive effects to reason cards
        const reasonCards = document.querySelectorAll('.reason-card');
        
        reasonCards.forEach(card => {
            card.addEventListener('click', function() {
                // Create a heart at the click position
                const heart = document.createElement('div');
                heart.innerHTML = '<i class="fas fa-heart"></i>';
                heart.style.position = 'absolute';
                heart.style.color = '#ff4458';
                heart.style.fontSize = '30px';
                heart.style.left = '50%';
                heart.style.top = '50%';
                heart.style.transform = 'translate(-50%, -50%)';
                heart.style.pointerEvents = 'none';
                heart.style.zIndex = '10';
                
                this.appendChild(heart);
                
                // Animate the heart
                setTimeout(() => {
                    heart.style.transition = 'all 1s ease';
                    heart.style.transform = 'translate(-50%, -150%) scale(1.5)';
                    heart.style.opacity = '0';
                }, 10);
                
                // Remove the heart after animation
                setTimeout(() => {
                    heart.remove();
                }, 1000);
            });
        });
        
        // Add a special effect when clicking on the main heart
        const mainHeart = document.querySelector('.heart');
        
        mainHeart.addEventListener('click', function() {
            // Create a burst of hearts
            for (let i = 0; i < 20; i++) {
                setTimeout(createHeart, i * 50);
            }
            
            // Change the main heart temporarily
            this.innerHTML = '<i class="fas fa-heart-broken"></i>';
            setTimeout(() => {
                this.innerHTML = '<i class="fas fa-heart"></i>';
            }, 500);
        });
        
        // Add a countdown to a special date (e.g., when you might meet)
        function updateCountdown() {
            // Set your special meeting date here (YYYY, MM, DD)
            const specialDate = new Date(2024, 11, 31); // December 31, 2024
            const currentDate = new Date();
            
            // If the date has passed this year, set it for next year
            if (currentDate > specialDate) {
                specialDate.setFullYear(specialDate.getFullYear() + 1);
            }
            
            const diff = specialDate - currentDate;
            
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            
            // Update the countdown display
            const countdownElement = document.getElementById('countdown');
            countdownElement.innerHTML = `${days} days, ${hours} hours, ${minutes} minutes, ${seconds} seconds until we hopefully meet!`;
        }
        
        // Update the countdown every second
        setInterval(updateCountdown, 1000);
        updateCountdown(); // Initial call
    </script>
</body>
</html>
