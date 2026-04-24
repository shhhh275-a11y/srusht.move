<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies - پلاتفۆرمی فیلمی کوردی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #0a0a0a;
            --bg2: #141414;
            --card: #1a1a1a;
            --accent: #e50914;
            --accent2: #ff6b35;
            --gold: #f5c518;
            --text: #fff;
            --text2: #999;
            --border: rgba(255,255,255,0.08);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        html { scroll-behavior: smooth; }

        body {
            font-family: 'Cairo', sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            overflow-x: hidden;
        }

        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

        /* navbar */
        .navbar {
            position: fixed;
            top:0; left:0; right:0;
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 48px;
            height: 68px;
            background: linear-gradient(to bottom, rgba(0,0,0,0.9) 0%, transparent 100%);
            transition: background 0.4s;
        }
        .navbar.scrolled {
            background: rgba(10,10,10,0.97);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border);
        }
        .brand {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 2em;
            letter-spacing: 3px;
            background: linear-gradient(135deg, #e50914, #ff6b35);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            cursor: pointer;
        }
        .nav-links {
            display: flex; gap: 28px; list-style: none;
        }
        .nav-links a {
            color: #ccc; text-decoration: none; font-size: 0.9em;
            font-weight: 600; transition: color 0.2s; cursor: pointer;
        }
        .nav-links a:hover { color: #fff; }
        .nav-right { display: flex; align-items: center; gap: 14px; }
        .mode-btn {
            background: rgba(255,255,255,0.07);
            border: 1px solid rgba(255,255,255,0.12);
            color: #ccc; border-radius: 20px;
            padding: 6px 14px; cursor: pointer;
            font-size: 0.82em; display: flex; align-items: center; gap: 6px;
            transition: all 0.2s;
        }
        .mode-btn:hover { background: rgba(255,255,255,0.14); color: #fff; }

        /* light mode */
        body.light {
            --bg: #f0f0f0; --bg2: #e8e8e8; --card: #fff;
            --text: #111; --text2: #555; --border: rgba(0,0,0,0.1);
        }
        body.light .navbar { background: linear-gradient(to bottom, rgba(240,240,240,0.95) 0%, transparent 100%); }
        body.light .navbar.scrolled { background: rgba(240,240,240,0.97); }
        body.light .movie-card { background: var(--card); box-shadow: 0 4px 20px rgba(0,0,0,0.1); }

        /* hero section */
        .hero {
            position: relative;
            height: 100vh; min-height: 640px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
        }
        .hero-backdrop {
            position: absolute; inset: 0; z-index: 0;
            background-size: cover;
            background-position: center top;
            animation: heroZoom 18s ease-in-out infinite alternate;
        }
        @keyframes heroZoom {
            from { transform: scale(1.0); }
            to   { transform: scale(1.07); }
        }
        .hero-poster-wrap {
            position: absolute;
            top: 50%; right: 8%;
            transform: translateY(-50%);
            z-index: 4;
            animation: posterIn 1.2s cubic-bezier(0.22,1,0.36,1) both;
            cursor: pointer;
        }
        @keyframes posterIn {
            from { opacity:0; transform: translateY(-44%) scale(0.92); }
            to   { opacity:1; transform: translateY(-50%) scale(1); }
        }
        .hero-poster-img {
            width: 260px;
            border-radius: 12px;
            box-shadow: 0 30px 80px rgba(0,0,0,0.85), 0 0 0 1px rgba(255,255,255,0.07);
            display: block;
        }
        .hero-overlay-top {
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to bottom, rgba(0,0,0,0.6) 0%, rgba(0,0,0,0.05) 25%, rgba(0,0,0,0.05) 55%, rgba(0,0,0,0.8) 85%, rgba(10,10,10,1) 100%);
        }
        .hero-overlay-sides {
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to left, rgba(0,0,0,0.45) 0%, rgba(0,0,0,0.15) 40%, rgba(0,0,0,0.7) 100%);
        }
        .hero-center {
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 160px;
            z-index: 3;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 0 56px;
            max-width: 600px;
        }
        .hero-site-badge {
            display: inline-flex; align-items: center; gap: 8px;
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1em; letter-spacing: 3px;
            color: rgba(255,255,255,0.55);
            margin-bottom: 18px;
        }
        .hero-brand-en {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(2.8em, 6vw, 5.5em);
            letter-spacing: 0.1em;
            line-height: 0.9;
            background: linear-gradient(160deg, #ffffff 0%, rgba(255,255,255,0.85) 50%, rgba(229,9,20,0.95) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 6px;
        }
        .hero-brand-line {
            width: 50px; height: 3px;
            background: var(--accent);
            border-radius: 2px;
            margin: 16px 0;
        }
        .hero-film-info {
            margin-top: 20px;
        }
        .hero-film-label {
            font-size: 0.72em; font-weight: 700;
            color: var(--accent); letter-spacing: 2px;
            text-transform: uppercase; margin-bottom: 6px;
        }
        .hero-film-title-big {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(1.8em, 4vw, 3em);
            letter-spacing: 2px;
            color: #fff;
            line-height: 1; margin-bottom: 8px;
        }
        .hero-film-tags {
            display: flex; gap: 10px; flex-wrap: wrap;
            margin-bottom: 20px;
        }
        .hero-film-tag {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.18);
            color: #ddd; font-size: 0.75em; font-weight: 600;
            padding: 4px 12px; border-radius: 20px;
        }
        .hero-cta {
            display: inline-flex; align-items: center; gap: 10px;
            background: var(--accent); color: #fff;
            padding: 13px 28px; border-radius: 8px;
            border: none; cursor: pointer;
            font-family: 'Cairo', sans-serif;
            font-size: 0.95em; font-weight: 700;
            transition: background 0.2s, transform 0.2s;
        }
        .hero-cta:hover { background: #c4070f; transform: translateY(-2px); }

        /* bottom film strip */
        .hero-film-row {
            position: relative; z-index: 4;
            display: flex;
            background: rgba(0,0,0,0.5);
            backdrop-filter: blur(3px);
        }
        .hero-film-card {
            flex: 1; position: relative;
            height: 150px; overflow: hidden;
            cursor: pointer;
            border-top: 2px solid rgba(229,9,20,0.6);
        }
        .hero-film-card::before {
            content: '';
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to top, rgba(0,0,0,0.88) 0%, rgba(0,0,0,0.1) 60%, transparent 100%);
            transition: background 0.3s;
        }
        .hero-film-card:hover::before {
            background: linear-gradient(to top, rgba(229,9,20,0.65) 0%, rgba(0,0,0,0.05) 70%, transparent 100%);
        }
        .hero-film-card-bg {
            position: absolute; inset: -4px;
            background-size: cover; background-position: center;
            transition: transform 0.5s ease;
        }
        .hero-film-card:hover .hero-film-card-bg { transform: scale(1.07); }
        .hero-film-card-info {
            position: absolute; bottom: 10px; left: 12px; right: 12px; z-index: 2;
        }
        .hero-film-card-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1.05em; letter-spacing: 1.5px;
            color: #fff; line-height: 1; margin-bottom: 3px;
            text-shadow: 0 2px 8px rgba(0,0,0,0.9);
        }
        .hero-film-card-meta {
            font-size: 0.7em; color: rgba(255,255,255,0.6);
            display: flex; gap: 7px;
        }
        .hero-film-card-rating { color: var(--gold); font-weight: 700; }
        .hero-film-card-divider {
            width: 2px; background: rgba(229,9,20,0.7);
            box-shadow: 0 0 6px rgba(229,9,20,0.5);
            flex-shrink: 0;
        }

        /* main content */
        .main { padding: 0 48px 80px; }
        .search-wrap { margin: 32px 0 10px; max-width: 680px; }
        .search-box {
            display: flex; align-items: center;
            background: rgba(255,255,255,0.06);
            border: 1px solid var(--border);
            border-radius: 10px; padding: 6px 6px 6px 20px;
        }
        .search-input {
            flex: 1; background: transparent; border: none; outline: none;
            color: var(--text); font-size: 1em;
            padding: 9px 0;
        }
        .search-btn {
            background: var(--accent); border: none; border-radius: 7px;
            padding: 10px 24px; color: #fff; cursor: pointer;
            font-size: 0.9em; font-weight: 700;
        }
        .tabs {
            display: flex; gap: 4px; margin: 26px 0 20px;
            border-bottom: 1px solid var(--border);
            flex-wrap: wrap;
        }
        .tab-btn {
            background: none; border: none; color: var(--text2);
            font-size: 0.9em; font-weight: 600;
            padding: 10px 20px; cursor: pointer;
            border-bottom: 2px solid transparent;
            transition: all 0.2s;
        }
        .tab-btn.active { color: var(--text); border-bottom-color: var(--accent); }
        .sec-title {
            font-size: 1.25em; font-weight: 700;
            margin: 20px 0 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .fav-row {
            display: flex;
            gap: 14px;
            overflow-x: auto;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        .fav-row > div {
            min-width: 120px;
            cursor: pointer;
            transition: transform 0.2s;
            background: var(--card);
            border-radius: 8px;
            overflow: hidden;
        }
        .fav-row > div:hover { transform: scale(1.05); }
        .fav-row img { width: 120px; height: 170px; object-fit: cover; display: block; }
        .fav-row div div { padding: 6px; font-size: 0.75em; text-align: center; }
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(195px, 1fr));
            gap: 20px; margin-bottom: 30px;
        }
        .movie-card {
            background: var(--card);
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.25s;
            position: relative;
        }
        .movie-card:hover { transform: scale(1.045); }
        .card-poster {
            width: 100%; height: 275px;
            object-fit: cover; display: block;
        }
        .fav-btn {
            position: absolute; top: 10px; left: 10px;
            background: rgba(0,0,0,0.72); border: none;
            width: 32px; height: 32px; border-radius: 50%;
            color: #fff; cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2;
        }
        .fav-btn.on { background: var(--accent); }
        .card-info { padding: 12px; }
        .card-title { font-weight: 700; margin-bottom: 4px; }
        .load-more {
            display: block; margin: 10px auto 50px;
            padding: 12px 44px;
            background: rgba(255,255,255,0.07);
            border: 1px solid var(--border);
            color: var(--text); border-radius: 8px;
            cursor: pointer;
            font-family: 'Cairo', sans-serif;
        }
        .load-more:hover { background: var(--accent); border-color: var(--accent); }

        /* modal */
        .modal-wrap {
            position: fixed; inset: 0; z-index: 3000;
            display: flex; align-items: center; justify-content: center;
            opacity: 0; pointer-events: none; transition: opacity 0.3s;
        }
        .modal-wrap.open { opacity: 1; pointer-events: all; }
        .modal-overlay {
            position: absolute; inset: 0;
            background: rgba(0,0,0,0.85); backdrop-filter: blur(8px);
        }
        .modal-box {
            position: relative; z-index: 1;
            background: var(--card);
            border-radius: 16px; overflow: hidden;
            width: 90%; max-width: 800px;
            max-height: 85vh; overflow-y: auto;
        }
        .modal-hero {
            position: relative; height: 220px;
            background-size: cover; background-position: center;
        }
        .modal-close {
            position: absolute; top: 14px; left: 14px;
            background: rgba(0,0,0,0.7); border: none; color: #fff;
            width: 36px; height: 36px; border-radius: 50%;
            cursor: pointer;
            z-index: 2;
        }
        .modal-body { padding: 24px; }
        .comment-section { margin-top: 40px; border-top: 1px solid var(--border); padding-top: 30px; }
        .comment-box {
            width: 100%; background: rgba(255,255,255,0.05);
            border: 1px solid var(--border); border-radius: 8px;
            padding: 12px; color: var(--text);
            margin-bottom: 10px;
            font-family: 'Cairo', sans-serif;
        }
        .comment-submit {
            background: var(--accent); color: #fff; border: none;
            padding: 10px 20px; border-radius: 8px; cursor: pointer;
            font-weight: 700;
        }
        .comments-list { margin-top: 20px; }
        .comment-item {
            border-bottom: 1px solid var(--border);
            padding: 12px 0;
        }
        .footer {
            text-align: center;
            padding: 30px;
            border-top: 1px solid var(--border);
            margin-top: 40px;
            color: var(--text2);
        }
        .scroll-top {
            position: fixed; bottom: 20px; left: 20px;
            background: var(--accent); border: none;
            width: 40px; height: 40px; border-radius: 50%;
            color: white; cursor: pointer; opacity: 0;
            transition: 0.3s;
            z-index: 999;
        }
        .scroll-top.show { opacity: 1; }

        @media(max-width:768px) {
            .navbar { padding: 0 16px; }
            .nav-links { display: none; }
            .hero-center { padding: 0 20px; }
            .hero-poster-wrap { right: 2%; transform: translateY(-50%) scale(0.85); }
            .hero-poster-img { width: 180px; }
            .main { padding: 0 16px; }
            .movie-grid { grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 12px; }
            .card-poster { height: 220px; }
        }
    </style>
