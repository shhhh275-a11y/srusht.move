<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="The First Kurdish Site for Finding Amazing Movies - Movies with Shocking Endings">
    <meta name="keywords" content="movies, cinema, Kurdish, shocking ending, amazing films">
    <meta name="author" content="srusht.movies">
    <title>Shocking Ending Movies - Kurdish Movie Site</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #c77b63;
            --secondary: #0f172a;
            --accent: #f59e0b;
            --text: #f8fafc;
            --card-bg: rgba(255, 255, 255, 0.08);
            --shadow: rgba(0, 0, 0, 0.5);
            --header-bg: rgba(255, 255, 255, 0.05);
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            min-height: 100vh;
            background: var(--secondary);
            color: var(--text);
            overflow-x: hidden;
            position: relative;
            transition: background-color 0.5s ease;
        }

        body.light-mode {
            --secondary: #f1f5f9;
            --text: #0f172a;
            --card-bg: rgba(15, 23, 42, 0.08);
            --header-bg: rgba(15, 23, 42, 0.05);
            --shadow: rgba(0, 0, 0, 0.1);
        }

        .background-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(135deg, rgba(0,0,0,0.9) 0%, rgba(15,23,42,0.95) 100%),
                url('https://images.unsplash.com/photo-1489599809505-7c8e1a48bcc0?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
            opacity: 0.15;
            z-index: -2;
            transition: opacity 0.5s ease;
        }

        body.light-mode .background-overlay {
            opacity: 0.05;
        }

        .gradient-circle {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 600px;
            height: 600px;
            border-radius: 50%;
            background: radial-gradient(circle, var(--primary) 0%, #8b5a4a 50%, transparent 70%);
            opacity: 0.1;
            filter: blur(60px);
            z-index: -1;
            animation: float 25s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(-50%, -50%) scale(1) rotate(0deg); }
            33% { transform: translate(-48%, -52%) scale(1.05) rotate(120deg); }
            66% { transform: translate(-52%, -48%) scale(1.1) rotate(240deg); }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding: 25px 0;
        }

        .site-title {
            font-size: 1.6em;
            font-weight: 700;
            margin-bottom: 15px;
            padding: 18px 40px;
            border: 2px solid rgba(255,255,255,0.2);
            border-radius: 50px;
            display: inline-block;
            background: var(--header-bg);
            backdrop-filter: blur(10px);
            animation: fadeInDown 1s ease;
            box-shadow: 0 8px 25px var(--shadow);
            transition: all 0.5s ease;
        }

        body.light-mode .site-title {
            border: 2px solid rgba(15, 23, 42, 0.2);
        }

        .brand-name {
            font-size: 3.2em;
            font-weight: 900;
            text-shadow: 2px 2px 0px rgba(0,0,0,0.4), 0 0 20px rgba(255,255,255,0.2);
            background: linear-gradient(45deg, #f8fafc, #e2e8f0, #cbd5e1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 8px;
            animation: fadeIn 1.5s ease;
            letter-spacing: 2px;
        }

        body.light-mode .brand-name {
            background: linear-gradient(45deg, #0f172a, #334155, #475569);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* ===== DARK MODE TOGGLE ===== */
        .mode-switcher-container {
            text-align: center;
            margin: 5px auto 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .mode-label {
            font-weight: 600;
            color: rgba(248, 250, 252, 0.9);
            font-size: 0.95em;
        }

        body.light-mode .mode-label {
            color: rgba(15, 23, 42, 0.9);
        }

        .mode-switcher {
            position: relative;
            display: inline-block;
            width: 70px;
            height: 30px;
        }

        .mode-switcher input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .mode-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, #475569, #0f172a);
            transition: .4s;
            border-radius: 34px;
            display: flex;
            align-items: center;
            padding: 0 5px;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.3);
        }

        .mode-slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: #f8fafc;
            transition: .4s;
            border-radius: 50%;
            z-index: 2;
        }

        .mode-icon {
            font-size: 0.8em;
            z-index: 1;
            transition: opacity 0.3s;
            color: #f8fafc;
        }

        #dark-icon {
            margin-right: auto;
            opacity: 1;
        }

        #light-icon {
            margin-left: auto;
            opacity: 0.7;
        }

        input:checked + .mode-slider {
            background: linear-gradient(90deg, #fdba74, #f59e0b);
        }

        input:checked + .mode-slider:before {
            transform: translateX(40px);
        }

        input:checked + .mode-slider #dark-icon {
            opacity: 0.7;
        }

        input:checked + .mode-slider #light-icon {
            opacity: 1;
        }

        /* ===== INSTAGRAM SECTION ===== */
        .social-section {
            text-align: center;
            margin: 10px auto 25px;
            padding: 0 15px;
        }

        .social-title {
            font-size: 1.3em;
            margin-bottom: 20px;
            color: rgba(248,250,252,0.9);
            font-weight: 600;
        }

        body.light-mode .social-title {
            color: rgba(15, 23, 42, 0.9);
        }

        .social-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            max-width: 500px;
            margin: 0 auto;
        }

        .social-card {
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            border-radius: 18px;
            padding: 15px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: 0 6px 20px rgba(0,0,0,0.25);
            transition: all 0.3s ease;
            min-width: 200px;
            flex: 1;
            max-width: 240px;
        }

        body.light-mode .social-card {
            border: 1px solid rgba(15, 23, 42, 0.12);
        }

        .social-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
        }

        body.light-mode .social-card:hover {
            background: rgba(15, 23, 42, 0.12);
            border: 1px solid rgba(15, 23, 42, 0.25);
        }

        .social-card a {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: var(--text);
            gap: 10px;
        }

        .social-icon {
            font-size: 2em;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .social-name {
            font-size: 1.1em;
            font-weight: 700;
        }

        .social-username {
            font-size: 0.85em;
            color: rgba(248,250,252,0.7);
            direction: ltr;
        }

        body.light-mode .social-username {
            color: rgba(15, 23, 42, 0.7);
        }

        .social-follow {
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            padding: 7px 18px;
            border-radius: 50px;
            font-weight: 600;
            margin-top: 6px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 12px rgba(253,29,29,0.3);
            font-size: 0.85em;
        }

        .social-card:hover .social-follow {
            transform: scale(1.05);
            box-shadow: 0 6px 16px rgba(253,29,29,0.5);
        }

        /* ===== SEARCH SECTION ===== */
        .search-section {
            max-width: 600px;
            margin: 25px auto 35px;
            padding: 0 20px;
        }

        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(12px);
            border-radius: 50px;
            padding: 4px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 8px 25px var(--shadow);
            transition: all 0.3s ease;
        }

        body.light-mode .search-box {
            background: rgba(15, 23, 42, 0.1);
            border: 1px solid rgba(15, 23, 42, 0.15);
        }

        .search-input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 16px 22px;
            color: var(--text);
            font-size: 1em;
            outline: none;
        }

        .search-input::placeholder {
            color: rgba(248,250,252,0.6);
        }

        body.light-mode .search-input::placeholder {
            color: rgba(15, 23, 42, 0.6);
        }

        .search-button {
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            border: none;
            border-radius: 50px;
            padding: 16px 30px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.95em;
        }

        .search-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 12px rgba(253,29,29,0.4);
        }

        /* ===== MOVIE GRID ===== */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            padding: 25px 0;
        }

        .movie-card {
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 35px var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
            cursor: pointer;
            position: relative;
            animation: fadeInUp 0.7s ease backwards;
        }

        body.light-mode .movie-card {
            border: 1px solid rgba(15, 23, 42, 0.1);
        }

        .movie-card:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        body.light-mode .movie-card:hover {
            background: rgba(15, 23, 42, 0.12);
            border: 1px solid rgba(15, 23, 42, 0.2);
        }

        .movie-rank {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0,0,0,0.85);
            color: var(--accent);
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.3em;
            border: 3px solid var(--accent);
            box-shadow: 0 4px 20px rgba(245, 158, 11, 0.5);
            z-index: 10;
            animation: pulse 2.5s infinite;
        }

        .movie-poster {
            width: 100%;
            height: 380px;
            background-size: cover;
            background-position: center;
            position: relative;
            overflow: hidden;
        }

        .movie-poster::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 60%;
            background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, transparent 100%);
        }

        .movie-info {
            padding: 22px;
            background: rgba(0, 0, 0, 0.3);
        }

        body.light-mode .movie-info {
            background: rgba(255, 255, 255, 0.3);
        }

        .movie-title {
            font-size: 1.5em;
            font-weight: 700;
            margin-bottom: 10px;
            color: var(--text);
        }

        .movie-year {
            color: rgba(248,250,252,0.8);
            font-size: 0.95em;
            margin-bottom: 12px;
            font-weight: 500;
        }

        body.light-mode .movie-year {
            color: rgba(15, 23, 42, 0.8);
        }

        .movie-plot {
            color: rgba(248,250,252,0.9);
            font-size: 0.9em;
            line-height: 1.6;
            margin-bottom: 15px;
            height: 78px;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
        }

        body.light-mode .movie-plot {
            color: rgba(15, 23, 42, 0.9);
        }

        .movie-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .imdb-rating {
            background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
            color: #000;
            padding: 8px 16px;
            border-radius: 12px;
            font-weight: 700;
            font-size: 1.05em;
            box-shadow: 0 4px 15px rgba(245, 158, 11, 0.4);
        }

        .age-rating {
            background: linear-gradient(135deg, #ef4444 0%, #dc2626 100%);
            color: white;
            padding: 8px 16px;
            border-radius: 12px;
            font-weight: 700;
            font-size: 0.9em;
            box-shadow: 0 4px 15px rgba(239, 68, 68, 0.4);
        }

        .age-rating.pg13 {
            background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
        }

        .age-rating.g {
            background: linear-gradient(135deg, #10b981 0%, #059669 100%);
            box-shadow: 0 4px 15px rgba(16, 185, 129, 0.4);
        }

        /* ===== FOOTER & OWNER ===== */
        .owner-box {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(12px);
            border-radius: 20px;
            padding: 28px;
            margin: 35px auto;
            max-width: 450px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            text-align: center;
            position: relative;
        }

        body.light-mode .owner-box {
            background: rgba(15, 23, 42, 0.08);
            border: 1px solid rgba(15, 23, 42, 0.15);
        }

        .owner-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #f59e0b, #ef4444, #3b82f6, #833ab4);
        }

        .owner-title {
            font-size: 1.1em;
            color: rgba(248,250,252,0.8);
            margin-bottom: 8px;
            font-weight: 600;
        }

        body.light-mode .owner-title {
            color: rgba(15, 23, 42, 0.8);
        }

        .owner-name {
            font-size: 2em;
            color: var(--accent);
            font-weight: 800;
            margin-bottom: 10px;
            text-shadow: 0 0 15px rgba(245, 158, 11, 0.7);
        }

        .owner-subtitle {
            font-size: 0.95em;
            color: rgba(248,250,252,0.7);
            font-style: italic;
        }

        body.light-mode .owner-subtitle {
            color: rgba(15, 23, 42, 0.7);
        }

        .footer {
            text-align: center;
            margin-top: 50px;
            padding: 25px;
            color: rgba(248,250,252,0.6);
            font-size: 0.9em;
            border-top: 1px solid rgba(255,255,255,0.1);
            background: rgba(0,0,0,0.15);
            border-radius: 15px 15px 0 0;
        }

        body.light-mode .footer {
            color: rgba(15, 23, 42, 0.6);
            border-top: 1px solid rgba(15, 23, 42, 0.1);
            background: rgba(241, 245, 249, 0.4);
        }

        /* ===== ANIMATIONS ===== */
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 768px) {
            .brand-name { font-size: 2.4em; }
            .site-title { font-size: 1.2em; padding: 14px 25px; }
            .movie-grid { grid-template-columns: 1fr; gap: 20px; }
            .social-container { flex-direction: column; align-items: center; }
            .social-card { max-width: 280px; }
            .search-section { padding: 0 15px; }
        }

        @media (max-width: 480px) {
            .brand-name { font-size: 2em; }
            .site-title { font-size: 1em; padding: 12px 20px; }
            .movie-poster { height: 350px; }
            .mode-switcher-container { gap: 8px; }
            .mode-label { font-size: 0.9em; }
        }
    </style>
