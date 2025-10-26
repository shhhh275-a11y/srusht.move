<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فیلمەکانی کۆتایی شۆککەر - فیلمی نایاب</title>
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
            background: #1a1a2e;
        }
        
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(0,0,0,0.8) 0%, rgba(26,26,46,0.9) 100%);
            z-index: -2;
        }
        
        .background-image {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 600px;
            height: 600px;
            border-radius: 50%;
            background: radial-gradient(circle, #c77b63 0%, #8b5a4a 50%, transparent 70%);
            opacity: 0.15;
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
        
        .header-section {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px 0;
        }
        
        .main-title {
            font-size: 1.8em;
            font-weight: 700;
            margin-bottom: 15px;
            padding: 20px 50px;
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 60px;
            display: inline-block;
            background: rgba(255,255,255,0.05);
            backdrop-filter: blur(10px);
            color: white;
            animation: fadeInDown 1s ease;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }
        
        .brand-name {
            font-size: 3.5em;
            font-weight: 900;
            color: white;
            text-shadow: 3px 3px 0px rgba(0,0,0,0.4), 0 0 30px rgba(255,255,255,0.3);
            background: linear-gradient(45deg, #ffffff, #e0e0e0, #a8a8a8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 5px;
            animation: fadeIn 1.5s ease;
            letter-spacing: 3px;
        }
        
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-40px);
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
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 35px;
            padding: 20px 0;
        }
        
        .movie-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            overflow: hidden;
            box-shadow: 0 12px 40px rgba(0,0,0,0.4);
            border: 1px solid rgba(255, 255, 255, 0.12);
            transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
            cursor: pointer;
            position: relative;
            animation: fadeInUp 0.7s ease backwards;
        }
        
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
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .movie-card:hover {
            transform: translateY(-18px) scale(1.03);
            box-shadow: 0 25px 70px rgba(0,0,0,0.6);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
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
            background: linear-gradient(
                45deg,
                transparent 30%,
                rgba(255, 255, 255, 0.08) 50%,
                transparent 70%
            );
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
            color: #fff;
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
        
        .rating-container {
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
        
        .movie-card:hover .age-rating {
            transform: scale(1.08);
        }
        
        .rank {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.9);
            color: #f5c518;
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.5em;
            border: 3px solid #f5c518;
            box-shadow: 0 5px 25px rgba(245, 197, 24, 0.6);
            z-index: 10;
            animation: pulse 2.5s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }
        
        /*----- خاونی سایەت / ئینستاگرام -----*/
        .social-section {
            text-align: center;
            margin: 40px auto;
        }
        
        .ig-banner {
            font-size: 1.15em;
            margin-bottom: 25px;
        }
        
        .ig-banner a {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 14px 32px;
            border-radius: 60px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: #fff;
            text-decoration: none;
            font-weight: 700;
            box-shadow: 0 0 25px rgba(253,29,29,.6), 0 6px 20px rgba(0,0,0,.3);
            transition: transform .3s, box-shadow .3s;
        }
        
        .ig-banner a:hover {
            transform: translateY(-4px) scale(1.06);
            box-shadow: 0 0 35px rgba(253,29,29,.8), 0 8px 25px rgba(0,0,0,.4);
        }
        
        .ig-banner .ig-icon {
            font-size: 1.5em;
        }
        
        .owner-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 30px;
            margin: 35px auto;
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
            color: #f5c518;
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
        
        .footer {
            text-align: center;
            margin-top: 60px;
            padding: 25px;
            color: rgba(255,255,255,0.7);
            font-size: 0.95em;
            border-top: 1px solid rgba(255,255,255,0.15);
        }
        
        @media (max-width: 768px) {
            .main-title { 
                font-size: 1.4em; 
                padding: 16px 30px;
            }
            .brand-name { 
                font-size: 2.5em; 
            }
            .movie-grid {
                grid-template-columns: 1fr;
                gap: 25px;
            }
            .background-image {
                width: 400px;
                height: 400px;
            }
            .social-section {
                margin: 30px auto;
            }
            .owner-box {
                max-width: 90%;
                padding: 25px;
            }
            .owner-name {
                font-size: 1.8em;
            }
            .movie-poster {
                height: 380px;
            }
        }
    </style>
</head>
<body>
    <div class="background-image"></div>
    
    <div class="container">
        <div class="header-section">
            <div class="main-title">🎬 سەرنجڕاکێشترین فیلمەکانی کۆتایی شۆککەر</div>
            <div class="brand-name">فیلمی نایاب</div>
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
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzUyNi00NGMwLTk3NTYtMDIyNTZmMzRlYmQyXkEyXkFqcGdeQXVyMTAwMzUyOTc@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">هەستی شەشەم</div>
                    <div class="movie-year">١٩٩٩</div>
                    <div class="movie-plot">دکتۆرێکی دەروونزانی هەوڵ دەدات منداڵێک یارمەتی بدات کە باوەڕی وایە دەتوانێت مردووان ببینێت و قسەیان لەگەڵ بکات. کۆتاییەکە هەموو شتێک دەگۆڕێت!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٢/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 2 -->
            <div class="movie-card">
                <div class="rank">2</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">کڵەبی شەڕ</div>
                    <div class="movie-year">١٩٩٩</div>
                    <div class="movie-plot">کارمەندێکی بێزار لە ژیانی دووبارەبوو ناسیاوی فرۆشەرێک دەکات و کلوبێکی شەڕی نهێنی دامەزرێنن. بەڵام نهێنییەکی گەورە لەبارەی ناسیاوە تازەکەی هەیە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٨/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 3 -->
            <div class="movie-card">
                <div class="rank">3</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">پێشکەوتن</div>
                    <div class="movie-year">٢٠٠٦</div>
                    <div class="movie-plot">دوو سیحربازی ناودار لە لەندەن دژایەتی توند دەکەن و هەریەکەیان هەوڵ دەدات ئەو یەکەی تر تێکبدات. نهێنیەکی ترسناک لە پشت یارییەکانیان شاراوەتەوە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٥/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 4 -->
            <div class="movie-card">
                <div class="rank">4</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">یادەوەری</div>
                    <div class="movie-year">٢٠٠٠</div>
                    <div class="movie-plot">پیاوێک یادەوەری کورتخایەنی هەیە و ناتوانێت یادەوەریی تازە دروست بکات. هەوڵ دەدات بکوژی ژنەکەی بدۆزێتەوە. چیرۆکەکە بە پێچەوانەوە دەڕوات!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٤/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 5 -->
            <div class="movie-card">
                <div class="rank">5</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjgyMQ@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">پیاوێکی کۆن</div>
                    <div class="movie-year">٢٠٠٣ (کۆریایی)</div>
                    <div class="movie-plot">پیاوێک بۆ ١٥ ساڵ لە ژوورێکدا بە دیل دەگیرێت بەبێ هۆکار. دوای ئازادبوون، هەوڵ دەدات بزانێت کێ و بۆچی ئەمەی کردووە. کۆتاییەکەی ترسناکە!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٤/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 6 -->
            <div class="movie-card">
                <div class="rank">6</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NzE3MjE@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">ژنە ونبووەکە</div>
                    <div class="movie-year">٢٠١٤</div>
                    <div class="movie-plot">ژنێک لە ڕۆژی ساڵیادی هاوسەرگیریدا ون دەبێت و مێردەکەی تۆمەتبار دەکرێت. بەڵام ڕاستییەکە تەواو جیاوازە لەوەی دەرکەوتووە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.١/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 7 -->
            <div class="movie-card">
                <div class="rank">7</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BNjk1NzBlY2YtNjJmNi00YTVmLWI2OTgtNDUxNDE5NjUzZmE0XkEyXkFqcGdeQXVyNTc1NTQxODI@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">ئەندازیارەکە</div>
                    <div class="movie-year">٢٠٠٤</div>
                    <div class="movie-plot">کرێکارێکی کارگە بۆ ساڵێکە نەخەوتووە و یادەوەری لێ دەشێوێت. کەسێکی نامۆ دەردەکەوێت و ژیانی تێکدەدات. نهێنییەکی تاریک لە ڕابردوویدا هەیە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٦/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 8 -->
            <div class="movie-card">
                <div class="rank">8</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTAxMDE4Mzc3ODNeQTJeQWpwZ15BbWU4MDY2Mjg4MDcx._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">ئەوانی تر</div>
                    <div class="movie-year">٢٠٠١</div>
                    <div class="movie-plot">دایکێک و دوو منداڵەکەی لە ماڵێکی تاریکدا دەژین. منداڵەکان نابێت تیشکیان لێ بکەوێت. ڕووداوی سەیر دەستپێدەکات و نهێنی ماڵەکە ئاشکرا دەبێت.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٦/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 9 -->
            <div class="movie-card">
                <div class="rank">9</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BN2JmMjViMjMtZTM5Mi00ZGZkLTk5YzctZDg5MjFjZDE4NjNkXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">دوورگەی شاتر</div>
                    <div class="movie-year">٢٠١٠</div>
                    <div class="movie-plot">پۆلیسێک بۆ تەحقیق لەسەر ونبوونی نەخۆسێکی دەروونی دەچێتە دوورگەیەکی تایبەت. بەڵام هەموو شتێک ئەوەندە سادە نییە کە دەردەکەوێت.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٢/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 10 -->
            <div class="movie-card">
                <div class="rank">10</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMjEzMjczOTI2MV5BMl5BanBnXkFtZTgwOTUwMjI3NzE@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">گومانلێکراوە ئاساییەکە</div>
                    <div class="movie-year">١٩٩٥</div>
                    <div class="movie-plot">کەسێکی تاوانبار بەڵێن دەدات بە پۆلیس کە ئەگەر بەڵێنەکەی بەجێبهێنێت، ناوی تاوانبارێکی نەناسراو دەڵێت. کۆتاییەکە هەموو شتێک دەگۆڕێت!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٥/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 11 -->
            <div class="movie-card">
                <div class="rank">11</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTcyMzUyMzY1OF5BMl5BanBnXkFtZTcwNDQ4ODk1Mw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">حەوت</div>
                    <div class="movie-year">١٩٩٥</div>
                    <div class="movie-plot">دوو پۆلیس هەوڵ دەدەن کەسێک بدۆزنەوە کە کوشتنەکانی بەپێی حەوت تاوانە مەزنەکەی ئینجیل ئەنجام دەدات. کۆتاییەکە هۆشیارکەرەوەیە!</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٦/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 12 -->
            <div class="movie-card">
                <div class="rank">12</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMDliOTNhNmEtYTk2NS00NjFiLTkxMDItN2M1M2VmNWQzMjhlXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">دەستپێکردن</div>
                    <div class="movie-year">٢٠١٠</div>
                    <div class="movie-plot">سەرکردەیەکی تیمی تایبەت کە خەون دەدزێت، دەست دەکات بە ئەرکێکی مەترسیدار: نەخشاندنی بیرۆکەیەک لە مێشکی کەسێک.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٨/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 13 -->
            <div class="movie-card">
                <div class="rank">13</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTk4ODQzNDY3Ml5BMl5BanBnXkFtZTcwODA0NTM4Nw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">خوێندکار</div>
                    <div class="movie-year">٢٠١١</div>
                    <div class="movie-plot">خوێندکارێکی زانکۆ دەچێتە ناو کۆمەڵگەیەکی تایبەت و دەبێتە هۆی ڕووداوەکی ترسناک. کۆتاییەکە کەس پێشبینی نەیدەکرد.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٦/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 14 -->
            <div class="movie-card">
                <div class="rank">14</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">کەسی تاریک</div>
                    <div class="movie-year">٢٠١١</div>
                    <div class="movie-plot">پۆلیسێک هەوڵ دەدات کەسێک بدۆزێتەوە کە کۆمەڵێک کەسی بەکۆمەڵ دەکوژێت. بەڵام ڕاستییەکە زۆر نزیکترە لەوەی کە خەیاڵی دەکات.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.١/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 15 -->
            <div class="movie-card">
                <div class="rank">15</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">ئاڤاتار</div>
                    <div class="movie-year">٢٠٠٩</div>
                    <div class="movie-plot">سەربازێک لە جیهانێکی تر دەچێتە ناو لەشی بوونەوەرێکی تر و دەبێتە هۆی گۆڕانکارییەکی مەزن لە ژیانی خۆی و ئەو جیهانە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٨/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 16 -->
            <div class="movie-card">
                <div class="rank">16</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTk2NTI1MTU4N15BMl5BanBnXkFtZTcwODg0OTY0Nw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">پاشای شێت</div>
                    <div class="movie-year">٢٠١٩</div>
                    <div class="movie-plot">کەسێکی کۆمیدی دەبێتە پاشای شێت و دەست دەکات بە جێبەجێکردنی پلانێکی ترسناک. کۆتاییەکە هەموو کەسێک سەرسام دەکات.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٤/١٠</div>
                        <div class="age-rating">R (١٨+)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 17 -->
            <div class="movie-card">
                <div class="rank">17</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTM0MDgwNjMyMl5BMl5BanBnXkFtZTcwNTg0NzU1Ng@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">پڕۆژەی بێڵ</div>
                    <div class="movie-year">٢٠١٦</div>
                    <div class="movie-plot">زانایەک پڕۆژەیەکی تایبەت دروست دەکات بۆ گەڕانەوەی کچەکەی. بەڵام پڕۆژەکە زۆر مەترسیدارترە لەوەی کە خەیاڵی دەکرد.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٩/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 18 -->
            <div class="movie-card">
                <div class="rank">18</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTY3NjY0MTQ0Nl5BMl5BanBnXkFtZTcwMDQzMzQ2Mw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">دەستەی ڤێنۆم</div>
                    <div class="movie-year">٢٠١٨</div>
                    <div class="movie-plot">ڕۆژنامەنووسێک دەبێتە میواندارێکی بوونەوەرێکی دەرەکی و دەبێتە هۆی گۆڕانکارییەکی مەزن لە ژیانی.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٦.٧/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 19 -->
            <div class="movie-card">
                <div class="rank">19</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTc5MDE2ODcwNV5BMl5BanBnXkFtZTgwMzI2NzQ2NzM@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">کۆتایی یاری</div>
                    <div class="movie-year">٢٠١٩</div>
                    <div class="movie-plot">کۆمەڵێک کەس لە جیهانێکدا خەون دەبینن کە تێیدا مردنەکەیان ڕاستەقینە نییە. بەڵام ڕاستییەکە زۆر ترسناکترە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٤/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 20 -->
            <div class="movie-card">
                <div class="rank">20</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTczNTI2ODUwOF5BMl5BanBnXkFtZTcwMTU0NTIzMw@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">ئیرۆن مەن</div>
                    <div class="movie-year">٢٠٠٨</div>
                    <div class="movie-plot">بلیمەتێکی بەهرەدار دەبێتە قارەمانێکی سەربەخۆ دوای ئەوەی ڕزگاری لە تاوانبارێک دەبێت. بەڵام ڕووبەڕووبوونەوەی گەورە هەر هەیە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٩/١٠</div>
                        <div class="age-rating pg13">PG-13</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 21 -->
            <div class="movie-card">
                <div class="rank">21</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTM4NzQ0OTYyOF5BMl5BanBnXkFtZTcwMDkyNjQyMg@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">پاشای شێر</div>
                    <div class="movie-year">١٩٩٤</div>
                    <div class="movie-plot">شێرێکی گەنج دەبێتە پاشا دوای مردنی باوکی. بەڵام مامی پلانێکی خراپ دادەنێت بۆ وەرگرتنی تەختی پاشایەتی.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٨.٥/١٠</div>
                        <div class="age-rating">G (هەموو تەمەن)</div>
                    </div>
                </div>
            </div>
            
            <!-- فیلم 22 -->
            <div class="movie-card">
                <div class="rank">22</div>
                <div class="movie-poster" style="background-image: url('https://m.media-amazon.com/images/M/MV5BMTY5OTU0OTc2NV5BMl5BanBnXkFtZTcwMzU4MDcyMQ@@._V1_FMjpg_UX1000_.jpg')"></div>
                <div class="movie-info">
                    <div class="movie-title">بەربەست</div>
                    <div class="movie-year">٢٠١٤</div>
                    <div class="movie-plot">کەسێک لە جیهانێکی پۆست-ئەپۆکالیپتیکدا هەوڵ دەدات ڕزگاری خەڵک بکات لە نەهێشتنی تەواو. بەڵام ڕێگەکە زۆر مەترسیدارە.</div>
                    <div class="rating-container">
                        <div class="imdb-rating">⭐ ٧.٢/١٠</div>
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
            © ٢٠٢٣ فیلمی نایاب - هەموو مافەکان پارێزراون
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
