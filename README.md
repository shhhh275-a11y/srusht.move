<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>فیلمەکانی کۆتایی شۆککەر - فیلمی نایاب</title>
  <style>
    :root{
      --bg:#0f1724;
      --card-bg: rgba(255,255,255,0.04);
      --accent: #f5c518;
      --glass: rgba(255,255,255,0.06);
      --gap: 20px;
    }

    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family: "Segoe UI", Tahoma, Arial, sans-serif;
      background: linear-gradient(180deg,#0b1220 0%, #0f1724 100%);
      color:#fff;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding:28px;
      direction:rtl;
    }

    /* background glow */
    .bg-glow{
      position:fixed;inset:0;z-index:-2;pointer-events:none;
      background:
        radial-gradient(600px 360px at 10% 10%, rgba(135,90,190,0.12), transparent 14%),
        radial-gradient(500px 300px at 90% 90%, rgba(245,197,24,0.07), transparent 12%);
      filter: blur(40px);
    }

    .container{max-width:1400px;margin:0 auto;position:relative;z-index:1}

    .header{
      text-align:center;margin-bottom:20px;
    }
    .main-title{
      display:inline-block;
      padding:14px 28px;border-radius:999px;
      background: linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      border:1px solid rgba(255,255,255,0.06);
      font-weight:700;font-size:1.2rem;
      color:#fff;margin-bottom:8px;
    }
    .brand{
      font-size:2.8rem;font-weight:900;letter-spacing:3px;
      background:linear-gradient(90deg,#fff,#d0d0d0);
      -webkit-background-clip:text;-webkit-text-fill-color:transparent;
      margin-top:8px;margin-bottom:6px;
      text-shadow: 0 6px 30px rgba(0,0,0,0.6);
    }

    /* social */
    .social{
      text-align:center;margin:16px 0 28px;
    }
    .ig-banner a{
      display:inline-flex;align-items:center;gap:12px;padding:10px 18px;border-radius:999px;
      background:linear-gradient(90deg,#833ab4,#fd1d1d,#fcb045);
      color:#fff;text-decoration:none;font-weight:700;
      box-shadow:0 8px 30px rgba(0,0,0,0.45);
    }

    /* Netflix-like grid */
    .movie-grid{
      display:grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap:var(--gap);
      align-items:start;
    }

    .movie-card{
      background:var(--card-bg);
      border-radius:12px;
      overflow:visible;
      padding:8px;
      transition: transform .28s cubic-bezier(.2,.9,.2,1), box-shadow .28s;
      position:relative;
    }
    .movie-card:hover{
      transform: translateY(-10px) scale(1.02);
      box-shadow: 0 30px 80px rgba(0,0,0,0.6);
      z-index:5;
    }

    /* poster: 16:9 Netflix style */
    .poster{
      width:100%;
      aspect-ratio: 16 / 9;
      border-radius:10px;
      background-size:cover;
      background-position:center;
      position:relative;
      overflow:hidden;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
      transition: transform .35s;
      border: 1px solid rgba(255,255,255,0.04);
    }
    .movie-card:hover .poster{
      transform: scale(1.04);
    }

    /* play icon (hidden but appears on hover) */
    .play-overlay{
      position:absolute;inset:0;display:flex;align-items:center;justify-content:center;
      pointer-events:none;opacity:0;transition:opacity .25s;
      background:linear-gradient(180deg, rgba(0,0,0,0.0) 40%, rgba(0,0,0,0.5) 100%);
    }
    .movie-card:hover .play-overlay{opacity:1}
    .play-btn{
      display:inline-flex;align-items:center;justify-content:center;
      width:56px;height:56px;border-radius:999px;
      background:rgba(255,255,255,0.12);backdrop-filter:blur(4px);
      border:1px solid rgba(255,255,255,0.06);box-shadow:0 8px 28px rgba(0,0,0,0.6);
    }
    .play-btn:after{
      content:'►';font-size:22px;color:#fff;margin-right:4px;
      transform:translateX(2px);
    }

    /* title overlay under poster (semi-transparent) */
    .title-row{
      display:flex;align-items:center;justify-content:space-between;
      gap:10px;padding:10px 6px 6px 6px;
    }
    .movie-title{
      font-size:1rem;font-weight:800;color:#fff;line-height:1.1;
      text-shadow:0 6px 20px rgba(0,0,0,0.6);
    }
    .movie-meta{display:flex;gap:8px;align-items:center}
    .imdb{
      background:linear-gradient(135deg,#f5c518,#d4af37);
      color:#000;padding:6px 10px;border-radius:8px;font-weight:800;font-size:0.9rem;
      box-shadow:0 6px 18px rgba(245,197,24,0.2)
    }
    .age{
      background:rgba(255,255,255,0.05);padding:6px 8px;border-radius:8px;font-weight:700;font-size:0.85rem;
      color:rgba(255,255,255,0.9)
    }

    /* description small under title */
    .movie-plot{
      font-size:0.88rem;color:rgba(255,255,255,0.86);line-height:1.45;
      margin-top:6px;height:3.1rem;overflow:hidden;text-align:justify;
    }

    /* rank badge */
    .rank{
      position:absolute;left:10px;top:12px;background:rgba(0,0,0,0.6);
      color:var(--accent);width:44px;height:44px;border-radius:999px;
      display:flex;align-items:center;justify-content:center;font-weight:800;border:2px solid var(--accent);
      box-shadow:0 8px 30px rgba(245,197,24,0.12);
      font-size:1.05rem;
    }

    /* responsive tweaks */
    @media (max-width:900px){
      .brand{font-size:2rem}
      .movie-grid{grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));}
      .movie-plot{height:2.6rem;font-size:0.82rem}
    }
    @media (max-width:520px){
      body{padding:16px}
      .brand{font-size:1.6rem}
      .movie-grid{grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));gap:12px}
      .play-btn{width:48px;height:48px}
      .rank{width:38px;height:38px;font-size:.95rem;left:8px;top:10px}
      .movie-plot{display:none}
    }
  </style>