</head>
<body>

<nav class="navbar" id="navbar">
    <span class="brand">Srusht Movies</span>
    <ul class="nav-links">
        <li><a onclick="window.scrollTo(0,0)">سەرەکی</a></li>
        <li><a onclick="document.getElementById('favSec').scrollIntoView({behavior:'smooth'})">دلخوازەکان</a></li>
        <li><a onclick="document.getElementById('gridSec').scrollIntoView({behavior:'smooth'})">فیلمەکان</a></li>
        <li><a onclick="document.getElementById('commentSec').scrollIntoView({behavior:'smooth'})">کۆمێنت</a></li>
    </ul>
    <div class="nav-right">
        <button class="mode-btn" id="modeBtn"><i class="fas fa-moon"></i><span>شەو</span></button>
    </div>
</nav>

<section class="hero" id="heroSec">
    <div class="hero-backdrop" id="heroBackdrop"></div>
    <div class="hero-overlay-top"></div>
    <div class="hero-overlay-sides"></div>
    <div class="hero-poster-wrap" id="heroPosterWrap">
        <img class="hero-poster-img" id="heroPosterImg" src="" alt="">
    </div>
    <div class="hero-center">
        <div class="hero-site-badge"><span></span> SRUSHT MOVIES <span></span></div>
        <div class="hero-brand-en">SRUSHT<br>MOVIES</div>
        <div class="hero-brand-line"></div>
        <div class="hero-film-info" id="heroFilmInfo"></div>
    </div>
    <div class="hero-film-row" id="heroFilmRow"></div>
