<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فیلمەکانی کۆتایی شۆککەر - Srusht Movies</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
            background: #2c1810;
        }
        
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.6));
            z-index: -2;
        }
        
        body::after {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, transparent 0%, rgba(0,0,0,0.5) 100%);
            z-index: -1;
        }
        
        .background-image {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 500px;
            height: 500px;
            border-radius: 50%;
            background-image: url('data:image/svg+xml,%3Csvg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 800"%3E%3Cdefs%3E%3CradialGradient id="bg"%3E%3Cstop offset="0%25" stop-color="%23c77b63"/%3E%3Cstop offset="100%25" stop-color="%238b5a4a"/%3E%3C/radialGradient%3E%3C/defs%3E%3Ccircle cx="400" cy="400" r="400" fill="url(%23bg)"/%3E%3C/svg%3E');
            background-size: cover;
            background-position: center;
            opacity: 0.3;
            filter: blur(80px);
            z-index: -1;
            animation: float 20s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -48%) scale(1.1); }
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        
        .header-section {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .main-title {
            font-family: 'Arial', sans-serif;
            font-size: 1.5em;
            font-weight: 600;
            letter-spacing: 2px;
            margin-bottom: 20px;
            padding: 18px 40px;
            border: 2px solid rgba(255,255,255,0.6);
            border-radius: 50px;
            display: inline-block;
            background: rgba(255,255,255,0.05);
            backdrop-filter: blur(5px);
            text-transform: uppercase;
            color: white;
            animation: fadeInDown 1s ease;
        }
        
        .brand-name {
            font-family: 'Arial Black', 'Arial', sans-serif;
            font-size: 3em;
            font-weight: 900;
            letter-spacing: 5px;
            color: white;
            text-shadow: 5px 5px 0px rgba(0,0,0,0.3), 0 0 40px rgba(255,255,255,0.5);
            text-transform: uppercase;
            background: linear-gradient(45deg, #ffffff, #f0f0f0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            animation: fadeIn 1.5s ease;
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
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            padding: 20px 0;
        }
        
        .movie-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 8px 32px rgba(0,0,0,0.3);
            border: 1px solid rgba(255, 255, 255, 0.18);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            position: relative;
            animation: fadeInUp 0.6s ease backwards;
        }
        
        .movie-card:nth-child(1) { animation-delay: 0.1s; }
        .movie-card:nth-child(2) { animation-delay: 0.2s; }
        .movie-card:nth-child(3) { animation-delay: 0.3s; }
        .movie-card:nth-child(4) { animation-delay: 0.4s; }
        .movie-card:nth-child(5) { animation-delay: 0.5s; }
        .movie-card:nth-child(6) { animation-delay: 0.6s; }
        .movie-card:nth-child(7) { animation-delay: 0.7s; }
        .movie-card:nth-child(8) { animation-delay: 0.8s; }
        .movie-card:nth-child(9) { animation-delay: 0.9s; }
        .movie-card:nth-child(10) { animation-delay: 1.0s; }
        .movie-card:nth-child(11) { animation-delay: 1.1s; }
        .movie-card:nth-child(12) { animation-delay: 1.2s; }
        
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
        
        .movie-card:hover {
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            background: rgba(255, 255, 255, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .movie-poster {
            width: 100%;
            height: 400px;
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.3em;
            text-align: center;
            padding: 20px;
            font-weight: bold;
            position: relative;
            overflow: hidden;
        }
        
        .movie-poster::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                45deg,
                transparent 30%,
                rgba(255, 255, 255, 0.1) 50%,
                transparent 70%
            );
            transform: rotate(45deg);
            animation: shine 3s infinite;
        }
        
        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }
        
        .movie-info {
            padding: 25px;
            background: rgba(0, 0, 0, 0.3);
        }
        
        .movie-title {
            font-size: 1.5em;
            font-weight: bold;
            margin-bottom: 10px;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        
        .movie-year {
            color: rgba(255, 255, 255, 0.8);
            font-size: 0.95em;
            margin-bottom: 12px;
        }
        
        .movie-plot {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.9em;
            line-height: 1.6;
            margin-bottom: 15px;
            text-align: justify;
        }
        
        .rating-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .imdb-rating {
            background: linear-gradient(135deg, #f5c518 0%, #e6b800 100%);
            color: #000;
            padding: 10px 18px;
            border-radius: 12px;
            font-weight: bold;
            font-size: 1.1em;
            box-shadow: 0 4px 15px rgba(245, 197, 24, 0.4);
            transition: all 0.3s ease;
        }
        
        .movie-card:hover .imdb-rating {
            transform: scale(1.05);
            box-shadow: 0 6px 20px rgba(245, 197, 24, 0.6);
        }
        
        .age-rating {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            padding: 10px 18px;
            border-radius: 12px;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(231, 76, 60, 0.4);
            transition: all 0.3s ease;
        }
        
        .age-rating.pg13 {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            box-shadow: 0 4px 15px rgba(52, 152, 219, 0.4);
        }
        
        .movie-card:hover .age-rating {
            transform: scale(1.05);
        }
        
        .rank {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0,0,0,0.85);
            color: #f5c518;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.4em;
            border: 3px solid #f5c518;
            box-shadow: 0 4px 20px rgba(245, 197, 24, 0.5);
            z-index: 10;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        /*----- خاونی سایەت / ئینستاگرام -----*/
        .social-section {
            text-align: center;
            margin: 30px auto;
        }
        
        .ig-banner {
            font-size: 1.1em;
            margin-bottom: 20px;
        }
        
        .ig-banner a {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 12px 28px;
            border-radius: 50px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            box-shadow: 0 0 20px rgba(253,29,29,.55), 0 4px 18px rgba(0,0,0,.25);
            transition: transform .25s, box-shadow .25s;
        }
        
        .ig-banner a:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 0 30px rgba(253,29,29,.75), 0 6px 22px rgba(0,0,0,.35);
        }
        
        .ig-banner .ig-icon {
            font-size: 1.4em;
        }
        
        .owner-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 25px;
            margin: 30px auto;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px rgba(0,0,0,0.3);
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
            height: 4px;
            background: linear-gradient(90deg, #f5c518, #e74c3c, #3498db);
        }
        
        .owner-title {
            font-size: 1.1em;
            color: rgba(255,255,255,0.8);
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .owner-name {
            font-size: 2em;
            color: #f5c518;
            font-weight: bold;
            margin-bottom: 15px;
            text-shadow: 0 0 15px rgba(245, 197, 24, 0.7);
        }
        
        .owner-subtitle {
            font-size: 1em;
            color: rgba(255,255,255,0.7);
            font-style: italic;
        }
        
        .footer {
            text-align: center;
            margin-top: 50px;
            padding: 20px;
            color: rgba(255,255,255,0.7);
            font-size: 0.9em;
            border-top: 1px solid rgba(255,255,255,0.1);
        }
        
        @media (max-width: 768px) {
            .main-title { font-size: 1.2em; }
            .brand-name { font-size: 2.2em; }
            .movie-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            .background-image {
                width: 300px;
                height: 300px;
            }
            .social-section {
                margin: 20px auto;
            }
            .owner-box {
                max-width: 90%;
                padding: 20px;
            }
            .owner-name {
                font-size: 1.6em;
            }
        }
    </style>
</head>
<body>
    <div class="background-image"></div>
    
    <div class="container">
        <div class="header-section">
            <div class="main-title">🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</div>
            <div class="brand-name">Srusht Movies</div>
        </div>
        
        <!-- بەشی ئینستاگرام -->
        <div class="social-section">
            <div class="ig-banner">
                <a href="https://www.instagram.com/9fi.99?igsh=MXQ0NG1icnc3Ym11NA==" target="_blank">
                    <span class="ig-icon">📱</span>
                    سەردانی ئەکاونتی ئینستاگراممان بکە
                </a>
            </div>
        </div>
        
        <div class="movie-grid">
            <!-- فیلم 1 -->
            <div class="movie-card">
                <div class="rank">1</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzUyNi00NGMwLTk3NTYtMDIyNTZmMzRlYmQyXkEyXkFqcGdeQXVyMTAwMzUyOTc@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">The Sixth Sense</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">The Sixth Sense</div>
                    <div class="movie-year">1999</div>
                    <div class="movie-plot">دکتۆرێکی دەروونزانی هەوڵ دەدات منداڵێک یارمەتی بدات کە باوەڕی وایە دەتوانێت مردووان ببینێت و قسەیان لەگەڵ بکات. کۆتاییەکە هەموو شتێک دەگۆڕێت!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.2/10</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 2 -->
            <div class="movie-card">
                <div class="rank">2</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Fight Club</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Fight Club</div>
                    <div class="movie-year">1999</div>
                    <div class="movie-plot">کارمەندێکی بێزار لە ژیانی دووبارەبوو ناسیاوی فرۆشەرێک دەکات و کلوبێکی شەڕی نهێنی دامەزرێنن. بەڵام نهێنییەکی گەورە لەبارەی ناسیاوە تازەکەی هەیە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.8/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 3 -->
            <div class="movie-card">
                <div class="rank">3</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">The Prestige</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">The Prestige</div>
                    <div class="movie-year">2006</div>
                    <div class="movie-plot">دوو سیحربازی ناودار لە لەندەن دژایەتی توند دەکەن و هەریەکەیان هەوڵ دەدات ئەو یەکەی تر تێکبدات. نهێنیەکی ترسناک لە پشت یارییەکانیان شاراوەتەوە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.5/10</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 4 -->
            <div class="movie-card">
                <div class="rank">4</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Memento</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Memento</div>
                    <div class="movie-year">2000</div>
                    <div class="movie-plot">پیاوێک یادەوەری کورتخایەنی هەیە و ناتوانێت یادەوەریی تازە دروست بکات. هەوڵ دەدات بکوژی ژنەکەی بدۆزێتەوە. چیرۆکەکە بە پێچەوانەوە دەڕوات!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.4/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 5 -->
            <div class="movie-card">
                <div class="rank">5</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjgyMQ@@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Oldboy</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Oldboy</div>
                    <div class="movie-year">2003 (کۆریایی)</div>
                    <div class="movie-plot">پیاوێک بۆ 15 ساڵ لە ژوورێکدا بە دیل دەگیرێت بەبێ هۆکار. دوای ئازادبوون، هەوڵ دەدات بزانێت کێ و بۆچی ئەمەی کردووە. کۆتاییەکەی ترسناکە!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.4/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 6 -->
            <div class="movie-card">
                <div class="rank">6</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NzE3MjE@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Gone Girl</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Gone Girl</div>
                    <div class="movie-year">2014</div>
                    <div class="movie-plot">ژنێک لە ڕۆژی ساڵیادی هاوسەرگیریدا ون دەبێت و مێردەکەی تۆمەتبار دەکرێت. بەڵام ڕاستییەکە تەواو جیاوازە لەوەی دەرکەوتووە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.1/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 7 -->
            <div class="movie-card">
                <div class="rank">7</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BNjk1NzBlY2YtNjJmNi00YTVmLWI2OTgtNDUxNDE5NjUzZmE0XkEyXkFqcGdeQXVyNTc1NTQxODI@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">The Machinist</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">The Machinist</div>
                    <div class="movie-year">2004</div>
                    <div class="movie-plot">کرێکارێکی کارگە بۆ ساڵێکە نەخەوتووە و یادەوەری لێ دەشێوێت. کەسێکی نامۆ دەردەکەوێت و ژیانی تێکدەدات. نهێنییەکی تاریک لە ڕابردوویدا هەیە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 7.6/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 8 -->
            <div class="movie-card">
                <div class="rank">8</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTAxMDE4Mzc3ODNeQTJeQWpwZ15BbWU4MDY2Mjg4MDcx._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">The Others</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">The Others</div>
                    <div class="movie-year">2001</div>
                    <div class="movie-plot">دایکێک و دوو منداڵەکەی لە ماڵێکی تاریکدا دەژین. منداڵەکان نابێت تیشکیان لێ بکەوێت. ڕووداوی سەیر دەستپێدەکات و نهێنی ماڵەکە ئاشکرا دەبێت.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 7.6/10</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 9 -->
            <div class="movie-card">
                <div class="rank">9</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BN2JmMjViMjMtZTM5Mi00ZGZkLTk5YzctZDg5MjFjZDE4NjNkXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Shutter Island</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Shutter Island</div>
                    <div class="movie-year">2010</div>
                    <div class="movie-plot">پۆلیسێک بۆ تەحقیق لەسەر ونبوونی نەخۆسێکی دەروونی دەچێتە دوورگەیەکی تایبەت. بەڵام هەموو شتێک ئەوەندە سادە نییە کە دەردەکەوێت.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.2/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 10 -->
            <div class="movie-card">
                <div class="rank">10</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMjEzMjczOTI2MV5BMl5BanBnXkFtZTgwOTUwMjI3NzE@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">The Usual Suspects</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">The Usual Suspects</div>
                    <div class="movie-year">1995</div>
                    <div class="movie-plot">کەسێکی تاوانبار بەڵێن دەدات بە پۆلیس کە ئەگەر بەڵێنەکەی بەجێبهێنێت، ناوی تاوانبارێکی نەناسراو دەڵێت. کۆتاییەکە هەموو شتێک دەگۆڕێت!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.5/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 11 -->
            <div class="movie-card">
                <div class="rank">11</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTcyMzUyMzY1OF5BMl5BanBnXkFtZTcwNDQ4ODk1Mw@@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Se7en</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Se7en</div>
                    <div class="movie-year">1995</div>
                    <div class="movie-plot">دوو پۆلیس هەوڵ دەدەن کەسێک بدۆزنەوە کە کوشتنەکانی بەپێی حەوت تاوانە مەزنەکەی ئینجیل ئەنجام دەدات. کۆتاییەکە هۆشیارکەرەوەیە!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.6/10</div>
                        <div class="age-rating">R (18+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 12 -->
            <div class="movie-card">
                <div class="rank">12</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMDliOTNhNmEtYTk2NS00NjFiLTkxMDItN2M1M2VmNWQzMjhlXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_FMjpg_UX1000_.jpg')">
                    <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px;">Inception</div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">Inception</div>
                    <div class="movie-year">2010</div>
                    <div class="movie-plot">سەرکردەیەکی تیمی تایبەت کە خەون دەدزێت، دەست دەکات بە ئەرکێکی مەترسیدار: نەخشاندنی بیرۆکەیەک لە مێشکی کەسێک.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ 8.8/10</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- بەشی خاوەنی سایەت -->
        <div class="owner-box">
            <div class="owner-title">خاوەنی سایەت</div>
            <div class="owner-name">srusht.movies</div>
            <div class="owner-subtitle">ئەم ماڵپەرە خاوەنداریەتی دەکرێت لە لایەن srusht.movies</div>
        </div>
        
        <div class="footer">
            © 2023 Srusht Movies - هەموو مافەکان پارێزراون
        </div>
    </div>

    <script>
        // کۆدی جاڤاسکریپت بۆ کاراکردنی زیاتر
        document.addEventListener('DOMContentLoaded', function() {
            const movieCards = document.querySelectorAll('.movie-card');
            
            movieCards.forEach(card => {
                card.addEventListener('click', function() {
                    const movieTitle = this.querySelector('.movie-title').textContent;
                    alert(`فیلمی "${movieTitle}" هەڵبژێردرا!`);
                });
            });
        });
    </script>
</body>
</html>