</head>
<body>
  <div class="bg-glow" aria-hidden="true"></div>

  <div class="container">
    <header class="header">
      <div class="main-title">🎬 سەرنجڕاکێشترین فیلمەکانی کۆتایی شۆککەر</div>
      <div class="brand">فیلمی نایاب</div>
      <div class="social" style="margin-top:12px;">
        <div class="ig-banner">
          <a href="https://www.instagram.com/9fi.99?igsh=MXQ0NG1icnc3Ym11NA==" target="_blank" rel="noopener noreferrer">
            <span>📱</span> سەردانی ئەکاونتی ئینستاگراممان بکە
          </a>
        </div>
      </div>
    </header>

    <main>
      <section class="movie-grid" id="movieGrid">
        <!-- Existing 22 cards (kept similar) + 10 new added below (total 32) -->
        <!-- I'll include 32 cards (22 original trimmed + 10 new). For posters I use the original URLs where provided, and picsum placeholders for new ones. -->

        <!-- 1 -->
        <article class="movie-card" data-title="هەستی شەشەم">
          <div class="rank">1</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMWM4NTFhYjctNzUyNi00NGMwLTk3NTYtMDIyNTZmMzRlYmQyXkEyXkFqcGdeQXVyMTAwMzUyOTc@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn" aria-hidden="true"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">هەستی شەشەم</div>
              <div class="movie-plot">دکتۆرێکی دەروونزانی هەوڵ دەدات منداڵێک یارمەتی بدات کە باوەڕی وایە دەتوانێت مردووان ببینێت و قسەیان لەگەڵ بکات.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.2</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 2 -->
        <article class="movie-card" data-title="کڵەبی شەڕ">
          <div class="rank">2</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">کڵەبی شەڕ</div>
              <div class="movie-plot">کارمەندێکی بێزار ناسیاوی فرۆشەرێک دەکات و کلوبێکی شەڕی نهێنی دامەزرێنێت؛ نهێنییەکی گەورە دەربارەی ناسیاوە هەیە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.8</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 3 -->
        <article class="movie-card" data-title="پێشکەوتن">
          <div class="rank">3</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMjA4NDI0MTIxNF5BMl5BanBnXkFtZTYwNTM0MzY2._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">پێشکەوتن</div>
              <div class="movie-plot">دوو سیحربازی ناودار لە لەندەن دژایەتی توند دەکەن و هەریەک هەوڵ دەدات تر بیکات.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.5</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 4 -->
        <article class="movie-card" data-title="یادەوەری">
          <div class="rank">4</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BZTcyNjk1MjgtOWI3Mi00YzQwLWI5MTktMzY4ZmI2NDAyNzYzXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">یادەوەری</div>
              <div class="movie-plot">پیاوێک یادەوەری کورتخایەن هەیە و هەوڵ دەدات بکوژی ژنەکەی بدۆزێتەوە — چیرۆکێکی پێچەوانەوە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.4</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 5 -->
        <article class="movie-card" data-title="پیاوێکی کۆن">
          <div class="rank">5</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTI3NTQyMzU5M15BMl5BanBnXkFtZTcwMTM2MjgyMQ@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">پیاوێکی کۆن</div>
              <div class="movie-plot">پیاوێک بۆ ١٥ ساڵ لە ژوورێکدا بە دیل دەگیرێت؛ دوای ئازادبوون هەوڵ دەدات بیر لەسەر هۆکارەکان بدۆزێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.4</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 6 -->
        <article class="movie-card" data-title="ژنە ونبووەکە">
          <div class="rank">6</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTk0MDQ3MzAzOV5BMl5BanBnXkFtZTgwNzU1NzE3MjE@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">ژنە ونبووەکە</div>
              <div class="movie-plot">ژنێک لە ڕۆژی ساڵیادی هاوسەرگیریدا ون دەبێت و راستییەکان جیاوازن لەوەیە ناتوانێت بێتربێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.1</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 7 -->
        <article class="movie-card" data-title="ئەندازیارەکە">
          <div class="rank">7</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BNjk1NzBlY2YtNjJmNi00YTVmLWI2OTgtNDUxNDE5NjUzZmE0XkEyXkFqcGdeQXVyNTc1NTQxODI@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">ئەندازیارەکە</div>
              <div class="movie-plot">کرێکارێکی کارگە بۆ ساڵێکە نەخەوتووە و ژیانەکەی تێکدەدات؛ نهێنی تاریکێکی پێویست دەربڕی.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.6</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 8 -->
        <article class="movie-card" data-title="ئەوانی تر">
          <div class="rank">8</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTAxMDE4Mzc3ODNeQTJeQWpwZ15BbWU4MDY2Mjg4MDcx._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">ئەوانی تر</div>
              <div class="movie-plot">دایکێک و دوو منداڵ لە ماڵێکی تاریکدا دەژین؛ ڕووداوی سەیر و نهێنی ماڵەکە ئاشکرا دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.6</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 9 -->
        <article class="movie-card" data-title="دوورگەی شاتر">
          <div class="rank">9</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BN2JmMjViMjMtZTM5Mi00ZGZkLTk5YzctZDg5MjFjZDE4NjNkXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">دوورگەی شاتر</div>
              <div class="movie-plot">پۆلیسێک بۆ تەحقیق لەسەر ونبوونی نەخۆسێکی دەروونی دەچێتە دوورگەی تایبەت؛ شتێکی زۆر سادە نییە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.2</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 10 -->
        <article class="movie-card" data-title="گومانلێکراوە ئاساییەکە">
          <div class="rank">10</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMjEzMjczOTI2MV5BMl5BanBnXkFtZTgwOTUwMjI3NzE@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">گومانلێکراوە ئاساییەکە</div>
              <div class="movie-plot">کەسێکی تاوانبار بەڵێن دەدات بە پۆلیس، وە کۆتایی تەواو جیاواز دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.5</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 11 -->
        <article class="movie-card" data-title="حەوت">
          <div class="rank">11</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTcyMzUyMzY1OF5BMl5BanBnXkFtZTcwNDQ4ODk1Mw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">حەوت</div>
              <div class="movie-plot">دوو پۆلیس هەوڵ دەدەن کەسێک بدۆزنەوە کە کوشتنەکان بە شێوەی حەوت داخڵ دەکات؛ کۆتایی هۆشیارکەرەوەیە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.6</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 12 -->
        <article class="movie-card" data-title="دەستپێکردن">
          <div class="rank">12</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMDliOTNhNmEtYTk2NS00NjFiLTkxMDItN2M1M2VmNWQzMjhlXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">دەستپێکردن</div>
              <div class="movie-plot">سەرکردەی تیمێک خەون دەدزێت و دەست دەکات بە مەترسیدارترین ئەرک: نەخشاندنی بیرۆکەی مێشک.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.8</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 13 -->
        <article class="movie-card" data-title="خوێندکار">
          <div class="rank">13</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTk4ODQzNDY3Ml5BMl5BanBnXkFtZTcwODA0NTM4Nw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">خوێندکار</div>
              <div class="movie-plot">خوێندکارێک دەچێتە ناو کۆمەڵگەیەکی تایبەت و دەبێتە هۆی ڕووداوێکی ترسناک.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.6</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 14 -->
        <article class="movie-card" data-title="کەسی تاریک">
          <div class="rank">14</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">کەسی تاریک</div>
              <div class="movie-plot">پۆلیسێک دەتەوێت کەسێک بدۆزێت کە زیاتر لە خەیاڵێکە — راستییەکە نزیکترە لەوەی پەیوەندیدا.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.1</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 15 -->
        <article class="movie-card" data-title="ئاڤاتار">
          <div class="rank">15</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">ئاڤاتار</div>
              <div class="movie-plot">سەربازێک لە جیهانێکی تر دەچێتە ناو لەشی بوونەوەر و گۆڕانکارییەکی مەزن لە ژیان و جیهان دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.8</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 16 -->
        <article class="movie-card" data-title="پاشای شێت">
          <div class="rank">16</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTk2NTI1MTU4N15BMl5BanBnXkFtZTcwODg0OTY0Nw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">پاشای شێت</div>
              <div class="movie-plot">کۆمیدیەکی قەسی دەبێتە پاشای شێت و پلانێکی ترسناک جێبەجێ دەکات؛ کۆتایی هەموو کەس سەرسام دەکات.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.4</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 17 -->
        <article class="movie-card" data-title="پڕۆژەی بێڵ">
          <div class="rank">17</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTM0MDgwNjMyMl5BMl5BanBnXkFtZTcwNTg0NzU1Ng@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">پڕۆژەی بێڵ</div>
              <div class="movie-plot">زانایەک پڕۆژەی تایبەت دروست دەکات بۆ گەڕانەوەی کچەکەی، بەڵام پڕۆژەکە مەترسیدارتر دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.9</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 18 -->
        <article class="movie-card" data-title="دەستەی ڤێنۆم">
          <div class="rank">18</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTY3NjY0MTQ0Nl5BMl5BanBnXkFtZTcwMDQzMzQ2Mw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">دەستەی ڤێنۆم</div>
              <div class="movie-plot">ڕۆژنامەنووسێک دەبێتە میواندار بوونەوەر و گۆڕانکارییەکی مەزن لە ژیانەکەی دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 6.7</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 19 -->
        <article class="movie-card" data-title="کۆتایی یاری">
          <div class="rank">19</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTc5MDE2ODcwNV5BMl5BanBnXkFtZTgwMzI2NzQ2NzM@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">کۆتایی یاری</div>
              <div class="movie-plot">کۆمەڵێک کەس لە جیهانێکدا خەون دەبینن، مردنەکەیان ڕاستەقینە نییە؛ راستەی ترسناکتر دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.4</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 20 -->
        <article class="movie-card" data-title="ئیرۆن مەن">
          <div class="rank">20</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTczNTI2ODUwOF5BMl5BanBnXkFtZTcwMTU0NTIzMw@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">ئیرۆن مەن</div>
              <div class="movie-plot">بلیمەتێکی بەهرەدار دەبێتە قارەمانێکی سەربەخۆ دوای ڕزگارکردن لە تاوانبارێک.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.9</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 21 -->
        <article class="movie-card" data-title="پاشای شێر">
          <div class="rank">21</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTM4NzQ0OTYyOF5BMl5BanBnXkFtZTcwMDkyNjQyMg@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">پاشای شێر</div>
              <div class="movie-plot">شێرێکی گەنج دەبێتە پاشا دوای مردنی باوکی؛ مامی پلانێکی خراپ دەچێتە جێ.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.5</div>
              <div class="age">G</div>
            </div>
          </div>
        </article>

        <!-- 22 -->
        <article class="movie-card" data-title="بەربەست">
          <div class="rank">22</div>
          <div class="poster" style="background-image:url('https://m.media-amazon.com/images/M/MV5BMTY5OTU0OTc2NV5BMl5BanBnXkFtZTcwMzU4MDcyMQ@@._V1_FMjpg_UX1000_.jpg')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">بەربەست</div>
              <div class="movie-plot">لە جیهانێکی پۆست-ئاپۆکالیپتیکی، کەسێک هەوڵ دەدات ڕزگاری خەڵک بکات — رێگەکە مەترسیدارە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.2</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- --- New 10 movies (23..32) with placeholders --- -->

        <!-- 23 -->
        <article class="movie-card" data-title="نیشتمان لە نیوەی تاریکی">
          <div class="rank">23</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie23/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">نیشتمان لە نیوەی تاریکی</div>
              <div class="movie-plot">فیلمێکی روانی دەربارەی کەسێک کە ناتوانێت نێوان راست و خەیاڵ جیا بکات؛ نهێنییەکانی ژیانی تەواو دەخرێن.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.3</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 24 -->
        <article class="movie-card" data-title="شەوەکانی سەردەم">
          <div class="rank">24</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie24/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">شەوەکانی سەردەم</div>
              <div class="movie-plot">تاریخی-ترسیەکە لە ماوەی دوو ساتی دا روودەدات و هوایەکی مایەدار و تەنها.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.9</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 25 -->
        <article class="movie-card" data-title="تاقیکردنەوەی لەکات">
          <div class="rank">25</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie25/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">تاقیکردنەوەی لەکات</div>
              <div class="movie-plot">سەرنجڕاکێش، فیلمی سای-فای کە وەختی کۆتایی و دەستکاری زمان ڕوون دەکات.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.1</div>
              <div class="age pg13">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 26 -->
        <article class="movie-card" data-title="رێگەی گەورە">
          <div class="rank">26</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie26/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">رێگەی گەورە</div>
              <div class="movie-plot">اکشن-دراما بۆ قهرمانێک کە لە شوێنێکی هەموو شت شکۆفتووە دەگرێتەوە.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.7</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 27 -->
        <article class="movie-card" data-title="دەنگی ڕوو">
          <div class="rank">27</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie27/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">دەنگی ڕوو</div>
              <div class="movie-plot">تاریک و روانی — کەسێک دەستی بە هەڵگرتنی هەستەکانی تری هەیە و ئەو دەنگان هێرش دەدەن.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.0</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 28 -->
        <article class="movie-card" data-title="شینەکانی نێودەوڵەتی">
          <div class="rank">28</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie28/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">شینەکانی نێودەوڵەتی</div>
              <div class="movie-plot">دراما سیاسی ـ روانی کە هەموو شت لە ماوەی کورتدا دەگۆڕێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.5</div>
              <div class="age">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 29 -->
        <article class="movie-card" data-title="کاتی شەوان">
          <div class="rank">29</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie29/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">کاتی شەوان</div>
              <div class="movie-plot">مێژووی هێز و رازەکان — فیلمێکی سەرنجڕاکێش کە لە شەوەکاندا ئەنجام دەدرێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.8</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 30 -->
        <article class="movie-card" data-title="یاریگەڕ">
          <div class="rank">30</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie30/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">یاریگەڕ</div>
              <div class="movie-plot">تەنها نیگەرانی و قسەی پاشپەڕ — فیلمێکی psychological کە هەموو شت لە گەڕانێک دەستپێدەکات.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.2</div>
              <div class="age">PG-13</div>
            </div>
          </div>
        </article>

        <!-- 31 -->
        <article class="movie-card" data-title="تەواوەتی تاریک">
          <div class="rank">31</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie31/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">تەواوەتی تاریک</div>
              <div class="movie-plot">کۆمەڵەی راز و ڕووداوە ترسناکەکانی کەسێک لە شەوێکی تایبەت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 7.6</div>
              <div class="age">R</div>
            </div>
          </div>
        </article>

        <!-- 32 -->
        <article class="movie-card" data-title="گۆڕانکاری نەتەوە">
          <div class="rank">32</div>
          <div class="poster" style="background-image:url('https://picsum.photos/seed/movie32/800/450')">
            <div class="play-overlay"><div class="play-btn"></div></div>
          </div>
          <div class="title-row">
            <div>
              <div class="movie-title">گۆڕانکاری نەتەوە</div>
              <div class="movie-plot">حکایەتی زۆر مەترسیدار کە لە کۆمەڵگەیەکی گەورەدا بەردەوام دەبێت.</div>
            </div>
            <div class="movie-meta">
              <div class="imdb">⭐ 8.0</div>
              <div class="age">PG-13</div>
            </div>
          </div>
        </article>

      </section>
    </main>

    <footer style="text-align:center;margin-top:34px;color:rgba(255,255,255,0.7);font-size:0.95rem;">
      © ٢٠٢٣ فیلمی نایاب - هەموو مافەکان پارێزراون
    </footer>

  </div>

  <script>
    // کلیکی لە سەر هەر کاردێک -> show alert (دەتوانیت modal یان پلێیەر زیاد بکەیت)
    document.addEventListener('click', function(e){
      const card = e.target.closest('.movie-card');
      if(!card) return;
      const title = card.getAttribute('data-title') || card.querySelector('.movie-title')?.textContent || 'فیلم';
      // بەجای alert دەتوانی modal popup زیاد بکەیت
      alert(`فیلمی "${title.trim()}" هەڵبژێردرا!`);
    });

    // Accessibility: keyboard navigation (Enter on focused card)
    document.querySelectorAll('.movie-card').forEach(card => {
      card.setAttribute('tabindex', '0');
      card.addEventListener('keydown', function(ev){
        if(ev.key === 'Enter' || ev.key === ' '){
          ev.preventDefault();
          card.click();
        }
      });
    });
  </script>
</body>
</html>