</section>

<main class="main">
    <div class="search-wrap">
        <div class="search-box">
            <i class="fas fa-search"></i>
            <input class="search-input" id="searchInput" placeholder="گەڕان بە ناوی فیلم...">
            <button class="search-btn" onclick="doSearch()">گەڕان</button>
        </div>
    </div>

    <div class="tabs">
        <button class="tab-btn active" data-tab="all">هەموو</button>
        <button class="tab-btn" data-tab="thriller">Thriller</button>
        <button class="tab-btn" data-tab="drama">Drama</button>
        <button class="tab-btn" data-tab="scifi">Sci-Fi</button>
        <button class="tab-btn" data-tab="top9">⭐ +8.5</button>
    </div>

    <section id="favSec">
        <div class="sec-title"><i class="fas fa-heart" style="color:var(--accent)"></i> دلخوازەکانم <span id="favCount">(0)</span></div>
        <div class="fav-row" id="favRow"></div>
    </section>

    <section id="gridSec">
        <div class="sec-title"><i class="fas fa-film" style="color:var(--accent)"></i> فیلمەکان <span id="movieCount"></span></div>
        <div class="movie-grid" id="movieGrid"></div>
        <button class="load-more" id="loadMore">زیاتر باربکە</button>
    </section>

    <section class="comment-section" id="commentSec">
        <div class="sec-title"><i class="fas fa-comments" style="color:var(--accent)"></i> کۆمێنتەکان <span id="commentCount">(0)</span></div>
        <div>
            <textarea class="comment-box" id="cText" rows="3" placeholder="کۆمێنتەکەت بنووسە..."></textarea>
            <input class="comment-box" id="cName" placeholder="ناوت...">
            <button class="comment-submit" onclick="addComment()"><i class="fas fa-paper-plane"></i> ناردن</button>
        </div>
        <div class="comments-list" id="commentsList"></div>
    </section>
