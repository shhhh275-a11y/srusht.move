<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فیلمەکانی کۆتایی شۆککەر</title>
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
        }
        
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.6)),
                        url('https://i.imgur.com/placeholder.jpg');
            background: #2c1810;
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
        
        h1 {
            text-align: center;
            color: white;
            margin-bottom: 10px;
            font-size: 2.5em;
            text-shadow: 3px 3px 10px rgba(0,0,0,0.7);
            animation: fadeInDown 1s ease;
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
        
        .subtitle {
            text-align: center;
            color: rgba(255,255,255,0.95);
            margin-bottom: 40px;
            font-size: 1.2em;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.5);
            animation: fadeIn 1.5s ease;
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
            background: linear-gradient(135deg, #c77b63 0%, #8b5a4a 100%);
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
        
        @media (max-width: 768px) {
            h1 { font-size: 2em; }
            .subtitle { font-size: 1em; }
            .movie-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            .background-image {
                width: 300px;
                height: 300px;
            }
        }
    </style>
</head>
<body>
    <div class="background-image"></div>
    
    <div class="container">
        <h1 style="font-family: 'Arial', sans-serif; font-size: 1.1em; font-weight: 500; letter-spacing: 2px; margin-bottom: 20px; padding: 12px 25px; border: 2px solid rgba(255,255,255,0.6); border-radius: 50px; display: inline-block; background: rgba(255,255,255,0.05); backdrop-filter: blur(5px); text-transform: uppercase;">🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</h1>
        <p class="subtitle" style="font-family: 'Arial Black', 'Arial', sans-serif; font-size: 3em; font-weight: 900; letter-spacing: 5px; color: white; text-shadow: 5px 5px 0px rgba(0,0,0,0.3), 0 0 40px rgba(255,255,255,0.5); text-transform: uppercase; background: linear-gradient(45deg, #ffffff, #f0f0f0); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Srusht Movies</p>
        
        <div class="movie-grid">
            <div class="movie-card">
                <div class="rank">1</div>
                <div class="movie-poster">
                    <div>The Sixth Sense<br>🎭👻</div>
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
            
            <div class="movie-card">
                <div class="rank">2</div>
                <div class="movie-poster">
                    <div>Fight Club<br>🥊💥</div>
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
            
            <div class="movie-card">
                <div class="rank">3</div>
                <div class="movie-poster">
                    <div>The Prestige<br>🎩✨🪄</div>
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
            
            <div class="movie-card">
                <div class="rank">4</div>
                <div class="movie-poster">
                    <div>Memento<br>🧩🔄</div>
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
            
            <div class="movie-card">
                <div class="rank">5</div>
                <div class="movie-poster">
                    <div>Oldboy<br>🔨⚔️</div>
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
            
            <div class="movie-card">
                <div class="rank">6</div>
                <div class="movie-poster">
                    <div>Gone Girl<br>💔🔪</div>
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
            
            <div class="movie-card">
                <div class="rank">7</div>
                <div class="movie-poster">
                    <div>The Machinist<br>⚙️😰</div>
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
            
            <div class="movie-card">
                <div class="rank">8</div>
                <div class="movie-poster">
                    <div>The Others<br>👻🏚️</div>
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
        </div>
    </div>
</body>
</html>
        </h1>

        <!-- خاونی سایەت -->
        <div class="ig-banner">
          <a href="https://instagram.com/9fi.99" target="_blank">
            <span class="ig-icon">📸</span>
            <span>srusht</span>
          </a>
        </div>

        <p class="subtitle" style="font-family: 'Arial Black', 'Arial', sans-serif; font-size: 3em; font-weight: 900; letter-spacing: 5px; color: white; text-shadow: 5px 5px 0px rgba(0,0,0,0.3), 0 0 40px rgba(255,255,255,0.5); text-transform: uppercase; background: linear-gradient(45deg, #ffffff, #f0f0f0); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">Srusht Movies</p>
