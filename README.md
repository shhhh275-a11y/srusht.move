<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies - باشترین فیلمەکان بە کوردی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        * { margin:0; padding:0; box-sizing:border-box; }
        :root {
            --bg: #0a0a0a;
            --bg2: #141414;
            --card: #1a1a1a;
            --accent: #e50914;
            --gold: #f5c518;
            --text: #fff;
            --text2: #999;
            --border: rgba(255,255,255,0.08);
        }
        body {
            font-family: 'Cairo', sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            overflow-x: hidden;
        }
        body.light {
            --bg: #f0f0f0;
            --card: #fff;
            --text: #111;
            --text2: #555;
        }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

        /* NAVBAR */
        .navbar {
            position: fixed; top:0; left:0; right:0; z-index: 1000;
            display: flex; align-items: center; justify-content: space-between;
            padding: 0 48px; height: 68px;
            background: linear-gradient(to bottom, rgba(0,0,0,0.95) 0%, transparent 100%);
            transition: background 0.4s;
        }
        .navbar.scrolled { background: rgba(10,10,10,0.97); backdrop-filter: blur(12px); }
        .brand {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 2em; letter-spacing: 3px;
            background: linear-gradient(135deg, #e50914, #ff6b35);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            cursor: pointer;
        }
        .nav-links { display: flex; gap: 28px; list-style: none; }
        .nav-links a { color: #ccc; text-decoration: none; cursor: pointer; transition: color 0.2s; }
        .nav-links a:hover { color: #fff; }
        .mode-btn {
            background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.12);
            color: #ccc; border-radius: 20px; padding: 6px 14px; cursor: pointer;
            display: flex; align-items: center; gap: 6px;
        }

        /* HERO */
        .hero {
            position: relative; height: 100vh; min-height: 640px;
            overflow: hidden; display: flex; flex-direction: column; justify-content: flex-end;
        }
        .hero-backdrop {
            position: absolute; inset: 0; z-index: 0;
            background-size: cover; background-position: center top;
            animation: heroZoom 18s ease-in-out infinite alternate;
        }
        @keyframes heroZoom { from { transform: scale(1); } to { transform: scale(1.07); } }
        .hero-poster-wrap {
            position: absolute; top: 50%; right: 8%; transform: translateY(-50%);
            z-index: 4; cursor: pointer;
        }
        .hero-poster-img { width: 260px; border-radius: 12px; box-shadow: 0 30px 80px rgba(0,0,0,0.85); display: block; }
        .hero-overlay-top {
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to bottom, rgba(0,0,0,0.6) 0%, rgba(0,0,0,0.05) 25%, rgba(0,0,0,0.05) 55%, rgba(0,0,0,0.8) 85%, rgba(10,10,10,1) 100%);
        }
        .hero-center {
            position: absolute; top: 0; left: 0; right: 0; bottom: 160px; z-index: 3;
            display: flex; flex-direction: column; justify-content: center;
            padding: 0 56px; max-width: 600px;
        }
        .hero-brand-en {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(2.8em, 6vw, 5.5em); letter-spacing: 0.1em; line-height: 0.9;
            background: linear-gradient(160deg, #fff 0%, rgba(255,255,255,0.85) 50%, rgba(229,9,20,0.95) 100%);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            margin-bottom: 6px;
        }
        .hero-brand-line { width: 50px; height: 3px; background: var(--accent); border-radius: 2px; margin: 16px 0; }
        .hero-cta {
            display: inline-flex; align-items: center; gap: 10px;
            background: var(--accent); color: #fff; padding: 13px 28px;
            border-radius: 8px; border: none; cursor: pointer;
            font-weight: 700; transition: background 0.2s;
        }
        .hero-cta:hover { background: #c4070f; }
        .hero-film-row { position: relative; z-index: 4; display: flex; gap: 0; }
        .hero-film-card {
            flex: 1; position: relative; height: 150px; overflow: hidden;
            cursor: pointer; border-top: 2px solid rgba(229,9,20,0.4);
        }
        .hero-film-card::before {
            content: ''; position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to top, rgba(0,0,0,0.88) 0%, rgba(0,0,0,0.1) 60%, transparent 100%);
        }
        .hero-film-card-bg {
            position: absolute; inset: -4px;
            background-size: cover; background-position: center;
            transition: transform 0.5s ease;
        }
        .hero-film-card:hover .hero-film-card-bg { transform: scale(1.07); }
        .hero-film-card-info { position: absolute; bottom: 10px; left: 12px; z-index: 2; }
        .hero-film-card-title { font-family: 'Bebas Neue', sans-serif; font-size: 1.05em; color: #fff; text-shadow: 0 2px 8px rgba(0,0,0,0.9); }
        .hero-film-card-divider { width: 1px; background: rgba(229,9,20,0.5); flex-shrink: 0; }

        /* MAIN */
        .main { padding: 0 48px 80px; }
        .search-wrap { margin: 32px 0 10px; max-width: 680px; }
        .search-box {
            display: flex; align-items: center;
            background: rgba(255,255,255,0.06); border: 1px solid var(--border);
            border-radius: 10px; padding: 6px 6px 6px 20px;
        }
        .search-input {
            flex: 1; background: transparent; border: none; outline: none;
            color: var(--text); font-size: 1em; padding: 9px 0;
        }
        .search-btn {
            background: var(--accent); border: none; border-radius: 7px;
            padding: 10px 24px; color: #fff; cursor: pointer; font-weight: 700;
        }
        .tabs {
            display: flex; gap: 4px; margin: 26px 0 20px;
            border-bottom: 1px solid var(--border); flex-wrap: wrap;
        }
        .tab-btn {
            background: none; border: none; color: var(--text2);
            font-size: 0.9em; font-weight: 600; padding: 10px 20px;
            cursor: pointer; border-bottom: 2px solid transparent;
            transition: all 0.2s;
        }
        .tab-btn.active { color: var(--text); border-bottom-color: var(--accent); }
        .sec-title { font-size: 1.25em; font-weight: 700; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; }
        
        .fav-section { margin-bottom: 42px; }
        .fav-empty {
            background: rgba(255,255,255,0.03); border: 1px dashed var(--border);
            border-radius: 12px; padding: 36px; text-align: center; color: var(--text2);
        }
        .fav-row { display: flex; gap: 14px; overflow-x: auto; padding-bottom: 10px; }
        .fav-mini {
            min-width: 140px; border-radius: 8px; overflow: hidden;
            background: var(--card); cursor: pointer; position: relative; flex-shrink: 0;
            transition: transform 0.2s;
        }
        .fav-mini:hover { transform: scale(1.04); }
        .fav-mini-img { width: 140px; height: 190px; object-fit: cover; display: block; background: #222; }
        .fav-mini-title { padding: 8px; font-size: 0.78em; font-weight: 600; color: var(--text); }
        .fav-mini-remove {
            position: absolute; top: 6px; left: 6px;
            background: rgba(229,9,20,0.85); border: none;
            width: 26px; height: 26px; border-radius: 50%; color: #fff; cursor: pointer;
        }
        
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(195px, 1fr));
            gap: 20px; margin-bottom: 30px;
        }
        .movie-card {
            background: var(--card); border-radius: 10px;
            overflow: hidden; cursor: pointer; transition: transform 0.25s; position: relative;
        }
        .movie-card:hover { transform: scale(1.045); }
        .card-poster { width: 100%; height: 275px; object-fit: cover; display: block; background: #1a1a1a; }
        .fav-btn {
            position: absolute; top: 10px; left: 10px;
            background: rgba(0,0,0,0.72); border: none;
            width: 32px; height: 32px; border-radius: 50%; color: #fff; cursor: pointer; z-index: 2;
        }
        .fav-btn.on { background: var(--accent); }
        .age-tag {
            position: absolute; top: 10px; right: 10px;
            background: rgba(0,0,0,0.75); color: #ccc; font-size: 0.68em;
            padding: 3px 7px; border-radius: 4px; z-index: 2;
        }
        .card-info { padding: 13px; }
        .card-title { font-size: 0.9em; font-weight: 700; margin-bottom: 5px; }
        .card-meta { display: flex; justify-content: space-between; }
        .card-rating { color: var(--gold) !important; }
        .load-more {
            display: block; margin: 10px auto 50px; padding: 12px 44px;
            background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.12);
            color: var(--text); border-radius: 8px; cursor: pointer;
        }
        
        /* MODAL */
        .modal-wrap {
            position: fixed; inset: 0; z-index: 3000;
            display: flex; align-items: center; justify-content: center;
            padding: 20px; opacity: 0; pointer-events: none; transition: opacity 0.3s;
        }
        .modal-wrap.open { opacity: 1; pointer-events: all; }
        .modal-overlay {
            position: absolute; inset: 0;
            background: rgba(0,0,0,0.85); backdrop-filter: blur(8px);
        }
        .modal-box {
            position: relative; z-index: 1; background: var(--card);
            border-radius: 16px; overflow: hidden; width: 100%; max-width: 860px;
            max-height: 90vh; overflow-y: auto;
        }
        .modal-hero { position: relative; height: 320px; background-size: cover; background-position: center top; }
        .modal-close {
            position: absolute; top: 14px; left: 14px;
            background: rgba(0,0,0,0.7); border: none; color: #fff;
            width: 36px; height: 36px; border-radius: 50%; cursor: pointer; z-index: 2;
        }
        .trailer-btn {
            display: flex; align-items: center; gap: 12px;
            background: linear-gradient(135deg, #e50914, #b0060f); color: #fff;
            border: none; border-radius: 10px; padding: 14px 28px;
            cursor: pointer; width: 100%; justify-content: center; margin-bottom: 14px;
        }
        .trailer-player { display: none; width: 100%; aspect-ratio: 16/9; border-radius: 10px; overflow: hidden; margin-bottom: 20px; }
        .trailer-player.open { display: block; }
        .trailer-player iframe { width: 100%; height: 100%; border: none; }
        .modal-tag { background: rgba(229,9,20,0.15); color: var(--accent); border: 1px solid rgba(229,9,20,0.25); font-size: 0.75em; padding: 4px 12px; border-radius: 20px; display: inline-block; margin: 2px; }
        .modal-section { margin-bottom: 20px; }
        .modal-section h4 { font-size: 0.9em; font-weight: 700; color: var(--accent); margin-bottom: 8px; }
        .modal-section p { font-size: 0.9em; color: var(--text2); line-height: 1.75; }
        
        .comment-section { margin: 50px 0; border-top: 1px solid var(--border); padding-top: 44px; }
        .comment-form { display: flex; flex-direction: column; gap: 12px; margin-bottom: 30px; }
        .comment-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .comment-box {
            width: 100%; background: rgba(255,255,255,0.05);
            border: 1px solid var(--border); border-radius: 8px;
            padding: 12px 16px; color: var(--text);
        }
        .comment-submit {
            align-self: flex-end; background: var(--accent); color: #fff;
            border: none; border-radius: 8px; padding: 12px 28px; cursor: pointer;
        }
        .comments-list { display: flex; flex-direction: column; gap: 12px; }
        .comment-item {
            background: rgba(255,255,255,0.03); border: 1px solid var(--border);
            border-radius: 10px; padding: 16px 20px; display: flex; gap: 14px;
        }
        .c-avatar { width: 40px; height: 40px; border-radius: 50%; background: linear-gradient(135deg, var(--accent), #ff6b35); display: flex; align-items: center; justify-content: center; font-weight: 800; }
        .ig-section { text-align: center; margin: 36px 0; }
        .ig-btn {
            display: inline-flex; align-items: center; gap: 10px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: #fff; padding: 13px 32px; border-radius: 50px; text-decoration: none;
        }
        .footer { background: rgba(0,0,0,0.35); border-top: 1px solid var(--border); padding: 28px 48px; text-align: center; }
        .scroll-top {
            position: fixed; bottom: 28px; left: 28px;
            width: 42px; height: 42px; background: var(--accent); border: none;
            border-radius: 50%; color: #fff; cursor: pointer;
            opacity: 0; transition: opacity 0.3s; z-index: 800;
        }
        .scroll-top.show { opacity: 1; }
        
        @media(max-width:768px) {
            .navbar { padding: 0 16px; }
            .nav-links { display: none; }
            .main { padding: 0 16px 60px; }
            .movie-grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
            .card-poster { height: 215px; }
            .comment-row { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

<nav class="navbar" id="navbar">
    <span class="brand">Srusht Movies</span>
    <ul class="nav-links">
        <li><a onclick="scrollTo(0,0)">سەرەکی</a></li>
        <li><a onclick="document.getElementById('favSec').scrollIntoView({behavior:'smooth'})">دلخوازەکانم</a></li>
        <li><a onclick="document.getElementById('gridSec').scrollIntoView({behavior:'smooth'})">فیلمەکان</a></li>
    </ul>
    <div class="nav-right">
        <button class="mode-btn" id="modeBtn"><i class="fas fa-moon"></i><span>شەو</span></button>
    </div>
</nav>

<section class="hero" id="heroSec">
    <div class="hero-backdrop" id="heroBackdrop"></div>
    <div class="hero-overlay-top"></div>
    <div class="hero-poster-wrap" id="heroPosterWrap">
        <img class="hero-poster-img" id="heroPosterImg" src="" alt="">
    </div>
    <div class="hero-center">
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
        <button class="tab-btn" data-tab="crime">Crime</button>
        <button class="tab-btn" data-tab="top9">⭐ +8.5</button>
    </div>

    <section class="fav-section" id="favSec">
        <div class="sec-title"><i class="fas fa-heart" style="color:var(--accent)"></i> دلخوازەکانم <span class="count" id="favCount">(0)</span></div>
        <div class="fav-empty" id="favEmpty"><i class="fas fa-heart-broken"></i> هیچ فیلمێک زیاد نەکردووە - لەسەر ❤️ کلیک بکە</div>
        <div class="fav-row" id="favRow" style="display:none"></div>
    </section>

    <section id="gridSec">
        <div class="sec-title"><i class="fas fa-film" style="color:var(--accent)"></i> فیلمەکان <span class="count" id="movieCount"></span></div>
        <div class="movie-grid" id="movieGrid"></div>
        <button class="load-more" id="loadMore" style="display:none"><i class="fas fa-chevron-down"></i> زیاتر باربکە</button>
    </section>

    <div class="ig-section">
        <a href="https://www.instagram.com/lipri_26" class="ig-btn" target="_blank"><i class="fab fa-instagram"></i> سەردانی ئینستاگرام بکە</a>
    </div>

    <section class="comment-section" id="commentSec">
        <div class="sec-title"><i class="fas fa-comments" style="color:var(--accent)"></i> کۆمینتەکان <span class="count" id="commentCount">(0)</span></div>
        <div class="comment-form">
            <div class="comment-row">
                <input class="comment-box" id="cName" placeholder="ناوت...">
                <input class="comment-box" id="cMovie" placeholder="ناوی فیلم">
            </div>
            <textarea class="comment-box" id="cText" rows="3" placeholder="کۆمینتەکەت بنووسە..."></textarea>
            <button class="comment-submit" onclick="addComment()"><i class="fas fa-paper-plane"></i> ناردن</button>
        </div>
        <div class="comments-list" id="commentsList"></div>
    </section>
</main>

<footer class="footer">
    <p>دروستکراوە بە ❤️ بۆ کوردەکان | <a href="https://www.instagram.com/lipri_26" target="_blank">@lipri_26</a> | Srusht Movies &copy; 2025</p>
</footer>

<button class="scroll-top" id="scrollTop" onclick="scrollTo({top:0,behavior:'smooth'})"><i class="fas fa-arrow-up"></i></button>

<div class="modal-wrap" id="modalWrap">
    <div class="modal-overlay" onclick="closeModal()"></div>
    <div class="modal-box" id="modalBox"></div>
</div>

<script>
// ===== 40 فیلم بە وێنەی ڕاستەقینە =====
const MOVIES = [
    { id:0, en:"Fight Club", ku:"فایت کلاب", year:1999, rating:8.8, duration:"139 خول", genre:["thriller","drama"], age:"R", director:"David Fincher", cast:"Brad Pitt, Edward Norton", country:"ئەمریکا", language:"ئینگلیزی", plot:"کارمەندێکی ناڕازی کۆمەڵێکی شەڕی نهێنی دروست دەکات.", awards:["Oscar: Best Editing"], trivia:"کتێبەکە لە 1996 نووسراوە.", trailer:"qtRKdVHc-cE", poster:"https://m.media-amazon.com/images/M/MV5BOTgyMjc3ODk2MV5BMl5BanBnXkFtZTgwNTA4Mzg5NTM@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BOTgyMjc3ODk2MV5BMl5BanBnXkFtZTgwNTA4Mzg5NTM@._V1_.jpg" },
    { id:1, en:"Inception", ku:"ئینسپشن", year:2010, rating:8.8, duration:"148 خول", genre:["scifi","thriller"], age:"PG-13", director:"Christopher Nolan", cast:"Leonardo DiCaprio, Joseph Gordon-Levitt", country:"ئەمریکا", language:"ئینگلیزی", plot:"دزێک کە دەتوانێت بچێتە ناو خەونی خەڵکی تر.", awards:["Oscar: Best Visual Effects"], trivia:"نۆلان 10 ساڵ کاری لەسەر کردووە.", trailer:"YoHD9XEInc0", poster:"https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_.jpg" },
    { id:2, en:"The Dark Knight", ku:"شێوازە تاریکەکە", year:2008, rating:9.0, duration:"152 خول", genre:["thriller","crime"], age:"PG-13", director:"Christopher Nolan", cast:"Christian Bale, Heath Ledger", country:"ئەمریکا", language:"ئینگلیزی", plot:"بەتمن دژی جۆکەر.", awards:["Oscar: Best Supporting Actor"], trivia:"Heath Ledger خەڵاتی Oscar ی وەرگرت.", trailer:"EXeTwQWrcwY", poster:"https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_.jpg" },
    { id:3, en:"Parasite", ku:"پاراسایت", year:2019, rating:8.5, duration:"132 خول", genre:["thriller","drama"], age:"R", director:"Bong Joon-ho", cast:"Song Kang-ho, Lee Sun-kyun", country:"کۆریا", language:"کۆری", plot:"خێزانێکی هەژار خۆیان دەدەنە مامۆستا.", awards:["Oscar: Best Picture"], trivia:"یەکەم فیلمی کۆریایی کە Oscar ی وەرگرت.", trailer:"5xH0HfJHsaY", poster:"https://m.media-amazon.com/images/M/MV5BYWZjMjk3ZTItODQ2ZC00NTY5LWE0ZDYtZTI3MjcwN2Q5NTVkXkEyXkFqcGdeQXVyODk4OTc3MTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BYWZjMjk3ZTItODQ2ZC00NTY5LWE0ZDYtZTI3MjcwN2Q5NTVkXkEyXkFqcGdeQXVyODk4OTc3MTY@._V1_.jpg" },
    { id:4, en:"Joker", ku:"جۆکەر", year:2019, rating:8.4, duration:"122 خول", genre:["thriller","drama"], age:"R", director:"Todd Phillips", cast:"Joaquin Phoenix, Robert De Niro", country:"ئەمریکا", language:"ئینگلیزی", plot:"Arthur Fleck دەبێتە Joker.", awards:["Oscar: Best Actor"], trivia:"Joaquin Phoenix 52 پاوند وزەی لادا.", trailer:"zAGVQLHvwOY", poster:"https://m.media-amazon.com/images/M/MV5BNGVjNWI4ZGUtNzE0MS00YTJmLWE0ZDYtY2VkZDhhYmQ2OTM4XkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNGVjNWI4ZGUtNzE0MS00YTJmLWE0ZDYtY2VkZDhhYmQ2OTM4XkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_.jpg" },
    { id:5, en:"Interstellar", ku:"ئینتەرستێلار", year:2014, rating:8.6, duration:"169 خول", genre:["scifi","drama"], age:"PG-13", director:"Christopher Nolan", cast:"Matthew McConaughey, Anne Hathaway", country:"ئەمریکا", language:"ئینگلیزی", plot:"گروپێک بۆ دۆزینەوەی گەردووی نوێ دەچن.", awards:["Oscar: Best Visual Effects"], trivia:"Kip Thorne فیزیکدانی نۆبێل یارمەتی دا.", trailer:"zSWdZVtXT7E", poster:"https://m.media-amazon.com/images/M/MV5BZjdkOTU3MDktN2IxOS00OGEyLWFmMjktY2FiMmZkNWIyODZiXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BZjdkOTU3MDktN2IxOS00OGEyLWFmMjktY2FiMmZkNWIyODZiXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg" },
    { id:6, en:"The Shawshank Redemption", ku:"ڕزگاری لە شاوشەنک", year:1994, rating:9.3, duration:"142 خول", genre:["drama"], age:"R", director:"Frank Darabont", cast:"Tim Robbins, Morgan Freeman", country:"ئەمریکا", language:"ئینگلیزی", plot:"پیاوێک بە تۆمەتی درۆ لە زیندان دادەنرێت.", awards:["Oscar: Best Picture"], trivia:"پڕ ڕیتینگترین فیلمی IMDb.", trailer:"6hB3S9bIaco", poster:"https://m.media-amazon.com/images/M/MV5BMDFkYTc0MGEtZmNhMC00ZDIzLWFmNTEtODM1ZmRlYWMwMWFmXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMDFkYTc0MGEtZmNhMC00ZDIzLWFmNTEtODM1ZmRlYWMwMWFmXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg" },
    { id:7, en:"Pulp Fiction", ku:"پاڵپ فیکشن", year:1994, rating:8.9, duration:"154 خول", genre:["crime","thriller"], age:"R", director:"Quentin Tarantino", cast:"John Travolta, Uma Thurman", country:"ئەمریکا", language:"ئینگلیزی", plot:"چەند چیرۆکی پەیوەندیدار لە جیهانی تاواندا.", awards:["Oscar: Best Screenplay"], trivia:"Tarantino سکریپتەکەی لە 3 مانگدا نووسی.", trailer:"s7EdQ4FqbhY", poster:"https://m.media-amazon.com/images/M/MV5BNGNhMDIzZTUtNTBlZi00MTRlLWFjM2ItYzViMjE3YzI5MjljXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNGNhMDIzZTUtNTBlZi00MTRlLWFjM2ItYzViMjE3YzI5MjljXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg" },
    { id:8, en:"The Godfather", ku:"باوکی خودا", year:1972, rating:9.2, duration:"175 خول", genre:["crime","drama"], age:"R", director:"Francis Ford Coppola", cast:"Marlon Brando, Al Pacino", country:"ئەمریکا", language:"ئینگلیزی", plot:"خێزانی کۆرلێۆن لە جیهانی مافیادا.", awards:["Oscar: Best Picture"], trivia:"مەزنترین فیلمی مێژوو.", trailer:"sY1S34973zA", poster:"https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg" },
    { id:9, en:"Goodfellas", ku:"خەڵکی باش", year:1990, rating:8.7, duration:"145 خول", genre:["crime","thriller"], age:"R", director:"Martin Scorsese", cast:"Robert De Niro, Ray Liotta", country:"ئەمریکا", language:"ئینگلیزی", plot:"ژیانی Henry Hill لە مافیادا.", awards:["Oscar: Best Supporting Actor"], trivia:"Scorsese و De Niro شەشەمین هاوکاری.", trailer:"qo5jJpHtZ1E", poster:"https://m.media-amazon.com/images/M/MV5BY2NkZjEzMDgtN2RjYy00YzM1LWI4ZmQtMjIwYjFjNmI3ZGEwXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BY2NkZjEzMDgtN2RjYy00YzM1LWI4ZmQtMjIwYjFjNmI3ZGEwXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg" },
    { id:10, en:"Se7en", ku:"حەفت", year:1995, rating:8.6, duration:"127 خول", genre:["thriller","crime"], age:"R", director:"David Fincher", cast:"Brad Pitt, Morgan Freeman", country:"ئەمریکا", language:"ئینگلیزی", plot:"کوشتارچیێک بەپێی حەفت گوناهی گەورە.", awards:["Oscar: Best Editing"], trivia:"Kevin Spacey لە کرێدیتەکان دانەنراوە.", trailer:"znmZoVkCjpI", poster:"https://m.media-amazon.com/images/M/MV5BOTUwODM5MTctZjczMi00OTk4LTgxNWUtNmVhMjU5NTA5M2U0XkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BOTUwODM5MTctZjczMi00OTk4LTgxNWUtNmVhMjU5NTA5M2U0XkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg" },
    { id:11, en:"The Matrix", ku:"ماتریکس", year:1999, rating:8.7, duration:"136 خول", genre:["scifi"], age:"R", director:"Wachowski", cast:"Keanu Reeves, Laurence Fishburne", country:"ئەمریکا", language:"ئینگلیزی", plot:"نیۆ ڕاستی ڕاستەقینە دەدۆزێتەوە.", awards:["Oscar: Best Visual Effects"], trivia:"تەکنیکای Bullet Time ی داهێنا.", trailer:"vKQi3bBA1y8", poster:"https://m.media-amazon.com/images/M/MV5BNzQzOTk3OTAtNDQ0Zi00ZTVkLWI0MTEtMDllZjNkYzNjNTc4L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNzQzOTk3OTAtNDQ0Zi00ZTVkLWI0MTEtMDllZjNkYzNjNTc4L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg" },
    { id:12, en:"Gladiator", ku:"گلادیاتۆر", year:2000, rating:8.5, duration:"155 خول", genre:["drama"], age:"R", director:"Ridley Scott", cast:"Russell Crowe, Joaquin Phoenix", country:"ئەمریکا", language:"ئینگلیزی", plot:"ژەنەڕالێک دەبێتە گلادیاتۆر.", awards:["Oscar: Best Picture"], trivia:"Russell Crowe بۆ ئەم ڕۆڵە Oscar ی وەرگرت.", trailer:"P5ieIbInFpg", poster:"https://m.media-amazon.com/images/M/MV5BMDliMmNhNDEtODUyOS00MjNlLTgxODEtN2U3NzIxMGVkZTA1L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMDliMmNhNDEtODUyOS00MjNlLTgxODEtN2U3NzIxMGVkZTA1L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg" },
    { id:13, en:"Forrest Gump", ku:"فۆڕێست گامپ", year:1994, rating:8.8, duration:"142 خول", genre:["drama"], age:"PG-13", director:"Robert Zemeckis", cast:"Tom Hanks, Robin Wright", country:"ئەمریکا", language:"ئینگلیزی", plot:"پیاوێکی سادە بەشداربووی چەندین ڕووداوی مێژووییە.", awards:["Oscar: Best Picture"], trivia:"Tom Hanks بەرامبەر ئەم ڕۆڵە 40 ملیۆن دۆلاری وەرگرت.", trailer:"bLvqoHBqjgI", poster:"https://m.media-amazon.com/images/M/MV5BNWIwODRlZTUtY2U3ZS00Yzg1LWJhNzYtMmZiYmEyNmU1NjMzXkEyXkFqcGdeQXVyMTQxNzMzNDI@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNWIwODRlZTUtY2U3ZS00Yzg1LWJhNzYtMmZiYmEyNmU1NjMzXkEyXkFqcGdeQXVyMTQxNzMzNDI@._V1_.jpg" },
    { id:14, en:"The Silence of the Lambs", ku:"بێدەنگی بەرخەکان", year:1991, rating:8.6, duration:"118 خول", genre:["thriller","crime"], age:"R", director:"Jonathan Demme", cast:"Jodie Foster, Anthony Hopkins", country:"ئەمریکا", language:"ئینگلیزی", plot:"ئەفسەرێکی FBI یارمەتی دکتۆر لێکتەر دەدات.", awards:["Oscar: Best Picture"], trivia:"تەنها 3 فیلم کە پێنج خەڵاتی سەرەکی Oscar ی وەرگرتووە.", trailer:"W6Mm8Sbe__o", poster:"https://m.media-amazon.com/images/M/MV5BNjNhZTk0ZmEtNjJhMi00YzZmLTgyYTMtZDAwNmU1YTIzYjMyXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNjNhZTk0ZmEtNjJhMi00YzZmLTgyYTMtZDAwNmU1YTIzYjMyXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg" },
    { id:15, en:"Schindler's List", ku:"لیستی شیندلەر", year:1993, rating:9.0, duration:"195 خول", genre:["drama"], age:"R", director:"Steven Spielberg", cast:"Liam Neeson, Ben Kingsley", country:"ئەمریکا", language:"ئینگلیزی", plot:"بازرگانێکی ئەڵمانی ژیانی جولەکەکان ڕزگار دەکات.", awards:["Oscar: Best Picture"], trivia:"Spielberg بەبێ مووچە فیلمەکەی دروست کرد.", trailer:"gG22XNhtnoY", poster:"https://m.media-amazon.com/images/M/MV5BNDE4OTMxMTctNmRhYy00NWE2LTg3YzItYTk3M2UwOTU5NjM4XkEyXkFqcGdeQXVyMTUzMDUzNTI3._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNDE4OTMxMTctNmRhYy00NWE2LTg3YzItYTk3M2UwOTU5NjM4XkEyXkFqcGdeQXVyMTUzMDUzNTI3._V1_.jpg" },
    { id:16, en:"The Departed", ku:"دچووەتەوە", year:2006, rating:8.5, duration:"151 خول", genre:["crime","thriller"], age:"R", director:"Martin Scorsese", cast:"Leonardo DiCaprio, Matt Damon", country:"ئەمریکا", language:"ئینگلیزی", plot:"پۆلیسێک لە نێو کۆمەڵی جینایی دانراوە.", awards:["Oscar: Best Picture"], trivia:"Scorsese یەکەم Oscar ی بردەوە.", trailer:"SGWvwjq0hDE", poster:"https://m.media-amazon.com/images/M/MV5BMTI1MTY2OTIxNV5BMl5BanBnXkFtZTYwNjQ4NjY3._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTI1MTY2OTIxNV5BMl5BanBnXkFtZTYwNjQ4NjY3._V1_.jpg" },
    { id:17, en:"Whiplash", ku:"ویپلاش", year:2014, rating:8.5, duration:"106 خول", genre:["drama"], age:"R", director:"Damien Chazelle", cast:"Miles Teller, J.K. Simmons", country:"ئەمریکا", language:"ئینگلیزی", plot:"تیلمیزانی درامز لەژێر فشاری مامۆستایەکی تونددا.", awards:["Oscar: Best Supporting Actor"], trivia:"J.K. Simmons بۆ ئەم ڕۆڵە خەڵاتی Oscar ی وەرگرت.", trailer:"7d65HCMEQls", poster:"https://m.media-amazon.com/images/M/MV5BOTA5NDZlZGUtMjAxOS00YTRkLTkwYmMtYWQ0NWEwZDZiNjEzXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BOTA5NDZlZGUtMjAxOS00YTRkLTkwYmMtYWQ0NWEwZDZiNjEzXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg" },
    { id:18, en:"Django Unchained", ku:"جانگۆ ئانچەینت", year:2012, rating:8.4, duration:"165 خول", genre:["crime","drama"], age:"R", director:"Quentin Tarantino", cast:"Jamie Foxx, Christoph Waltz", country:"ئەمریکا", language:"ئینگلیزی", plot:"کۆیلێکی ئازادکراو هاوسەری خۆی ڕزگار دەکات.", awards:["Oscar: Best Supporting Actor"], trivia:"Christoph Waltz دووەم Oscar ی بردەوە.", trailer:"0fUCuvNlOCg", poster:"https://m.media-amazon.com/images/M/MV5BMjIyNTQ5NjQ1OV5BMl5BanBnXkFtZTcwODg1MDU4OA@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMjIyNTQ5NjQ1OV5BMl5BanBnXkFtZTcwODg1MDU4OA@@._V1_.jpg" },
    { id:19, en:"The Wolf of Wall Street", ku:"گورگی وال ستریت", year:2013, rating:8.2, duration:"180 خول", genre:["crime","drama"], age:"R", director:"Martin Scorsese", cast:"Leonardo DiCaprio, Jonah Hill", country:"ئەمریکا", language:"ئینگلیزی", plot:"بازرگانێکی سەرمایەداری کۆمپانیای خۆی دەکاتەوە.", awards:["Oscar: Best Actor"], trivia:"DiCaprio 500 وشەی ناسێک لە فیلمەکەدا دەڵێت.", trailer:"pabEtIERlic", poster:"https://m.media-amazon.com/images/M/MV5BMjIxMjgxNTk0MF5BMl5BanBnXkFtZTgwNjIyOTg2MDE@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMjIxMjgxNTk0MF5BMl5BanBnXkFtZTgwNjIyOTg2MDE@._V1_.jpg" },
    { id:20, en:"The Green Mile", ku:"میلە سەوزەکە", year:1999, rating:8.6, duration:"189 خول", genre:["drama"], age:"R", director:"Frank Darabont", cast:"Tom Hanks, Michael Clarke Duncan", country:"ئەمریکا", language:"ئینگلیزی", plot:"پاسەوانێکی زیندان پەیوەندی بە دیلێکی تایبەتەوە دەکات.", awards:["Oscar: Best Picture"], trivia:"فیلمەکە درێژترین فیلمی Darabont e.", trailer:"Ki4haFrFRUw", poster:"https://m.media-amazon.com/images/M/MV5BMTUxMzQyNjA5MF5BMl5BanBnXkFtZTYwOTU2NTY3._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTUxMzQyNjA5MF5BMl5BanBnXkFtZTYwOTU2NTY3._V1_.jpg" },
    { id:21, en:"American History X", ku:"مێژووی ئەمریکی X", year:1998, rating:8.5, duration:"119 خول", genre:["drama","crime"], age:"R", director:"Tony Kaye", cast:"Edward Norton, Edward Furlong", country:"ئەمریکا", language:"ئینگلیزی", plot:"پێشەوایەکی نەتەوەپەروەست لە زیندانەوە دێتەدەر.", awards:["Oscar: Best Actor"], trivia:"Edward Norton بۆ ئەم ڕۆڵە نومزەتی Oscar ی هەبوو.", trailer:"XfQYHqkXyXc", poster:"https://m.media-amazon.com/images/M/MV5BZTJhN2FkYWEtMGI0My00YWM4LWI2MjAtM2UwNjY4MTlmYzc2XkEyXkFqcGdeQXVyNjc3MjQzNTI@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BZTJhN2FkYWEtMGI0My00YWM4LWI2MjAtM2UwNjY4MTlmYzc2XkEyXkFqcGdeQXVyNjc3MjQzNTI@._V1_.jpg" },
    { id:22, en:"Casino", ku:"کازینۆ", year:1995, rating:8.2, duration:"178 خول", genre:["crime","thriller"], age:"R", director:"Martin Scorsese", cast:"Robert De Niro, Joe Pesci", country:"ئەمریکا", language:"ئینگلیزی", plot:"کازینۆیەک لە لاس ڤێگاس لەژێر کۆنتڕۆڵی مافیادا.", awards:["Golden Globe: Best Actor"], trivia:"Scorsese و De Niro هەشتەمین هاوکاری.", trailer:"YFyBki1eET4", poster:"https://m.media-amazon.com/images/M/MV5BMTcxOWYzNDYtYmM4YS00N2NkLTg0YTEtYzYwNzM4MzI3YWI4XkEyXkFqcGdeQXVyNjc1NTYyMjg@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTcxOWYzNDYtYmM4YS00N2NkLTg0YTEtYzYwNzM4MzI3YWI4XkEyXkFqcGdeQXVyNjc1NTYyMjg@._V1_.jpg" },
    { id:23, en:"Braveheart", ku:"دڵی ئازا", year:1995, rating:8.3, duration:"178 خول", genre:["drama"], age:"R", director:"Mel Gibson", cast:"Mel Gibson, Sophie Marceau", country:"ئەمریکا", language:"ئینگلیزی", plot:"شەڕی سکۆتلەندییەکان بۆ سەربەخۆیی.", awards:["Oscar: Best Picture"], trivia:"Mel Gibson بەرامبەر ئەم فیلمە Oscar ی بردەوە.", trailer:"wj0cz8cPAME", poster:"https://m.media-amazon.com/images/M/MV5BMzkzMmU0YTYtOWIzYi00YmUyLWE2MjAtODAyNzU4N2UzNmQ4XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMzkzMmU0YTYtOWIzYi00YmUyLWE2MjAtODAyNzU4N2UzNmQ4XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg" },
    { id:24, en:"Gone Girl", ku:"کچە ونبووە", year:2014, rating:8.1, duration:"149 خول", genre:["thriller"], age:"R", director:"David Fincher", cast:"Ben Affleck, Rosamund Pike", country:"ئەمریکا", language:"ئینگلیزی", plot:"ژنی پیاوێک ناپەیدا دەبێت.", awards:["Oscar: Best Actress"], trivia:"Rosamund Pike نومزەتی Oscar ی هەبوو.", trailer:"2-_-1nJf8Vg", poster:"https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NTczNzE@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NTczNzE@._V1_.jpg" },
    { id:25, en:"Prisoners", ku:"بندیەکان", year:2013, rating:8.1, duration:"153 خول", genre:["thriller","crime"], age:"R", director:"Denis Villeneuve", cast:"Hugh Jackman, Jake Gyllenhaal", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو کچ ناپەیدا دەبن، باوکیان خۆی دەگەڕێت.", awards:["Oscar: Best Cinematography"], trivia:"Denis Villeneuve یەکەم فیلمی ئینگلیزی بوو.", trailer:"bPXuGcVhRlU", poster:"https://m.media-amazon.com/images/M/MV5BMTg0NTIzMjQ1NV5BMl5BanBnXkFtZTcwNDc3MzM5OQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTg0NTIzMjQ1NV5BMl5BanBnXkFtZTcwNDc3MzM5OQ@@._V1_.jpg" },
    { id:26, en:"Oldboy", ku:"ئۆڵدبۆی", year:2003, rating:8.1, duration:"120 خول", genre:["thriller","crime"], age:"R", director:"Park Chan-wook", cast:"Choi Min-sik, Yoo Ji-tae", country:"کۆریا", language:"کۆری", plot:"پیاوێک 15 ساڵ لە ژووری نهێنیدا دادەنرێت.", awards:["Cannes: Grand Prix"], trivia:"Quentin Tarantino ئەم فیلمەی خۆش دەوێت.", trailer:"2Hx1U_ZtR4", poster:"https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjIyMQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjIyMQ@@._V1_.jpg" },
    { id:27, en:"Shutter Island", ku:"شوتەر ئایلەند", year:2010, rating:8.2, duration:"138 خول", genre:["thriller"], age:"R", director:"Martin Scorsese", cast:"Leonardo DiCaprio, Mark Ruffalo", country:"ئەمریکا", language:"ئینگلیزی", plot:"دیتێکتیڤێک لە دوای گیراوەیەکی مەزن.", awards:["Saturn Award"], trivia:"DiCaprio کتێبی دەروونناسی خوێندووە.", trailer:"5iaYLCiq5RM", poster:"https://m.media-amazon.com/images/M/MV5BYzhiNDkyNzktNTZmYS00ZTBkLTk2MDAtM2U0YjU1MzgxZjgzXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BYzhiNDkyNzktNTZmYS00ZTBkLTk2MDAtM2U0YjU1MzgxZjgzXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg" },
    { id:28, en:"The Prestige", ku:"دەستگیری", year:2006, rating:8.5, duration:"130 خول", genre:["thriller","drama"], age:"PG-13", director:"Christopher Nolan", cast:"Christian Bale, Hugh Jackman", country:"ئەمریکا", language:"ئینگلیزی", plot:"دوو سیحرباز دەبنە دوژمن.", awards:["Oscar: Best Cinematography"], trivia:"نۆلان دوو سکریپتی جیاواز نووسی.", trailer:"RLtaA9fFNXU", poster:"https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_.jpg" },
    { id:29, en:"Memento", ku:"مەمینتۆ", year:2000, rating:8.4, duration:"113 خول", genre:["thriller"], age:"R", director:"Christopher Nolan", cast:"Guy Pearce, Carrie-Anne Moss", country:"ئەمریکا", language:"ئینگلیزی", plot:"پیاوێک ناخۆشی بیرنەکردنەوەی هەیە.", awards:["Oscar: Best Editing"], trivia:"فیلمەکە بە دوو شێواز دەتوانرێت ببینرێت.", trailer:"0vS0E9bBSL0", poster:"https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg" },
    { id:30, en:"The Sixth Sense", ku:"هەستی شەشەم", year:1999, rating:8.1, duration:"107 خول", genre:["thriller"], age:"PG-13", director:"M. Night Shyamalan", cast:"Bruce Willis, Haley Joel Osment", country:"ئەمریکا", language:"ئینگلیزی", plot:"کوڕێک قسەی مردووان دەکات.", awards:["Oscar: Best Director"], trivia:"فیلمەکە 672 ملیۆن دۆلارە.", trailer:"VG9AGf66tXM", poster:"https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzU1Ni00Mzg2LTlhM2MtMzU4NmNjOTAyNTZmXkEyXkFqcGdeQXVyMTUzMDUzNTI3._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzU1Ni00Mzg2LTlhM2MtMzU4NmNjOTAyNTZmXkEyXkFqcGdeQXVyMTUzMDUzNTI3._V1_.jpg" },
    { id:31, en:"No Country for Old Men", ku:"وڵاتێک بۆ پیرەمێرد نییە", year:2007, rating:8.2, duration:"122 خول", genre:["crime","thriller"], age:"R", director:"Coen Brothers", cast:"Tommy Lee Jones, Javier Bardem", country:"ئەمریکا", language:"ئینگلیزی", plot:"ڕاوچیێک دوو ملیۆن دۆلار دەدۆزێتەوە.", awards:["Oscar: Best Picture"], trivia:"Javier Bardem ترسناکترین ڤیلانی مێژوو.", trailer:"38A__WT3-o0", poster:"https://m.media-amazon.com/images/M/MV5BMjA5Njk3MjM4OV5BMl5BanBnXkFtZTcwMTc5MTE1MQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMjA5Njk3MjM4OV5BMl5BanBnXkFtZTcwMTc5MTE1MQ@@._V1_.jpg" },
    { id:32, en:"The Usual Suspects", ku:"گومانلێکراوەکان", year:1995, rating:8.5, duration:"106 خول", genre:["crime"], age:"R", director:"Bryan Singer", cast:"Kevin Spacey, Gabriel Byrne", country:"ئەمریکا", language:"ئینگلیزی", plot:"پێنج تاوانبار کۆدەبنەوە.", awards:["Oscar: Best Supporting Actor"], trivia:"Keyser Söze یەکێک لە باشترین ڤیلانەکانە.", trailer:"oiXdPolca5w", poster:"https://m.media-amazon.com/images/M/MV5BYTViYTE3ZGQtNDBlMC00ZTAyLTkyODMtZGRiZDg0MjA2YThkXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BYTViYTE3ZGQtNDBlMC00ZTAyLTkyODMtZGRiZDg0MjA2YThkXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg" },
    { id:33, en:"Black Swan", ku:"قووی تاریک", year:2010, rating:8.0, duration:"108 خول", genre:["thriller","drama"], age:"R", director:"Darren Aronofsky", cast:"Natalie Portman, Mila Kunis", country:"ئەمریکا", language:"ئینگلیزی", plot:"ڕاقیسەیەک بۆ ڕۆڵی Swan Lake.", awards:["Oscar: Best Actress"], trivia:"Natalie Portman 11 مانگ ئامادەکاری کرد.", trailer:"5jaI1XZM-hY", poster:"https://m.media-amazon.com/images/M/MV5BNzY2NzI4OTE5MF5BMl5BanBnXkFtZTcwMjMyNDU4Mw@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNzY2NzI4OTE5MF5BMl5BanBnXkFtZTcwMjMyNDU4Mw@@._V1_.jpg" },
    { id:34, en:"Requiem for a Dream", ku:"ئاهەنگی خەونێک", year:2000, rating:8.3, duration:"102 خول", genre:["drama"], age:"R", director:"Darren Aronofsky", cast:"Jared Leto, Jennifer Connelly", country:"ئەمریکا", language:"ئینگلیزی", plot:"چوار کەس تووشی ماددەی دەرمان دەبن.", awards:["Oscar: Best Actress"], trivia:"Ellen Burstyn نومزەتی Oscar ی هەبوو.", trailer:"i1GmxMTwUgs", poster:"https://m.media-amazon.com/images/M/MV5BOTk0ODZmMTAtMzIxOC00ZmJmLTk5MzYtNGU2YjdkMmZmYWI1XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BOTk0ODZmMTAtMzIxOC00ZmJmLTk5MzYtNGU2YjdkMmZmYWI1XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg" },
    { id:35, en:"The Shining", ku:"درەوشانەوە", year:1980, rating:8.4, duration:"146 خول", genre:["thriller"], age:"R", director:"Stanley Kubrick", cast:"Jack Nicholson, Shelley Duvall", country:"ئەمریکا", language:"ئینگلیزی", plot:"نووسەرێک لە مێمانخانەیەکی تاریکدا.", awards:["Saturn Award"], trivia:"Kubrick زیاتر لە 100 دەرفەت سەحنەکانی گرتەوە.", trailer:"S014oGZiSdI", poster:"https://m.media-amazon.com/images/M/MV5BZWFlYmY2M2YtZTA2MC00MDQ1LWI2YTYtMmI4MTVjNTBjY2RkXkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BZWFlYmY2M2YtZTA2MC00MDQ1LWI2YTYtMmI4MTVjNTBjY2RkXkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg" },
    { id:36, en:"Mystic River", ku:"ڕووباری مایستیک", year:2003, rating:7.9, duration:"138 خول", genre:["crime","drama"], age:"R", director:"Clint Eastwood", cast:"Sean Penn, Tim Robbins", country:"ئەمریکا", language:"ئینگلیزی", plot:"سێ هاوڕێی منداڵی پەیوەندیان بە کوشتنێکەوە دەبێت.", awards:["Oscar: Best Actor"], trivia:"Sean Penn بۆ ئەم ڕۆڵە Oscar ی بردەوە.", trailer:"qioU6pW9hIk", poster:"https://m.media-amazon.com/images/M/MV5BMTIzYzIyZThhZTUzLWI4MDgtYzY1Ni1mMWQ5MGQ0Y2M5ZmJfXkFyXkN0TW1ic1VDMzkw@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BMTIzYzIyZThhZTUzLWI4MDgtYzY1Ni1mMWQ5MGQ0Y2M5ZmJfXkFyXkN0TW1ic1VDMzkw@._V1_.jpg" },
    { id:37, en:"Fargo", ku:"فارگۆ", year:1996, rating:8.1, duration:"98 خول", genre:["crime","thriller"], age:"R", director:"Coen Brothers", cast:"Frances McDormand, William H. Macy", country:"ئەمریکا", language:"ئینگلیزی", plot:"ڕفاندنێک لە شاری فارگۆ.", awards:["Oscar: Best Actress"], trivia:"فیلمەکە لەسەر ڕووداوێکی ڕاستەقینەیە.", trailer:"h2tY82z3xXU", poster:"https://m.media-amazon.com/images/M/MV5BN2UwNDc5NmEtNjVjZS00OTI5LWI5Y2QtMWVjNzFkYmI2ZmM1XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BN2UwNDc5NmEtNjVjZS00OTI5LWI5Y2QtMWVjNzFkYmI2ZmM1XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg" },
    { id:38, en:"Heat", ku:"گەرما", year:1995, rating:8.3, duration:"170 خول", genre:["crime","thriller"], age:"R", director:"Michael Mann", cast:"Al Pacino, Robert De Niro", country:"ئەمریکا", language:"ئینگلیزی", plot:"پۆلیس لە دوای دزێکی بانک.", awards:["BAFTA: Best Director"], trivia:"یەکەم جار De Niro و Pacino پێکەوە یارییان کرد.", trailer:"0xbBLJ1YGw4", poster:"https://m.media-amazon.com/images/M/MV5BNjI0NzY4YjgtZTVjZC00MTI0LTk4MTEtMmQ1MjA3NTg2YzA5XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNjI0NzY4YjgtZTVjZC00MTI0LTk4MTEtMmQ1MjA3NTg2YzA5XkEyXkFqcGdeQXVyNTAyODkwOQ@@._V1_.jpg" },
    { id:39, en:"Blade Runner 2049", ku:"بلەید ڕەنەر 2049", year:2017, rating:8.0, duration:"164 خول", genre:["scifi","thriller"], age:"R", director:"Denis Villeneuve", cast:"Ryan Gosling, Harrison Ford", country:"ئەمریکا", language:"ئینگلیزی", plot:"بلەید ڕەنەرێکی نوێ نهێنییەک دەدۆزێتەوە.", awards:["Oscar: Best Cinematography"], trivia:"Roger Deakins یەکەم Oscar ی بردەوە.", trailer:"gCcx85zbxz4", poster:"https://m.media-amazon.com/images/M/MV5BNzA1Njg4NzYxOV5BMl5BanBnXkFtZTgwODk5NjU3MzI@._V1_.jpg", backdrop:"https://m.media-amazon.com/images/M/MV5BNzA1Njg4NzYxOV5BMl5BanBnXkFtZTgwODk5NjU3MzI@._V1_.jpg" }
];

// ===== STATE =====
let favs = JSON.parse(localStorage.getItem('srushtFavs') || '[]');
let comments = JSON.parse(localStorage.getItem('srushtComments') || '[]');
let currentPage = 1;
const perPage = 15;
let activeTab = 'all';
let searchQ = '';

// ===== HERO SETUP =====
(function setupHero() {
    const featured = MOVIES[1];
    const stripMovies = [MOVIES[0], MOVIES[2], MOVIES[4], MOVIES[6], MOVIES[8]];
    document.getElementById('heroBackdrop').style.backgroundImage = `url('${featured.backdrop}')`;
    document.getElementById('heroPosterImg').src = featured.poster;
    document.getElementById('heroPosterWrap').onclick = () => openModal(featured.id);
    document.getElementById('heroFilmInfo').innerHTML = `
        <div class="hero-film-label" style="color:var(--accent); font-size:0.8em;">⬤ فیلمی هەفتە</div>
        <div class="hero-film-title-big" style="font-family:'Bebas Neue'; font-size:2.2em;">${featured.en}</div>
        <button class="hero-cta" onclick="openModal(${featured.id})"><i class="fas fa-info-circle"></i> زانیاری تەواو</button>
    `;
    const row = document.getElementById('heroFilmRow');
    row.innerHTML = '';
    stripMovies.forEach((m, i) => {
        if (i > 0) { const div = document.createElement('div'); div.className = 'hero-film-card-divider'; row.appendChild(div); }
        const card = document.createElement('div');
        card.className = 'hero-film-card';
        card.innerHTML = `<div class="hero-film-card-bg" style="background-image:url('${m.backdrop}')"></div>
            <div class="hero-film-card-info"><div class="hero-film-card-title">${m.en}</div></div>`;
        card.onclick = () => openModal(m.id);
        row.appendChild(card);
    });
})();

function filtered() {
    let list = [...MOVIES];
    if (activeTab === 'thriller') list = list.filter(m => m.genre.includes('thriller'));
    else if (activeTab === 'drama') list = list.filter(m => m.genre.includes('drama'));
    else if (activeTab === 'scifi') list = list.filter(m => m.genre.includes('scifi'));
    else if (activeTab === 'crime') list = list.filter(m => m.genre.includes('crime'));
    else if (activeTab === 'top9') list = list.filter(m => m.rating >= 8.5);
    if (searchQ) list = list.filter(m => m.ku.includes(searchQ) || m.en.toLowerCase().includes(searchQ.toLowerCase()));
    return list;
}

function renderMovies(reset = false) {
    const grid = document.getElementById('movieGrid');
    if (reset) { grid.innerHTML = ''; currentPage = 1; }
    const list = filtered();
    const show = list.slice(0, currentPage * perPage);
    document.getElementById('movieCount').textContent = `(${list.length})`;
    if (show.length === 0) {
        grid.innerHTML = '<div style="text-align:center; padding:60px; color:var(--text2)">هیچ فیلمێک نەدۆزرایەوە</div>';
        document.getElementById('loadMore').style.display = 'none';
        return;
    }
    show.forEach((m) => {
        const isFav = favs.includes(m.id);
        const card = document.createElement('div');
        card.className = 'movie-card';
        card.innerHTML = `
            <img class="card-poster" src="${m.poster}" alt="${m.ku}" loading="lazy" onerror="this.src='https://fakeimg.pl/300x420/1a1a1a/e50914?text=${encodeURIComponent(m.en)}&font=lobster'">
            <button class="fav-btn ${isFav ? 'on' : ''}" data-id="${m.id}"><i class="${isFav ? 'fas' : 'far'} fa-heart"></i></button>
            <span class="age-tag">${m.age}</span>
            <div class="card-info">
                <div class="card-title">${m.ku}</div>
                <div class="card-meta"><span class="card-rating">⭐ ${m.rating}</span><span>${m.year}</span></div>
            </div>
        `;
        card.querySelector('.fav-btn').onclick = e => { e.stopPropagation(); toggleFav(m.id); };
        card.onclick = () => openModal(m.id);
        grid.appendChild(card);
    });
    document.getElementById('loadMore').style.display = (currentPage * perPage) < list.length ? 'block' : 'none';
}

function toggleFav(id) {
    const i = favs.indexOf(id);
    i === -1 ? favs.push(id) : favs.splice(i, 1);
    localStorage.setItem('srushtFavs', JSON.stringify(favs));
    renderFavs();
    document.querySelectorAll(`.fav-btn[data-id="${id}"]`).forEach(b => {
        const on = favs.includes(id);
        b.classList.toggle('on', on);
        b.querySelector('i').className = on ? 'fas fa-heart' : 'far fa-heart';
    });
}

function renderFavs() {
    const row = document.getElementById('favRow');
    const empty = document.getElementById('favEmpty');
    document.getElementById('favCount').textContent = `(${favs.length})`;
    if (!favs.length) { row.style.display = 'none'; empty.style.display = 'block'; return; }
    empty.style.display = 'none'; row.style.display = 'flex'; row.innerHTML = '';
    favs.forEach(id => {
        const m = MOVIES.find(x => x.id === id);
        if (!m) return;
        const c = document.createElement('div');
        c.className = 'fav-mini';
        c.innerHTML = `
            <img class="fav-mini-img" src="${m.poster}" alt="${m.ku}" onerror="this.src='https://fakeimg.pl/140x190/1a1a1a/e50914?text=${m.en}'">
            <button class="fav-mini-remove" data-id="${m.id}"><i class="fas fa-times"></i></button>
            <div class="fav-mini-title">${m.ku}</div>
        `;
        c.querySelector('.fav-mini-remove').onclick = e => { e.stopPropagation(); toggleFav(m.id); };
        c.onclick = () => openModal(m.id);
        row.appendChild(c);
    });
}

function openModal(id) {
    const m = MOVIES.find(x => x.id === id);
    if (!m) return;
    const isFav = favs.includes(m.id);
    document.getElementById('modalBox').innerHTML = `
        <div class="modal-hero" style="background-image:url('${m.poster}')">
            <button class="modal-close" onclick="closeModal()"><i class="fas fa-times"></i></button>
            <div class="modal-hero-title" style="position:absolute; bottom:20px; right:24px;"><h2 style="font-family:'Bebas Neue'; font-size:2em;">${m.ku}</h2><div style="font-size:0.85em; color:#aaa;">${m.en}</div></div>
        </div>
        <div style="padding:24px 28px 32px;">
            <div style="margin-bottom:15px;"><span class="modal-tag">⭐ ${m.rating}</span><span class="modal-tag">${m.year}</span><span class="modal-tag">${m.duration}</span><span class="modal-tag">${m.age}</span></div>
            <button class="modal-fav-btn" onclick="toggleFav(${m.id})" style="background:${isFav ? '#e50914' : 'rgba(229,9,20,0.12)'}; color:${isFav ? '#fff' : '#e50914'}; border:1px solid rgba(229,9,20,0.3); border-radius:8px; padding:10px 20px; margin-bottom:20px; cursor:pointer; width:100%;"><i class="${isFav ? 'fas' : 'far'} fa-heart"></i> ${isFav ? 'لە دلخوازەکانم' : 'زیادکردن بۆ دلخواز'}</button>
            <div class="modal-section"><h4>باسی فیلم</h4><p>${m.plot}</p></div>
            <div class="modal-section"><h4>بازیگەران</h4><p>${m.cast}</p></div>
            <div class="modal-section"><h4>دەرکەوتن</h4><p>${m.director}</p></div>
            <div class="modal-section"><h4>خەڵاتەکان</h4><p>${m.awards.join(', ')}</p></div>
            <div class="modal-section"><h4>زانیاری سەرسوڕهێنەر</h4><p>${m.trivia}</p></div>
        </div>
    `;
    document.getElementById('modalWrap').classList.add('open');
    document.body.style.overflow = 'hidden';
}

function closeModal() {
    document.getElementById('modalWrap').classList.remove('open');
    document.body.style.overflow = '';
}

function doSearch() {
    searchQ = document.getElementById('searchInput').value.trim();
    renderMovies(true);
}

function addComment() {
    const name = document.getElementById('cName').value.trim();
    const text = document.getElementById('cText').value.trim();
    if (!name || !text) return;
    comments.unshift({ name, text, movie: document.getElementById('cMovie').value.trim(), time: new Date().toLocaleDateString('ku') });
    localStorage.setItem('srushtComments', JSON.stringify(comments));
    document.getElementById('cName').value = '';
    document.getElementById('cText').value = '';
    document.getElementById('cMovie').value = '';
    renderComments();
}

function renderComments() {
    const list = document.getElementById('commentsList');
    document.getElementById('commentCount').textContent = `(${comments.length})`;
    list.innerHTML = '';
    comments.forEach(c => {
        const div = document.createElement('div');
        div.className = 'comment-item';
        div.innerHTML = `<div class="c-avatar">${c.name.charAt(0)}</div>
            <div class="c-body"><div class="c-author">${c.name} ${c.movie ? `· ${c.movie}` : ''}</div>
            <div class="c-text">${c.text}</div><div class="c-time">${c.time}</div></div>`;
        list.appendChild(div);
    });
}

document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.onclick = function() {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        activeTab = this.dataset.tab;
        renderMovies(true);
    };
});

document.getElementById('loadMore').onclick = () => { currentPage++; renderMovies(); };
document.getElementById('searchInput').onkeydown = e => { if (e.key === 'Enter') doSearch(); };

const modeBtn = document.getElementById('modeBtn');
if (localStorage.getItem('srushtMode') === 'light') {
    document.body.classList.add('light');
    modeBtn.querySelector('i').className = 'fas fa-sun';
    modeBtn.querySelector('span').textContent = 'ڕۆژ';
}
modeBtn.onclick = () => {
    document.body.classList.toggle('light');
    const isL = document.body.classList.contains('light');
    modeBtn.querySelector('i').className = isL ? 'fas fa-sun' : 'fas fa-moon';
    modeBtn.querySelector('span').textContent = isL ? 'ڕۆژ' : 'شەو';
    localStorage.setItem('srushtMode', isL ? 'light' : 'dark');
};

window.onscroll = () => {
    document.getElementById('navbar').classList.toggle('scrolled', scrollY > 50);
    document.getElementById('scrollTop').classList.toggle('show', scrollY > 400);
};
document.onkeydown = e => { if (e.key === 'Escape') closeModal(); };

renderMovies();
renderFavs();
renderComments();
</script>
</body>
</html>
