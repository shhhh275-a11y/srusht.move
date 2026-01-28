<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب - فیلمەکان کۆتاییەکی سەرسوڕهێنەریان هەیە">
    <meta name="keywords" content="فیلم, سینەما, کوردی, کۆتایی سەرسوڕهێنەر, فیلمی نایاب">
    <meta name="author" content="srusht.movies">
    <title>Shocking Ending Movies - سایتی فیلمی کوردی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #c77b63;
            --secondary: #1a1a2e;
            --accent: #f5c518;
            --text: #ffffff;
            --card-bg: rgba(255, 255, 255, 0.08);
            --shadow: rgba(0, 0, 0, 0.4);
        }

        body {
            font-family: 'Segoe UI', 'Tahoma', 'Geneva', 'Verdana', sans-serif;
            min-height: 100vh;
            background: var(--secondary);
            color: var(--text);
            overflow-x: hidden;
            position: relative;
        }

        .background-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(135deg, rgba(0,0,0,0.9) 0%, rgba(26,26,46,0.95) 100%),
                url('https://images.unsplash.com/photo-1489599809505-7c8e1a48bcc0?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
            opacity: 0.15;
            z-index: -2;
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

        /* Header Styles */
        .header {
            text-align: center;
            margin-bottom: 50px;
            padding: 30px 0;
        }

        .site-title {
            font-size: 1.8em;
            font-weight: 700;
            margin-bottom: 20px;
            padding: 20px 50px;
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 60px;
            display: inline-block;
            background: rgba(255,255,255,0.05);
            backdrop-filter: blur(10px);
            animation: fadeInDown 1s ease;
            box-shadow: 0 8px 25px var(--shadow);
        }

        .brand-name {
            font-size: 3.5em;
            font-weight: 900;
            text-shadow: 3px 3px 0px rgba(0,0,0,0.4), 0 0 30px rgba(255,255,255,0.3);
            background: linear-gradient(45deg, #ffffff, #e0e0e0, #a8a8a8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            animation: fadeIn 1.5s ease;
            letter-spacing: 3px;
        }

        /* Search Section */
        .search-section {
            max-width: 600px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 50px;
            padding: 5px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 25px var(--shadow);
            transition: all 0.3s ease;
        }

        .search-box:focus-within {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
        }

        .search-input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 18px 25px;
            color: var(--text);
            font-size: 1.1em;
            outline: none;
            font-family: inherit;
        }

        .search-input::placeholder {
            color: rgba(255,255,255,0.6);
        }

        .search-button {
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            border: none;
            border-radius: 50px;
            padding: 18px 35px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
            font-size: 1em;
        }

        .search-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(253,29,29,0.5);
        }

        /* Movie Grid */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 35px;
            padding: 30px 0;
        }

        .movie-card {
            background: var(--card-bg);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            overflow: hidden;
            box-shadow: 0 12px 40px var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.12);
            transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
            cursor: pointer;
            position: relative;
            animation: fadeInUp 0.7s ease backwards;
        }

        .movie-card:hover {
            transform: translateY(-15px) scale(1.03);
            box-shadow: 0 25px 70px rgba(0,0,0,0.6);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
        }

        .movie-rank {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.9);
            color: var(--accent);
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.5em;
            border: 3px solid var(--accent);
            box-shadow: 0 5px 25px rgba(245, 197, 24, 0.6);
            z-index: 10;
            animation: pulse 2.5s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        .movie-poster {
            width: 100%;
            height: 420px;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
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

        .movie-poster::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.08) 50%, transparent 70%);
            transform: rotate(45deg);
            animation: shine 4s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .movie-info {
            padding: 28px;
            background: rgba(0, 0, 0, 0.4);
        }

        .movie-title {
            font-size: 1.6em;
            font-weight: 700;
            margin-bottom: 12px;
            color: var(--text);
            text-shadow: 2px 2px 6px rgba(0,0,0,0.5);
            line-height: 1.3;
        }

        .movie-year {
            color: rgba(255, 255, 255, 0.85);
            font-size: 1em;
            margin-bottom: 14px;
            font-weight: 500;
        }

        .movie-plot {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.95em;
            line-height: 1.7;
            margin-bottom: 18px;
            text-align: justify;
            height: 85px;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
        }

        .movie-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .imdb-rating {
            background: linear-gradient(135deg, #f5c518 0%, #d4af37 100%);
            color: #000;
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: 700;
            font-size: 1.15em;
            box-shadow: 0 5px 20px rgba(245, 197, 24, 0.4);
            transition: all 0.3s ease;
        }

        .movie-card:hover .imdb-rating {
            transform: scale(1.08);
            box-shadow: 0 7px 25px rgba(245, 197, 24, 0.6);
        }

        .age-rating {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: 700;
            box-shadow: 0 5px 20px rgba(231, 76, 60, 0.4);
            transition: all 0.3s ease;
        }

        .age-rating.pg13 {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            box-shadow: 0 5px 20px rgba(52, 152, 219, 0.4);
        }

        .age-rating.g {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
            box-shadow: 0 5px 20px rgba(46, 204, 113, 0.4);
        }

        .movie-card:hover .age-rating {
            transform: scale(1.08);
        }

        /* Social Section */
        .social-section {
            text-align: center;
            margin: 50px auto;
        }

        .ig-banner {
            font-size: 1.15em;
            margin-bottom: 25px;
        }

        .ig-banner a {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            padding: 16px 35px;
            border-radius: 60px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: #fff;
            text-decoration: none;
            font-weight: 700;
            box-shadow: 0 0 25px rgba(253,29,29,.6), 0 6px 20px rgba(0,0,0,.3);
            transition: all 0.3s ease;
        }

        .ig-banner a:hover {
            transform: translateY(-4px) scale(1.06);
            box-shadow: 0 0 35px rgba(253,29,29,.8), 0 8px 25px rgba(0,0,0,.4);
        }

        /* Owner Section */
        .owner-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 35px;
            margin: 40px auto;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 12px 35px rgba(0,0,0,0.4);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .owner-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, #f5c518, #e74c3c, #3498db, #833ab4);
        }

        .owner-title {
            font-size: 1.2em;
            color: rgba(255,255,255,0.85);
            margin-bottom: 10px;
            font-weight: 600;
        }

        .owner-name {
            font-size: 2.2em;
            color: var(--accent);
            font-weight: 800;
            margin-bottom: 15px;
            text-shadow: 0 0 20px rgba(245, 197, 24, 0.8);
            letter-spacing: 1px;
        }

        .owner-subtitle {
            font-size: 1.05em;
            color: rgba(255,255,255,0.75);
            font-style: italic;
        }

        /* Footer */
        .footer {
            text-align: center;
            margin-top: 60px;
            padding: 30px;
            color: rgba(255,255,255,0.7);
            font-size: 0.95em;
            border-top: 1px solid rgba(255,255,255,0.15);
            background: rgba(0,0,0,0.2);
            border-radius: 20px 20px 0 0;
        }

        /* Animations */
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Staggered animation for movie cards */
        .movie-card:nth-child(1) { animation-delay: 0.1s; }
        .movie-card:nth-child(2) { animation-delay: 0.15s; }
        .movie-card:nth-child(3) { animation-delay: 0.2s; }
        .movie-card:nth-child(4) { animation-delay: 0.25s; }
        .movie-card:nth-child(5) { animation-delay: 0.3s; }
        .movie-card:nth-child(6) { animation-delay: 0.35s; }
        .movie-card:nth-child(7) { animation-delay: 0.4s; }
        .movie-card:nth-child(8) { animation-delay: 0.45s; }
        .movie-card:nth-child(9) { animation-delay: 0.5s; }
        .movie-card:nth-child(10) { animation-delay: 0.55s; }
        .movie-card:nth-child(11) { animation-delay: 0.6s; }
        .movie-card:nth-child(12) { animation-delay: 0.65s; }
        .movie-card:nth-child(13) { animation-delay: 0.7s; }
        .movie-card:nth-child(14) { animation-delay: 0.75s; }
        .movie-card:nth-child(15) { animation-delay: 0.8s; }
        .movie-card:nth-child(16) { animation-delay: 0.85s; }
        .movie-card:nth-child(17) { animation-delay: 0.9s; }
        .movie-card:nth-child(18) { animation-delay: 0.95s; }
        .movie-card:nth-child(19) { animation-delay: 1.0s; }
        .movie-card:nth-child(20) { animation-delay: 1.05s; }
        .movie-card:nth-child(21) { animation-delay: 1.1s; }
        .movie-card:nth-child(22) { animation-delay: 1.15s; }

        /* Responsive Design */
        @media (max-width: 1200px) {
            .container {
                padding: 15px;
            }
            .movie-grid {
                grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
                gap: 25px;
            }
        }

        @media (max-width: 768px) {
            .brand-name {
                font-size: 2.5em;
            }
            .site-title {
                font-size: 1.4em;
                padding: 16px 30px;
            }
            .movie-grid {
                grid-template-columns: 1fr;
                gap: 25px;
            }
            .gradient-circle {
                width: 400px;
                height: 400px;
            }
            .movie-poster {
                height: 380px;
            }
            .search-section {
                padding: 0 15px;
            }
            .search-input {
                padding: 15px 20px;
            }
            .search-button {
                padding: 15px 25px;
            }
        }

        @media (max-width: 480px) {
            .brand-name {
                font-size: 2em;
            }
            .site-title {
                font-size: 1.1em;
                padding: 12px 20px;
            }
            .movie-title {
                font-size: 1.4em;
            }
            .owner-name {
                font-size: 1.8em;
            }
            .ig-banner a {
                padding: 14px 25px;
                font-size: 0.9em;
            }
        }

        /* Utility Classes */
        .no-results {
            text-align: center;
            padding: 50px;
            font-size: 1.3em;
            color: rgba(255,255,255,0.7);
            grid-column: 1 / -1;
            display: none;
        }

        .pagination {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 40px 0;
            flex-wrap: wrap;
        }

        .page-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            padding: 12px 20px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .page-btn:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-3px);
        }

        .page-btn.active {
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="background-overlay"></div>
    <div class="gradient-circle"></div>

    <div class="container">
        <!-- Header -->
        <header class="header">
            <div class="site-title">🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</div>
            <h1 class="brand-name">Shocking Ending Movies</h1>
        </header>

        <!-- Search Section -->
        <section class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" placeholder="گەڕان بە ناوی فیلم...">
                <button class="search-button">
                    <i class="fas fa-search"></i> گەڕان
                </button>
            </div>
        </section>

        <!-- Social Media Banner -->
        <section class="social-section">
            <div class="ig-banner">
                <a href="https://www.instagram.com/9fi.99?igsh=MXQ0NG1icnc3Ym11NA==" target="_blank">
                    <i class="fab fa-instagram"></i>
                    سەردانی ئەکاونتی ئینستاگراممان بکە
                </a>
            </div>
        </section>

        <!-- Movie Grid -->
        <section class="movie-grid" id="movieGrid">
            <!-- Movie cards will be loaded here by JavaScript -->
        </section>

        <!-- No Results Message -->
        <div class="no-results" id="noResults">
            <i class="fas fa-film fa-2x" style="margin-bottom: 20px; opacity: 0.5;"></i>
            <p>هیچ فیلمێک بەم ناوە نەدۆزرایەوە!</p>
        </div>

        <!-- Pagination -->
        <div class="pagination" id="pagination">
            <!-- Pagination buttons will be added by JavaScript -->
        </div>

        <!-- Owner Section -->
        <section class="owner-box">
            <div class="owner-title">خاوەنی سایەت</div>
            <div class="owner-name">srusht.movies</div>
            <div class="owner-subtitle">ئەم ماڵپەرە خاوەنداریەتی دەکرێت لە لایەن srusht.movies</div>
        </section>

        <!-- Footer -->
        <footer class="footer">
            <p>© 2023 Shocking Ending Movies - هەموو مافەکان پارێزراون</p>
            <p style="margin-top: 10px; font-size: 0.9em; opacity: 0.6;">
                ئەم سایەتە بۆ خۆشی و ڕابواردنی هونەری سینەما دروست کراوە
            </p>
        </footer>
    </div>

    <script>
        // Movie data array
        const movies = [
            {
                rank: 1,
                title: "The Sixth Sense",
                year: 1999,
                plot: "دکتۆرێکی دەروونزانی هەوڵ دەدات منداڵێک یارمەتی بدات کە باوەڕی وایە دەتوانێت مردووان ببینێت و قسەیان لەگەڵ بکات. کۆتاییەکە هەموو شتێک دەگۆڕێت!",
                rating: 8.2,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzUyNi00NGMwLTk3NTYtMDIyNTZmMzRlYmQyXkEyXkFqcGdeQXVyMTAwMzUyOTc@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 2,
                title: "Fight Club",
                year: 1999,
                plot: "کارمەندێکی بێزار لە ژیانی دووبارەبوو ناسیاوی فرۆشەرێک دەکات و کلوبێکی شەڕی نهێنی دامەزرێنن. بەڵام نهێنییەکی گەورە لەبارەی ناسیاوە تازەکەی هەیە.",
                rating: 8.8,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 3,
                title: "The Prestige",
                year: 2006,
                plot: "دوو سیحربازی ناودار لە لەندەن دژایەتی توند دەکەن و هەریەکەیان هەوڵ دەدات ئەو یەکەی تر تێکبدات. نهێنیەکی ترسناک لە پشت یارییەکانیان شاراوەتەوە.",
                rating: 8.5,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 4,
                title: "Memento",
                year: 2000,
                plot: "پیاوێک یادەوەری کورتخایەنی هەیە و ناتوانێت یادەوەریی تازە دروست بکات. هەوڡ دەدات بکوژی ژنەکەی بدۆزێتەوە. چیرۆکەکە بە پێچەوانەوە دەڕوات!",
                rating: 8.4,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 5,
                title: "Oldboy",
                year: 2003,
                plot: "پیاوێک بۆ 15 ساڵ لە ژوورێکدا بە دیل دەگیرێت بەبێ هۆکار. دوای ئازادبوون، هەوڡ دەدات بزانێت کێ و بۆچی ئەمەی کردووە. کۆتاییەکەی ترسناکە!",
                rating: 8.4,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjgyMQ@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 6,
                title: "Gone Girl",
                year: 2014,
                plot: "ژنێک لە ڕۆژی ساڵیادی هاوسەرگیریدا ون دەبێت و مێردەکەی تۆمەتبار دەکرێت. بەڵام ڕاستییەکە تەواو جیاوازە لەوەی دەرکەوتووە.",
                rating: 8.1,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NzE3MjE@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 7,
                title: "The Machinist",
                year: 2004,
                plot: "کرێکارێکی کارگە بۆ ساڵێکە نەخەوتووە و یادەوەری لێ دەشێوێت. کەسێکی نامۆ دەردەکەوێت و ژیانی تێکدەدات. نهێنییەکی تاریک لە ڕابردوودا هەیە.",
                rating: 7.6,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BNjk1NzBlY2YtNjJmNi00YTVmLWI2OTgtNDUxNDE5NjUzZmE0XkEyXkFqcGdeQXVyNTc1NTQxODI@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 8,
                title: "The Others",
                year: 2001,
                plot: "دایکێک و دوو منداڵەکەی لە ماڵێکی تاریکدا دەژین. منداڵەکان نابێت تیشکیان لێ بکەوێت. ڕووداوی سەیر دەستپێدەکات و نهێنی ماڵەکە ئاشکرا دەبێت.",
                rating: 7.6,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTAxMDE4Mzc3ODNeQTJeQWpwZ15BbWU4MDY2Mjg4MDcx._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 9,
                title: "Shutter Island",
                year: 2010,
                plot: "پۆلیسێک بۆ تەحقیق لەسەر ونبوونی نەخۆسێکی دەروونی دەچێتە دوورگەیەکی تایبەت. بەڵام هەموو شتێک ئەوەندە سادە نییە کە دەردەکەوێت.",
                rating: 8.2,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BN2JmMjViMjMtZTM5Mi00ZGZkLTk5YzctZDg5MjFjZDE4NjNkXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 10,
                title: "The Usual Suspects",
                year: 1995,
                plot: "کەسێکی تاوانبار بەڵێن دەدات بە پۆلیس کە ئەگەر بەڵێنەکەی بەجێبهێنێت، ناوی تاوانبارێکی نەناسراو دەڵێت. کۆتاییەکە هەموو شتێک دەگۆڕێت!",
                rating: 8.5,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BMjEzMjczOTI2MV5BMl5BanBnXkFtZTgwOTUwMjI3NzE@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 11,
                title: "Se7en",
                year: 1995,
                plot: "دوو پۆلیس هەوڡ دەدەن کەسێک بدۆزنەوە کە کوشتنەکانی بەپێی حەوت تاوانە مەزنەکەی ئینجیل ئەنجام دەدات. کۆتاییەکە هۆشیارکەرەوەیە!",
                rating: 8.6,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BMTcyMzUyMzY1OF5BMl5BanBnXkFtZTcwNDQ4ODk1Mw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 12,
                title: "Inception",
                year: 2010,
                plot: "سەرکردەیەکی تیمی تایبەت کە خەون دەدزێت، دەست دەکات بە ئەرکێکی مەترسیدار: نەخشاندنی بیرۆکەیەک لە مێشکی کەسێک.",
                rating: 8.8,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMDliOTNhNmEtYTk2NS00NjFiLTkxMDItN2M1M2VmNWQzMjhlXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 13,
                title: "The Social Network",
                year: 2010,
                plot: "چیرۆکی دروستکردنی فەیسبووک و کێشەکانی نێوان دامەزرێنەرەکانی. کۆتاییەکە ڕوونی دەکاتەوە کە سەرکەوتن بە نرخی چیمە.",
                rating: 7.7,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTk4ODQzNDY3Ml5BMl5BanBnXkFtZTcwODA0NTM4Nw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 14,
                title: "The Dark Knight",
                year: 2008,
                plot: "بەتمان هەوڡ دەدات شاری گۆتەم ڕزگار بکات لە جۆکەر، کەسێکی شێت کە پلانی تێکدانی شاری هەیە. کۆتاییەکە گۆڕانکاری گەورە دروست دەکات.",
                rating: 9.0,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 15,
                title: "Avatar",
                year: 2009,
                plot: "سەربازێک لە جیهانێکی تر دەچێتە ناو لەشی بوونەوەرێکی تر و دەبێتە هۆی گۆڕانکارییەکی مەزن لە ژیانی خۆی و ئەو جیهانە.",
                rating: 7.8,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 16,
                title: "Joker",
                year: 2019,
                plot: "کەسێکی کۆمیدی دەبێتە جۆکەر و دەست دەکات بە جێبەجێکردنی پلانێکی ترسناک. کۆتاییەکە هەموو کەسێک سەرسام دەکات.",
                rating: 8.4,
                ageRating: "r",
                poster: "https://m.media-amazon.com/images/M/MV5BMTk2NTI1MTU4N15BMl5BanBnXkFtZTcwODg0OTY0Nw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 17,
                title: "Interstellar",
                year: 2014,
                plot: "زانایەک پڕۆژەیەکی تایبەت دروست دەکات بۆ گەڕانەوەی کچەکەی. بەڵام پڕۆژەکە زۆر مەترسیدارترە لەوەی کە خەیاڵی دەکرد.",
                rating: 8.6,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTM0MDgwNjMyMl5BMl5BanBnXkFtZTcwNTg0NzU1Ng@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 18,
                title: "Venom",
                year: 2018,
                plot: "ڕۆژنامەنووسێک دەبێتە میواندارێکی بوونەوەرێکی دەرەکی و دەبێتە هۆی گۆڕانکارییەکی مەزن لە ژیانی.",
                rating: 6.7,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTY3NjY0MTQ0Nl5BMl5BanBnXkFtZTcwMDQzMzQ2Mw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 19,
                title: "Avengers: Endgame",
                year: 2019,
                plot: "کۆمەڵێک قارەمان هەوڡ دەدەن جیهان ڕزگار بکەن لە تەنانۆس. بەڵام ڕێگەکە زۆر مەترسیدارە و کۆتاییەکە گۆڕانکاری گەورە دروست دەکات.",
                rating: 8.4,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTc5MDE2ODcwNV5BMl5BanBnXkFtZTgwMzI2NzQ2NzM@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 20,
                title: "Iron Man",
                year: 2008,
                plot: "بلیمەتێکی بەهرەدار دەبێتە قارەمانێکی سەربەخۆ دوای ئەوەی ڕزگاری لە تاوانبارێک دەبێت. بەڵام ڕووبەڕووبوونەوەی گەورە هەر هەیە.",
                rating: 7.9,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTczNTI2ODUwOF5BMl5BanBnXkFtZTcwMTU0NTIzMw@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 21,
                title: "The Lion King",
                year: 1994,
                plot: "شێرێکی گەنج دەبێتە پاشا دوای مردنی باوکی. بەڵام مامی پلانێکی خراپ دادەنێت بۆ وەرگرتنی تەختی پاشایەتی.",
                rating: 8.5,
                ageRating: "g",
                poster: "https://m.media-amazon.com/images/M/MV5BMTM4NzQ0OTYyOF5BMl5BanBnXkFtZTcwMDkyNjQyMg@@._V1_FMjpg_UX1000_.jpg"
            },
            {
                rank: 22,
                title: "The Maze Runner",
                year: 2014,
                plot: "کەسێک لە جیهانێکی پۆست-ئەپۆکالیپتیکدا هەوڡ دەدات ڕزگاری خەڵک بکات لە نەهێشتنی تەواو. بەڵام ڕێگەکە زۆر مەترسیدارە.",
                rating: 6.8,
                ageRating: "pg13",
                poster: "https://m.media-amazon.com/images/M/MV5BMTY5OTU0OTc2NV5BMl5BanBnXkFtZTcwMzU4MDcyMQ@@._V1_FMjpg_UX1000_.jpg"
            }
        ];

        // DOM Elements
        const movieGrid = document.getElementById('movieGrid');
        const searchInput = document.querySelector('.search-input');
        const searchButton = document.querySelector('.search-button');
        const noResults = document.getElementById('noResults');
        const pagination = document.getElementById('pagination');

        // Pagination variables
        let currentPage = 1;
        const moviesPerPage = 6;
        let filteredMovies = [...movies];

        // Initialize the website
        document.addEventListener('DOMContentLoaded', () => {
            renderMovies();
            setupPagination();
            setupSearch();
            setupMovieClickEvents();
        });

        // Render movies based on current page
        function renderMovies() {
            movieGrid.innerHTML = '';
            
            const startIndex = (currentPage - 1) * moviesPerPage;
            const endIndex = startIndex + moviesPerPage;
            const moviesToShow = filteredMovies.slice(startIndex, endIndex);
            
            if (moviesToShow.length === 0) {
                noResults.style.display = 'block';
            } else {
                noResults.style.display = 'none';
                
                moviesToShow.forEach(movie => {
                    const movieCard = document.createElement('div');
                    movieCard.className = 'movie-card';
                    movieCard.dataset.id = movie.rank;
                    
                    // Get age rating text
                    let ageRatingText = '';
                    let ageRatingClass = '';
                    switch(movie.ageRating) {
                        case 'pg13':
                            ageRatingText = 'PG-13';
                            ageRatingClass = 'pg13';
                            break;
                        case 'r':
                            ageRatingText = 'R (18+)';
                            ageRatingClass = '';
                            break;
                        case 'g':
                            ageRatingText = 'G (All Ages)';
                            ageRatingClass = 'g';
                            break;
                        default:
                            ageRatingText = 'PG-13';
                            ageRatingClass = 'pg13';
                    }
                    
                    movieCard.innerHTML = `
                        <div class="movie-rank">${movie.rank}</div>
                        <div class="movie-poster" style="background-image: url('${movie.poster}')"></div>
                        <div class="movie-info">
                            <div class="movie-title">${movie.title}</div>
                            <div class="movie-year">${movie.year}</div>
                            <div class="movie-plot">${movie.plot}</div>
                            <div class="movie-meta">
                                <div class="imdb-rating">⭐ ${movie.rating}/10</div>
                                <div class="age-rating ${ageRatingClass}">${ageRatingText}</div>
                            </div>
                        </div>
                    `;
                    
                    movieGrid.appendChild(movieCard);
                });
            }
        }

        // Setup pagination
        function setupPagination() {
            const totalPages = Math.ceil(filteredMovies.length / moviesPerPage);
            
            if (totalPages <= 1) {
                pagination.style.display = 'none';
                return;
            }
            
            pagination.style.display = 'flex';
            pagination.innerHTML = '';
            
            // Previous button
            const prevButton = document.createElement('button');
            prevButton.className = 'page-btn';
            prevButton.innerHTML = '<i class="fas fa-chevron-right"></i> پێشوو';
            prevButton.disabled = currentPage === 1;
            prevButton.addEventListener('click', () => {
                if (currentPage > 1) {
                    currentPage--;
                    renderMovies();
                    setupPagination();
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                }
            });
            pagination.appendChild(prevButton);
            
            // Page buttons
            for (let i = 1; i <= totalPages; i++) {
                const pageButton = document.createElement('button');
                pageButton.className = `page-btn ${i === currentPage ? 'active' : ''}`;
                pageButton.textContent = i;
                pageButton.addEventListener('click', () => {
                    currentPage = i;
                    renderMovies();
                    setupPagination();
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                });
                pagination.appendChild(pageButton);
            }
            
            // Next button
            const nextButton = document.createElement('button');
            nextButton.className = 'page-btn';
            nextButton.innerHTML = 'داهاتوو <i class="fas fa-chevron-left"></i>';
            nextButton.disabled = currentPage === totalPages;
            nextButton.addEventListener('click', () => {
                if (currentPage < totalPages) {
                    currentPage++;
                    renderMovies();
                    setupPagination();
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                }
            });
            pagination.appendChild(nextButton);
        }

        // Setup search functionality
        function setupSearch() {
            // Search button click
            searchButton.addEventListener('click', performSearch);
            
            // Enter key in search input
            searchInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    performSearch();
                }
            });
            
            // Clear search when input is empty
            searchInput.addEventListener('input', (e) => {
                if (!e.target.value.trim()) {
                    filteredMovies = [...movies];
                    currentPage = 1;
                    renderMovies();
                    setupPagination();
                }
            });
        }

        // Perform search
        function performSearch() {
            const searchTerm = searchInput.value.toLowerCase().trim();
            
            if (!searchTerm) {
                filteredMovies = [...movies];
            } else {
                filteredMovies = movies.filter(movie => 
                    movie.title.toLowerCase().includes(searchTerm) || 
                    movie.year.toString().includes(searchTerm) ||
                    movie.plot.toLowerCase().includes(searchTerm)
                );
            }
            
            currentPage = 1;
            renderMovies();
            setupPagination();
        }

        // Setup movie click events
        function setupMovieClickEvents() {
            // Using event delegation for movie cards
            movieGrid.addEventListener('click', (e) => {
                const movieCard = e.target.closest('.movie-card');
                if (movieCard) {
                    const movieId = movieCard.dataset.id;
                    const movie = movies.find(m => m.rank == movieId);
                    
                    if (movie) {
                        // Create modal or alert
                        const modal = document.createElement('div');
                        modal.style.cssText = `
                            position: fixed;
                            top: 0;
                            left: 0;
                            width: 100%;
                            height: 100%;
                            background: rgba(0,0,0,0.8);
                            display: flex;
                            justify-content: center;
                            align-items: center;
                            z-index: 1000;
                            backdrop-filter: blur(10px);
                        `;
                        
                        modal.innerHTML = `
                            <div style="
                                background: rgba(26,26,46,0.95);
                                border-radius: 25px;
                                padding: 30px;
                                max-width: 500px;
                                width: 90%;
                                border: 1px solid rgba(255,255,255,0.2);
                                box-shadow: 0 20px 60px rgba(0,0,0,0.7);
                                position: relative;
                            ">
                                <button style="
                                    position: absolute;
                                    top: 15px;
                                    left: 15px;
                                    background: transparent;
                                    border: none;
                                    color: white;
                                    font-size: 1.5em;
                                    cursor: pointer;
                                ">×</button>
                                <h2 style="color: #f5c518; margin-bottom: 15px; text-align: center;">${movie.title}</h2>
                                <div style="text-align: center; margin-bottom: 20px;">
                                    <span style="background: #f5c518; color: black; padding: 5px 15px; border-radius: 20px; font-weight: bold;">
                                        Rating: ${movie.rating}/10
                                    </span>
                                    <span style="margin-right: 15px;"></span>
                                    <span style="background: #3498db; color: white; padding: 5px 15px; border-radius: 20px; font-weight: bold;">
                                        Year: ${movie.year}
                                    </span>
                                </div>
                                <p style="color: rgba(255,255,255,0.9); line-height: 1.7; text-align: justify;">
                                    ${movie.plot}
                                </p>
                                <div style="text-align: center; margin-top: 25px;">
                                    <button style="
                                        background: linear-gradient(45deg, #833ab4, #fd1d1d);
                                        border: none;
                                        padding: 12px 30px;
                                        border-radius: 50px;
                                        color: white;
                                        font-weight: bold;
                                        cursor: pointer;
                                        margin-top: 15px;
                                    ">دەستنیشانکردنی فیلم</button>
                                </div>
                            </div>
                        `;
                        
                        document.body.appendChild(modal);
                        
                        // Close modal when clicking close button or outside
                        modal.addEventListener('click', (e) => {
                            if (e.target === modal || e.target.textContent === '×') {
                                document.body.removeChild(modal);
                            }
                        });
                        
                        // Close with Escape key
                        document.addEventListener('keydown', function closeModal(e) {
                            if (e.key === 'Escape' && document.body.contains(modal)) {
                                document.body.removeChild(modal);
                                document.removeEventListener('keydown', closeModal);
                            }
                        });
                    }
                }
            });
        }

        // Add some interactivity to movie cards
        document.addEventListener('mousemove', (e) => {
            const cards = document.querySelectorAll('.movie-card');
            cards.forEach(card => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                
                card.style.setProperty('--mouse-x', `${x}px`);
                card.style.setProperty('--mouse-y', `${y}px`);
            });
        });
    </script>
</body>
</html>