</main>

<footer class="footer">
    <p>Srusht Movies &copy; 2025 - هەموو فیلمەکان بۆ خەڵکی کوردستان</p>
</footer>

<button class="scroll-top" id="scrollTop" onclick="window.scrollTo({top:0,behavior:'smooth'})"><i class="fas fa-arrow-up"></i></button>

<div class="modal-wrap" id="modalWrap">
    <div class="modal-overlay" onclick="closeModal()"></div>
    <div class="modal-box" id="modalBox"></div>
</div>

<script>
// ======================== داتای فیلمەکان ========================
const MOVIES = [
    {id:0, en:"Fight Club", ku:"فایت کلاب", year:1999, rating:8.8, duration:"139 خولەک", genre:["thriller","drama"], age:"R", director:"David Fincher", cast:"Brad Pitt, Edward Norton, Helena Bonham Carter", country:"ئەمریکا", language:"ئینگلیزی", plot:"کارمەندێکی ناڕازی کۆمەڵێکی شەڕی نهێنی دادەمەزرێنێت. کۆتایی فیلمەکە یەکێک لە شۆککەرترین کۆتاییەکانی مێژووی سینەمایە.", awards:["Oscar: Best Film Editing (Nominated)"], trivia:"Brad Pitt تەنها 137 خولەک لە فیلمەکەدا دەردەکەوێت.", poster:"https://image.tmdb.org/t/p/w500/pB8BM7pdSp6B6Ih7QZ4DrQ3PmJK.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/hZkgoQYus5vegHoetLkCJzC5cZM.jpg"},
    {id:1, en:"The Sixth Sense", ku:"هەستی شەشەم", year:1999, rating:8.1, duration:"107 خولەک", genre:["thriller","drama"], age:"PG-13", director:"M. Night Shyamalan", cast:"Bruce Willis, Haley Joel Osment", country:"ئەمریکا", language:"ئینگلیزی", plot:"کوڕێکی بچووک قسەی رووحەکان دەکات. دکتۆرێک هەوڵی یارمەتیدانی دەدات.", awards:["Oscar: Best Director (Nominated)"], trivia:"فیلمەکە لە باجەتی 40 ملیۆن دۆلار، 672 ملیۆنی بەدەست هێنا.", poster:"https://image.tmdb.org/t/p/w500/ejkD56BejrSjCJOsUAISUqPEGo3.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/y4fwKFSRgEcz0A80QRiqhRtcfhO.jpg"},
    {id:2, en:"Shutter Island", ku:"شوتەر ئایلەند", year:2010, rating:8.2, duration:"138 خولەک", genre:["thriller","drama"], age:"R", director:"Martin Scorsese", cast:"Leonardo DiCaprio, Mark Ruffalo", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو دیتێکتیڤ لە دوورگەیێکی نەخۆشخانەی دیوانە لێکۆڵینەوە دەکەن.", awards:["Saturn Award: Best Horror Film"], trivia:"DiCaprio کتێبی دەروونناسی خوێندەوە بۆ ئامادەکاری.", poster:"https://image.tmdb.org/t/p/w500/5gzzkR7y3hnY8AD1wXjCnVlHba5.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/qfGcWXmKFUFgNpLShL2aRxGKwcl.jpg"},
    {id:3, en:"Parasite", ku:"پاراسایت", year:2019, rating:8.6, duration:"132 خولەک", genre:["thriller","drama","crime"], age:"R", director:"Bong Joon-ho", cast:"Song Kang-ho, Lee Sun-kyun", country:"کۆریای باشوور", language:"کۆری", plot:"خێزانێکی هەژار خۆیان دەخەنە ناو ماڵی دەوڵەمەند. نهێنییەکی ژێر خانووەکە هەموو شتێک دەگۆڕێت.", awards:["Oscar: Best Picture", "Palme d'Or"], trivia:"یەکەمین فیلمی کۆریایی کە Oscar ی باشترین فیلمی وەرگرت.", poster:"https://image.tmdb.org/t/p/w500/7IiTTgloJzvGI1TAYymCfbfl3vT.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/TU9NIjwzjoKPwQHoHshkFcQUCG.jpg"},
    {id:4, en:"Inception", ku:"ئینسپشن", year:2010, rating:8.8, duration:"148 خولەک", genre:["scifi","thriller"], age:"PG-13", director:"Christopher Nolan", cast:"Leonardo DiCaprio, Joseph Gordon-Levitt", country:"ئەمریکا", language:"ئینگلیزی", plot:"دزێک دەتوانێت بچێتە ناو خەونی کەسانی تر و بیرەکانی بدزێت. ئەرکی قورسی دانانی بیرۆکەیە لە مێشکدا.", awards:["Oscar: Best Visual Effects", "Oscar: Best Cinematography"], trivia:"Nolan 10 ساڵ کارکرد لەسەر سکریپتەکە.", poster:"https://image.tmdb.org/t/p/w500/oYuLEt3zVCKq57qu2F8dT7NIa6f.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/s3TBrRGB1iav7gFOCNx3H31MoES.jpg"},
    {id:5, en:"Memento", ku:"مەمینتۆ", year:2000, rating:8.4, duration:"113 خولەک", genre:["thriller","crime"], age:"R", director:"Christopher Nolan", cast:"Guy Pearce, Carrie-Anne Moss", country:"ئەمریکا", language:"ئینگلیزی", plot:"پیاوێک ناخۆشی بیرنەکردنەوەی هەیە. بۆ دۆزینەوەی کوشتنی ژنی، لەسەر جەستەی خۆی تێبینی دەنووسێت.", awards:["Oscar: Best Editing (Nominated)"], trivia:"فیلمەکە بە دوو شێوەی جیاواز دەتوانرێت بینرێت.", poster:"https://image.tmdb.org/t/p/w500/yuNs09hvpHVU1cXnO7EomSHzHHm.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/fS9VQm5WQ4u46Hc3NqJdBdVdIWH.jpg"},
    {id:6, en:"The Prestige", ku:"دەستگیری", year:2006, rating:8.5, duration:"130 خولەک", genre:["thriller","drama"], age:"PG-13", director:"Christopher Nolan", cast:"Christian Bale, Hugh Jackman", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو سیحر باز ڕکابەری دەکەن بۆ دۆزینەوەی نهێنی گەورەترین تێکەڵکاری.", awards:["Oscar: Best Cinematography (Nominated)"], trivia:"Nolan سکریپتی جیاوازی بۆ هەر ئەکتەرێک نووسی.", poster:"https://image.tmdb.org/t/p/w500/bdN3gXuIZYaJP6a3BbCOLJdRQQq.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/glyFRqkLHXXDEoGFrpBBOHj7gC.jpg"},
    {id:7, en:"Gone Girl", ku:"کچە ونبووە", year:2014, rating:8.1, duration:"149 خولەک", genre:["thriller","crime"], age:"R", director:"David Fincher", cast:"Ben Affleck, Rosamund Pike", country:"ئەمریکا", language:"ئینگلیزی", plot:"ژنی پیاوێک لە ڕۆژی ئەنیڤەرسەری ئازادییانە ون دەبێت. میدیا و پۆلیس دوژمنایەتی بەرامبەر مێردەکە دروست دەکەن.", awards:["Oscar: Best Actress (Nominated)"], trivia:"Rosamund Pike کتێبی دەروونناسی خوێندوە بۆ ئامادەکاری.", poster:"https://image.tmdb.org/t/p/w500/fSRb7vyIP8rQpL0I47P3qUsEKX3.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/3kcEGnYBHDeqmdYf8ZRbKdfmlUO.jpg"},
    {id:8, en:"Get Out", ku:"دەرچۆ", year:2017, rating:7.8, duration:"104 خولەک", genre:["thriller"], age:"R", director:"Jordan Peele", cast:"Daniel Kaluuya, Allison Williams", country:"ئەمریکا", language:"ئینگلیزی", plot:"کوڕێکی ڕەش سەردانی خێزانی خۆشەویستەکەی دەکات. ڕەفتاری نامۆی خێزانەکە نهێنییەکی ترسناک شاردووەتەوە.", awards:["Oscar: Best Original Screenplay"], trivia:"باجەتی فیلمەکە 4.5 ملیۆن دۆلار بوو، 255 ملیۆنی بەدەست هێنا.", poster:"https://image.tmdb.org/t/p/w500/tFXcEccSQMf3lfhfXKSU9iRBpa3.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/nNmJrD0DiALfkXFKz23G01NrWBO.jpg"},
    {id:9, en:"Oldboy", ku:"ئۆڵدبۆی", year:2003, rating:8.4, duration:"120 خولەک", genre:["thriller"], age:"R", director:"Park Chan-wook", cast:"Choi Min-sik, Yoo Ji-tae", country:"کۆریای باشوور", language:"کۆری", plot:"پیاوێک 15 ساڵ بەبێ هۆکار لە ژوورێکدا دادەنرێت. دوای ئازادبوون، 5 ڕۆژی هەیە تا ڕاستییەکە بدۆزێتەوە.", awards:["Grand Prix - Cannes 2004"], trivia:"Quentin Tarantino ئەم فیلمەی خستووەتە لیستی باشترین فیلمەکانی.", poster:"https://image.tmdb.org/t/p/w500/pWDtjs568ZfOTMbURQBmHx9LTWR.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/8tbVLgNhBUTaGcq3iFMnmXf9f5l.jpg"},
    {id:10, en:"Se7en", ku:"حەفت", year:1995, rating:8.6, duration:"127 خولەک", genre:["thriller","crime"], age:"R", director:"David Fincher", cast:"Brad Pitt, Morgan Freeman, Kevin Spacey", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو دیتێکتیڤ لەدوای کوشتارچیێکدا کە تاوانەکانی بەپێی حەفت گوناهی گەورە دەکات.", awards:["Oscar: Best Film Editing (Nominated)"], trivia:"Kevin Spacey لە کرێدیتە سەرەکییەکان دانەنراوە بۆ پاراستنی نهێنی.", poster:"https://image.tmdb.org/t/p/w500/6yoghtyTpznpBik8EngEmJskVnS.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/or0ZTn9nvlEtH35KvCtxGruoJbR.jpg"},
    {id:11, en:"The Usual Suspects", ku:"گومانلێکراوەکان", year:1995, rating:8.5, duration:"106 خولەک", genre:["crime","thriller"], age:"R", director:"Bryan Singer", cast:"Kevin Spacey, Gabriel Byrne", country:"ئەمریکا", language:"ئینگلیزی", plot:"پێنج تاوانبار کۆدەبنەوە بۆ ئەنجامدانی پرۆژەیەکی مەزن. کۆتاییەکە هەموو شتێک دەگۆڕێت.", awards:["Oscar: Best Supporting Actor", "Oscar: Best Original Screenplay"], trivia:"Keyser Söze یەکێک لە باشترین ڤیلانەکانی مێژووی سینەمایە.", poster:"https://image.tmdb.org/t/p/w500/3gQKNHfTPvazBj1IsIOvuqFnTYX.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/8Zug5ZoGSBpE1gSoMGqkRVZAcex.jpg"},
    {id:12, en:"Interstellar", ku:"ئینتەرستێلار", year:2014, rating:8.7, duration:"169 خولەک", genre:["scifi","drama"], age:"PG-13", director:"Christopher Nolan", cast:"Matthew McConaughey, Anne Hathaway", country:"ئەمریکا", language:"ئینگلیزی", plot:"گروپێک لە شوێندۆزان بەدوای هەسارەی نوێدا دەگەڕێن بۆ ڕزگارکردنی مرۆڤایەتی.", awards:["Oscar: Best Visual Effects"], trivia:"Kip Thorne، فیزیکدانی نۆبێل، ڕاوێژکاری فیلمەکە بوو.", poster:"https://image.tmdb.org/t/p/w500/gEU2QniE6E77NI6lCU6MxlNBvIx.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/xu9zaAevzQ5nnrsXN6JcahLnG4i.jpg"},
    {id:13, en:"Joker", ku:"جۆکەر", year:2019, rating:8.5, duration:"122 خولەک", genre:["thriller","drama"], age:"R", director:"Todd Phillips", cast:"Joaquin Phoenix, Robert De Niro", country:"ئەمریکا", language:"ئینگلیزی", plot:"Arthur Fleck، پیاوێکی ئازاردراو، بەرەو بوونە جۆکەر دەڕوات. چیرۆکی کۆمەڵایەتی و دەروونی.", awards:["Oscar: Best Actor - Joaquin Phoenix", "Golden Lion"], trivia:"Joaquin Phoenix 52 پاوند وزەی لادا بۆ ئەم ڕۆڵە.", poster:"https://image.tmdb.org/t/p/w500/udDclJoHjfjb8Ekgsd4FDteOkCU.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/n6bUvigpRFqSwmPp1m2YAnoNHjQ.jpg"},
    {id:14, en:"Prisoners", ku:"بندیەکان", year:2013, rating:8.2, duration:"153 خولەک", genre:["thriller","crime"], age:"R", director:"Denis Villeneuve", cast:"Hugh Jackman, Jake Gyllenhaal", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو کچ ون دەبن. باوکی یەکێکیان بڕیاری خۆی دەدات بۆ دۆزینەوەی ڕاستی.", awards:["Oscar: Best Cinematography (Nominated)"], trivia:"Villeneuve فیلمەکەی درێژکردووە بۆ 153 خولەک و ستودیۆ قبوڵی کرد.", poster:"https://image.tmdb.org/t/p/w500/oAISjx6DvR2yUn9dxj00vP15CFh.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/7X3CYEoatxBiLBMeKbstVmCVKGI.jpg"},
    {id:15, en:"The Departed", ku:"دچووەتەوە", year:2006, rating:8.5, duration:"151 خولەک", genre:["crime","thriller"], age:"R", director:"Martin Scorsese", cast:"Leonardo DiCaprio, Matt Damon", country:"ئەمریکا", language:"ئینگلیزی", plot:"پۆلیسێک لە ناو باندێک و باندبەرێک لە ناو پۆلیسدا. هەر دووکیان دەبێت یەکتر بدۆزنەوە.", awards:["Oscar: Best Picture", "Oscar: Best Director"], trivia:"یەکەم ئۆسکاری سکۆرسێزی بۆ باشترین دەرھێنەر.", poster:"https://image.tmdb.org/t/p/w500/nT97ifVT2J1yMQmeq20Qblg61T.jpg", backdrop:"https://image.tmdb.org/t/p/w1280/5GiDW8HXMGFLmpfMtNOKYjW7MZY.jpg"}
];

// ========== کۆنترۆڵی هێڵی خوارەوە (strip) ==========
// ✅ ئەم لیستەی خوارەوە دەستکاری بکە بۆ زیادکردن یان کەمکردنی فیلمەکانی strip
// تەنها ژمارەی ئایدی فیلمەکان (id) زیاد بکە یان لابەرە
const STRIP_MOVIES_IDS = [0, 3, 13, 15, 7, 10, 4, 12];  // ئێستا 8 فیلم - دەتوانیت زیاد یان کەمی بکەیت

// ========== STATE ==========
let favs = JSON.parse(localStorage.getItem('srushtFavs') || '[]');
let comments = JSON.parse(localStorage.getItem('srushtComments') || '[]');
let currentPage = 1;
let activeTab = 'all';
let searchQ = '';

// ========== SETUP HERO ==========
function setupHero() {
    const featured = MOVIES[4];
    const backdropEl = document.getElementById('heroBackdrop');
    if(backdropEl) backdropEl.style.backgroundImage = `url('${featured.backdrop}')`;
    
    const posterImg = document.getElementById('heroPosterImg');
    if(posterImg) {
        posterImg.src = featured.poster;
        posterImg.onclick = () => openModal(featured.id);
    }
    
    const infoDiv = document.getElementById('heroFilmInfo');
    infoDiv.innerHTML = `
        <div class="hero-film-label">🎬 فیلمی تایبەتی هەفتە</div>
        <div class="hero-film-title-big">${featured.en}</div>
        <div class="hero-film-tags">
            <span class="hero-film-tag">⭐ ${featured.rating}</span>
            <span class="hero-film-tag">${featured.year}</span>
            <span class="hero-film-tag">${featured.duration}</span>
            <span class="hero-film-tag">${featured.age}</span>
        </div>
        <button class="hero-cta" onclick="openModal(${featured.id})">
            <i class="fas fa-info-circle"></i> زانیاری تەواو
        </button>
    `;
    
    // دروستکردنی strip بە شێوەی داینامیک
    const row = document.getElementById('heroFilmRow');
    row.innerHTML = '';
    STRIP_MOVIES_IDS.forEach((id, idx) => {
        const movie = MOVIES.find(m => m.id === id);
        if(!movie) return;
        if(idx > 0) {
            const divider = document.createElement('div');
            divider.className = 'hero-film-card-divider';
            row.appendChild(divider);
        }
        const card = document.createElement('div');
        card.className = 'hero-film-card';
        card.innerHTML = `
            <div class="hero-film-card-bg" style="background-image:url('${movie.backdrop}')"></div>
            <div class="hero-film-card-info">
                <div class="hero-film-card-title">${movie.en}</div>
                <div class="hero-film-card-meta">
                    <span class="hero-film-card-rating">⭐ ${movie.rating}</span>
                    <span>${movie.year}</span>
                </div>
            </div>
        `;
        card.onclick = () => openModal(movie.id);
        row.appendChild(card);
    });
}

// ========== FILTER & RENDER ==========
function filteredMovies() {
    let list = [...MOVIES];
    if(activeTab === 'thriller') list = list.filter(m => m.genre.includes('thriller'));
    else if(activeTab === 'drama') list = list.filter(m => m.genre.includes('drama'));
    else if(activeTab === 'scifi') list = list.filter(m => m.genre.includes('scifi'));
    else if(activeTab === 'top9') list = list.filter(m => m.rating >= 8.5);
    if(searchQ) list = list.filter(m => m.ku.includes(searchQ) || m.en.toLowerCase().includes(searchQ.toLowerCase()));
    return list;
}

function renderMovies(reset = true) {
    const grid = document.getElementById('movieGrid');
    if(reset) { grid.innerHTML = ''; currentPage = 1; }
    const list = filteredMovies();
    const start = (currentPage - 1) * 15;
    const end = start + 15;
    const pageItems = list.slice(start, end);
    
    document.getElementById('movieCount')?.setAttribute('data-count', list.length);
    
    pageItems.forEach(m => {
        const isFav = favs.includes(m.id);
        const card = document.createElement('div');
        card.className = 'movie-card';
        card.style.position = 'relative';
        card.innerHTML = `
            <img class="card-poster" src="${m.poster}" onerror="this.src='https://via.placeholder.com/300x420?text=No+Image'">
            <button class="fav-btn ${isFav ? 'on' : ''}" data-id="${m.id}">
                <i class="${isFav ? 'fas' : 'far'} fa-heart"></i>
            </button>
            <div class="card-info">
                <div class="card-title">${m.ku}</div>
                <div style="display:flex; justify-content:space-between; margin-top:5px;">
                    <span style="color:var(--gold)">⭐ ${m.rating}</span>
                    <span style="color:var(--text2)">${m.year}</span>
                </div>
            </div>
        `;
        card.querySelector('.fav-btn').onclick = (e) => { e.stopPropagation(); toggleFav(m.id); };
        card.onclick = () => openModal(m.id);
        grid.appendChild(card);
    });
    
    const loadBtn = document.getElementById('loadMore');
    loadBtn.style.display = end < list.length ? 'block' : 'none';
}

// ========== FAVORITES ==========
function toggleFav(id) {
    const idx = favs.indexOf(id);
    if(idx === -1) favs.push(id);
    else favs.splice(idx, 1);
    localStorage.setItem('srushtFavs', JSON.stringify(favs));
    renderFavs();
    document.querySelectorAll(`.fav-btn[data-id="${id}"]`).forEach(btn => {
        const on = favs.includes(id);
        btn.classList.toggle('on', on);
        btn.innerHTML = `<i class="${on ? 'fas' : 'far'} fa-heart"></i>`;
    });
}

function renderFavs() {
    const row = document.getElementById('favRow');
    row.innerHTML = '';
    if(favs.length === 0) {
        row.innerHTML = '<div style="color:var(--text2); padding:20px; text-align:center;">هیچ فیلمێک زیاد نەکراوە - لەسەر ❤️ کلیک بکە</div>';
        document.getElementById('favCount').innerText = '(0)';
        return;
    }
    document.getElementById('favCount').innerText = `(${favs.length})`;
    favs.forEach(id => {
        const m = MOVIES.find(x => x.id === id);
        if(m) {
            const div = document.createElement('div');
            div.innerHTML = `<img src="${m.poster}" alt="${m.ku}" onerror="this.src='https://via.placeholder.com/120x170'"><div>${m.ku}</div>`;
            div.onclick = () => openModal(m.id);
            row.appendChild(div);
        }
    });
}

// ========== MODAL ==========
function openModal(id) {
    const m = MOVIES.find(x => x.id === id);
    if(!m) return;
    const isFav = favs.includes(m.id);
    const genres = m.genre.map(g => `<span style="background:rgba(229,9,20,0.15); padding:4px 12px; border-radius:20px; font-size:0.75rem;">${g.toUpperCase()}</span>`).join('');
    const awardsHtml = m.awards.map(a => `<span style="background:rgba(245,197,24,0.1); padding:4px 12px; border-radius:20px; font-size:0.7rem;">🏆 ${a}</span>`).join('');
    
    const modalBox = document.getElementById('modalBox');
    modalBox.innerHTML = `
        <div class="modal-hero" style="background-image:url('${m.backdrop}')">
            <div style="background:linear-gradient(to top, var(--card), transparent); height:100%"></div>
        </div>
        <button class="modal-close" onclick="closeModal()"><i class="fas fa-times"></i></button>
        <div class="modal-body">
            <h2 style="font-family:'Bebas Neue'; font-size:2rem;">${m.ku} <span style="font-size:1rem; color:var(--text2);">(${m.year})</span></h2>
            <div style="display:flex; gap:8px; flex-wrap:wrap; margin:15px 0;">${genres}</div>
            <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; margin:15px 0;">
                <div><span style="color:var(--text2);">⭐ ڕیتینگ:</span> <strong>${m.rating}/10</strong></div>
                <div><span style="color:var(--text2);">🕐 ماوە:</span> ${m.duration}</div>
                <div><span style="color:var(--text2);">🎬 دەرھێنەر:</span> ${m.director}</div>
                <div><span style="color:var(--text2);">🌍 وڵات:</span> ${m.country}</div>
            </div>
            <div style="margin:15px 0;"><span style="color:var(--text2);">📖 باسی فیلم:</span><br>${m.plot}</div>
            <div style="margin:15px 0;"><span style="color:var(--text2);">🎭 بازیگەران:</span><br>${m.cast}</div>
            <div style="margin:15px 0;"><span style="color:var(--text2);">🏆 خەڵاتەکان:</span><br><div style="display:flex; flex-wrap:wrap; gap:6px; margin-top:5px;">${awardsHtml || '---'}</div></div>
            <div style="margin:15px 0;"><span style="color:var(--text2);">💡 زانیاری:</span><br>${m.trivia}</div>
            <button class="comment-submit" onclick="toggleFav(${m.id}); this.innerHTML = favs.includes(${m.id}) ? 'لە دلخوازەکانم ✅' : '❤️ زیادکردن بۆ دلخواز';" style="margin-top:15px; width:100%;">${isFav ? 'لە دلخوازەکانم ✅' : '❤️ زیادکردن بۆ دلخواز'}</button>
        </div>
    `;
    document.getElementById('modalWrap').classList.add('open');
    document.body.style.overflow = 'hidden';
}

function closeModal() {
    document.getElementById('modalWrap').classList.remove('open');
    document.body.style.overflow = '';
}

// ========== COMMENTS ==========
function renderComments() {
    const container = document.getElementById('commentsList');
    document.getElementById('commentCount').innerText = `(${comments.length})`;
    if(comments.length === 0) {
        container.innerHTML = '<div style="color:var(--text2); text-align:center; padding:20px;">هیچ کۆمێنتێک نییە - یەکەم کەس بە!</div>';
        return;
    }
    container.innerHTML = comments.slice().reverse().map(c => `
        <div class="comment-item">
            <strong style="color:var(--accent);">${escapeHtml(c.name)}</strong>
            <div style="font-size:0.85rem; margin-top:5px;">${escapeHtml(c.text)}</div>
            <div style="font-size:0.7rem; color:var(--text2); margin-top:5px;">${c.time}</div>
        </div>
    `).join('');
}

function escapeHtml(str) { return str.replace(/[&<>]/g, function(m){if(m==='&') return '&amp;'; if(m==='<') return '&lt;'; if(m==='>') return '&gt;'; return m;}); }

function addComment() {
    const text = document.getElementById('cText').value.trim();
    const name = document.getElementById('cName').value.trim();
    if(!text || !name) return;
    comments.unshift({
        name: name,
        text: text,
        time: new Date().toLocaleString('ku')
    });
    localStorage.setItem('srushtComments', JSON.stringify(comments));
    renderComments();
    document.getElementById('cText').value = '';
    document.getElementById('cName').value = '';
}

// ========== SEARCH & TABS ==========
function doSearch() {
    searchQ = document.getElementById('searchInput').value.trim();
    renderMovies(true);
}

document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.onclick = () => {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        activeTab = btn.dataset.tab;
        renderMovies(true);
    };
});

document.getElementById('searchInput').addEventListener('keydown', e => { if(e.key === 'Enter') doSearch(); });
document.getElementById('loadMore').onclick = () => { currentPage++; renderMovies(false); };

// ========== MODE & SCROLL ==========
const modeBtn = document.getElementById('modeBtn');
if(localStorage.getItem('srushtMode') === 'light') {
    document.body.classList.add('light');
    modeBtn.querySelector('i').className = 'fas fa-sun';
    modeBtn.querySelector('span').innerText = 'ڕۆژ';
}
modeBtn.onclick = () => {
    document.body.classList.toggle('light');
    const isLight = document.body.classList.contains('light');
    modeBtn.querySelector('i').className = isLight ? 'fas fa-sun' : 'fas fa-moon';
    modeBtn.querySelector('span').innerText = isLight ? 'ڕۆژ' : 'شەو';
    localStorage.setItem('srushtMode', isLight ? 'light' : 'dark');
};

window.onscroll = () => {
    document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 50);
    document.getElementById('scrollTop').classList.toggle('show', window.scrollY > 400);
};

document.addEventListener('keydown', e => { if(e.key === 'Escape') closeModal(); });

// ========== INIT ==========
setupHero();
renderMovies();
renderFavs();
renderComments();
</script>
</body>
</html>