</head>
<body class="dark-mode">
    <div class="background-overlay"></div>
    <div class="gradient-circle"></div>

    <div class="container">
        <!-- Header -->
        <header class="header">
            <div class="site-title">🎬 The First Kurdish Site for Finding Amazing Movies</div>
            <h1 class="brand-name">Shocking Ending Movies</h1>
        </header>

        <!-- Dark Mode Toggle -->
        <div class="mode-switcher-container">
            <span class="mode-label">Mode: </span>
            <label class="mode-switcher">
                <input type="checkbox" id="modeToggle">
                <span class="mode-slider">
                    <span id="dark-icon" class="mode-icon">🌙</span>
                    <span id="light-icon" class="mode-icon">☀️</span>
                </span>
            </label>
            <span class="mode-label" id="currentModeLabel">Dark</span>
            <div class="auto-status" id="autoStatus"></div>
        </div>

        <!-- Instagram Section -->
        <section class="social-section">
            <h2 class="social-title">Visit Our Instagram Accounts</h2>
            <div class="social-container">
                <div class="social-card">
                    <a href="https://www.instagram.com/lipri_26" target="_blank">
                        <div class="social-icon"><i class="fab fa-instagram"></i></div>
                        <div class="social-name">Movies Account</div>
                        <div class="social-username">@lipri_26</div>
                        <div class="social-follow">Follow</div>
                    </a>
                </div>
                <div class="social-card">
                    <a href="https://www.instagram.com/ml.2050ll" target="_blank">
                        <div class="social-icon"><i class="fab fa-instagram"></i></div>
                        <div class="social-name">Film Reviews</div>
                        <div class="social-username">@ml.2050ll</div>
                        <div class="social-follow">Follow</div>
                    </a>
                </div>
            </div>
        </section>

        <!-- Search Section -->
        <section class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" placeholder="Search by movie name...">
                <button class="search-button"><i class="fas fa-search"></i> Search</button>
            </div>
        </section>

        <!-- Movie Grid -->
        <section class="movie-grid" id="movieGrid">
            <!-- Movies will load here -->
        </section>

        <!-- No Results -->
        <div class="no-results" id="noResults" style="display:none; text-align:center; padding:40px;">
            <i class="fas fa-film fa-2x" style="opacity:0.5; margin-bottom:15px;"></i>
            <p>No movies found with that name!</p>
        </div>

        <!-- Pagination -->
        <div class="pagination" id="pagination"></div>

        <!-- Owner Section -->
        <section class="owner-box">
            <div class="owner-title">Site Owner</div>
            <div class="owner-name">srusht.movies</div>
            <div class="owner-subtitle">This website is owned by srusht.movies</div>
        </section>

        <!-- Footer -->
        <footer class="footer">
            <p>© 2023 Shocking Ending Movies - All Rights Reserved</p>
            <p style="margin-top:8px; font-size:0.85em; opacity:0.7;">
                This site is created for entertainment and cinema appreciation
            </p>
            <p style="margin-top:12px; font-size:0.8em; opacity:0.6;">
                <i class="fas fa-hashtag"></i> Kurdish_Movies <i class="fas fa-hashtag"></i> Shocking_Endings
            </p>
        </footer>
    </div>

    <script>
        // ===== DARK MODE FUNCTIONALITY =====
        const modeToggle = document.getElementById('modeToggle');
        const currentModeLabel = document.getElementById('currentModeLabel');
        const body = document.body;

        // Initialize theme
        function initializeTheme() {
            const savedMode = localStorage.getItem('siteTheme');
            const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
            
            if (savedMode === 'light' || (!savedMode && !prefersDark)) {
                body.classList.add('light-mode');
                body.classList.remove('dark-mode');
                modeToggle.checked = true;
                currentModeLabel.textContent = 'Light';
            } else {
                body.classList.add('dark-mode');
                body.classList.remove('light-mode');
                modeToggle.checked = false;
                currentModeLabel.textContent = 'Dark';
            }
        }

        // Toggle theme
        modeToggle.addEventListener('change', function() {
            if (this.checked) {
                body.classList.add('light-mode');
                body.classList.remove('dark-mode');
                currentModeLabel.textContent = 'Light';
                localStorage.setItem('siteTheme', 'light');
            } else {
                body.classList.add('dark-mode');
                body.classList.remove('light-mode');
                currentModeLabel.textContent = 'Dark';
                localStorage.setItem('siteTheme', 'dark');
            }
        });

        // ===== MOVIE DATA =====
        const movies = [
            {
                rank: 1, title: "The Sixth Sense", year: 1999,
                plot: "A child psychologist tries to help a boy who claims to see and communicate with the dead. The ending changes everything!",
                rating: 8.2, ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzUyNi00NGMwLTk3NTYtMDIyNTZmMzRlYmQyXkEyXkFqcGdeQXVyMTAwMzUyOTc@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 2, title: "Fight Club", year: 1999,
                plot: "An insomniac office worker forms an underground fight club with a mysterious soap salesman. But there's a big secret about his new friend.",
                rating: 8.8, ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 3, title: "The Prestige", year: 2006,
                plot: "Two stage magicians in London engage in a bitter rivalry, each trying to outdo the other. A terrifying secret lies behind their games.",
                rating: 8.5, ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_FMjpg_UX1000_.jpg"
            },
            // Add remaining 19 movies here...
        ];

        // ===== MOVIE RENDERING =====
        const movieGrid = document.getElementById('movieGrid');
        const searchInput = document.querySelector('.search-input');
        const searchButton = document.querySelector('.search-button');
        const noResults = document.getElementById('noResults');
        const pagination = document.getElementById('pagination');

        let currentPage = 1;
        const moviesPerPage = 6;
        let filteredMovies = [...movies];

        // Initialize everything
        document.addEventListener('DOMContentLoaded', () => {
            initializeTheme();
            renderMovies();
            setupSearch();
            
            // Add animation to social cards
            setTimeout(() => {
                document.querySelectorAll('.social-card').forEach((card, index) => {
                    card.style.animation = `fadeInUp 0.6s ease ${0.2 + (index * 0.1)}s backwards`;
                });
            }, 300);
        });

        function renderMovies() {
            movieGrid.innerHTML = '';
            const start = (currentPage - 1) * moviesPerPage;
            const end = start + moviesPerPage;
            const moviesToShow = filteredMovies.slice(start, end);

            if (moviesToShow.length === 0) {
                noResults.style.display = 'block';
                movieGrid.style.display = 'none';
            } else {
                noResults.style.display = 'none';
                movieGrid.style.display = 'grid';
                
                moviesToShow.forEach(movie => {
                    const card = document.createElement('div');
                    card.className = 'movie-card';
                    card.innerHTML = `
                        <div class="movie-rank">${movie.rank}</div>
                        <div class="movie-poster" style="background-image: url('${movie.poster}')"></div>
                        <div class="movie-info">
                            <div class="movie-title">${movie.title}</div>
                            <div class="movie-year">${movie.year}</div>
                            <div class="movie-plot">${movie.plot}</div>
                            <div class="movie-meta">
                                <div class="imdb-rating">⭐ ${movie.rating}/10</div>
                                <div class="age-rating ${movie.ageRating}">${
                                    movie.ageRating === 'pg13' ? 'PG-13' : 
                                    movie.ageRating === 'r' ? 'R (18+)' : 'G (All)'
                                }</div>
                            </div>
                        </div>
                    `;
                    movieGrid.appendChild(card);
                });
            }
        }

        function setupSearch() {
            searchButton.addEventListener('click', performSearch);
            searchInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') performSearch();
            });
            
            searchInput.addEventListener('input', () => {
                if (!searchInput.value.trim()) {
                    filteredMovies = [...movies];
                    currentPage = 1;
                    renderMovies();
                }
            });
        }

        function performSearch() {
            const term = searchInput.value.toLowerCase().trim();
            filteredMovies = movies.filter(movie => 
                movie.title.toLowerCase().includes(term) || 
                movie.year.toString().includes(term)
            );
            currentPage = 1;
            renderMovies();
        }
    </script>
</body>
</html>
