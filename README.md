<!DOCTYPE html>

<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فیلمەکانی کۆتایی شۆککەر</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

```
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
        background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.6)), #2c1810;
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
        background: radial-gradient(circle, #c77b63, #8b5a4a);
        opacity: 0.3;
        filter: blur(80px);
        z-index: -1;
        animation: float 20s ease-in-out infinite;
    }
    
    @keyframes float {
        0%, 100% { transform: translate(-50%, -50%) scale(1); }
        50% { transform: translate(-50%, -48%) scale(1.1); }
    }
    
    .container { max-width: 1200px; margin: 0 auto; padding: 20px; position: relative; z-index: 1; }
    
    h1 {
        text-align: center;
        color: white;
        margin-bottom: 10px;
        font-size: 2.5em;
        text-shadow: 3px 3px 10px rgba(0,0,0,0.7);
        animation: fadeInDown 1s ease;
    }
    
    @keyframes fadeInDown {
        from { opacity: 0; transform: translateY(-30px); }
        to { opacity: 1; transform: translateY(0); }
    }
    
    .subtitle {
        text-align: center;
        color: rgba(255,255,255,0.95);
        margin-bottom: 40px;
        font-size: 1.2em;
        text-shadow: 2px 2px 8px rgba(0,0,0,0.5);
        animation: fadeIn 1.5s ease;
    }
    
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

    .home-section { display: block; }
    .home-section.hidden { display: none; }
    
    .category-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
        gap: 30px;
        padding: 20px 0;
        margin-bottom: 60px;
    }
    
    .category-card {
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        border-radius: 20px;
        padding: 40px;
        box-shadow: 0 8px 32px rgba(0,0,0,0.3);
        border: 2px solid rgba(255, 255, 255, 0.18);
        transition: all 0.4s;
        cursor: pointer;
        animation: fadeInUp 0.6s ease backwards;
        text-align: center;
    }
    
    .category-card:nth-child(1) { animation-delay: 0.1s; }
    .category-card:nth-child(2) { animation-delay: 0.2s; }
    .category-card:nth-child(3) { animation-delay: 0.3s; }
    .category-card:nth-child(4) { animation-delay: 0.4s; }
    .category-card:nth-child(5) { animation-delay: 0.5s; }
    .category-card:nth-child(6) { animation-delay: 0.6s; }
    
    @keyframes fadeInUp {
        from { opacity: 0; transform: translateY(30px); }
        to { opacity: 1; transform: translateY(0); }
    }
    
    .category-card:hover {
        transform: translateY(-15px) scale(1.02);
        box-shadow: 0 20px 60px rgba(0,0,0,0.5);
        background: rgba(255, 255, 255, 0.15);
    }

    .category-icon { font-size: 4em; margin-bottom: 20px; }
    .category-title { font-size: 1.8em; color: white; margin-bottom: 10px; font-weight: bold; }
    .category-subtitle { font-size: 1.1em; color: rgba(255,255,255,0.7); }

    .movie-section { display: none; animation: fadeIn 0.5s ease; }
    .movie-section.active { display: block; }

    .back-button {
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        border: 2px solid rgba(255,255,255,0.3);
        color: white;
        padding: 15px 35px;
        border-radius: 50px;
        font-size: 1.1em;
        cursor: pointer;
        transition: all 0.3s;
        margin-bottom: 30px;
    }

    .back-button:hover {
        background: rgba(255, 255, 255, 0.2);
        transform: translateX(10px);
        box-shadow: 0 5px 15px rgba(0,0,0,0.3);
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
        transition: all 0.4s;
        animation: fadeInUp 0.6s ease backwards;
    }
    
    .movie-card:hover {
        transform: translateY(-10px) scale(1.02);
        box-shadow: 0 15px 50px rgba(0,0,0,0.5);
        background: rgba(255, 255, 255, 0.15);
    }

    .movie-poster {
        width: 100%;
        height: 200px;
        background: linear-gradient(135deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 3em;
    }

    .movie-content { padding: 20px; }
    .movie-title { font-size: 1.4em; color: white; margin-bottom: 8px; font-weight: bold; }
    .movie-year { color: rgba(255,255,255,0.6); font-size: 0.95em; margin-bottom: 12px; }
    .movie-description { color: rgba(255,255,255,0.85); line-height: 1.6; font-size: 0.95em; }

    .footer { margin-top: 80px; padding: 50px 20px 30px; border-top: 1px solid rgba(255,255,255,0.1); }

    .social-links {
        display: flex;
        justify-content: center;
        gap: 30px;
        margin-bottom: 30px;
        flex-wrap: wrap;
    }

    .social-card {
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        padding: 25px 35px;
        border-radius: 15px;
        border: 2px solid rgba(255,255,255,0.2);
        transition: all 0.3s;
        text-decoration: none;
        text-align: center;
    }

    .social-card:hover {
        transform: translateY(-5px);
        background: rgba(255, 255, 255, 0.15);
        box-shadow: 0 10px 25px rgba(0,0,0,0.3);
    }

    .social-icon { font-size: 2.5em; margin-bottom: 10px; }
    .social-name { color: white; font-size: 1.2em; font-weight: bold; margin-bottom: 5px; }
    .social-username { color: rgba(255,255,255,0.7); font-size: 1em; }
    .copyright { text-align: center; color: rgba(255,255,255,0.5); font-size: 0.9em; margin-top: 20px; }
    
    @media (max-width: 768px) {
        h1 { font-size: 2em; }
        .category-grid, .movie-grid { grid-template-columns: 1fr; }
    }
</style>
```

</head>
<body>
    <div class="background-image"></div>

```
<div class="container">
    <div id="home" class="home-section">
        <h1>فیلمەکانی کۆتایی شۆککەر</h1>
        <p class="subtitle">باشترین فیلمەکان کە کۆتاییەکەیان سەرسوڕمانت دەکات</p>
        
        <div class="category-grid">
            <div class="category-card" onclick="showSection('twist')">
                <div class="category-icon">🧩</div>
                <h2 class="category-title">فیلمی ئاڵۆز</h2>
                <p class="category-subtitle">Twist Endings</p>
            </div>
            <div class="category-card" onclick="showSection('drama')">
                <div class="category-icon">🎭</div>
                <h2 class="category-title">فیلمی دراما</h2>
                <p class="category-subtitle">Drama</p>
            </div>
            <div class="category-card" onclick="showSection('comedy')">
                <div class="category-icon">😂</div>
                <h2 class="category-title">فیلمی کۆمیدی</h2>
                <p class="category-subtitle">Comedy</p>
            </div>
            <div class="category-card" onclick="showSection('action')">
                <div class="category-icon">💥</div>
                <h2 class="category-title">فیلمی ئاکشن</h2>
                <p class="category-subtitle">Action</p>
            </div>
            <div class="category-card" onclick="showSection('horror')">
                <div class="category-icon">👻</div>
                <h2 class="category-title">فیلمی ترسناک</h2>
                <p class="category-subtitle">Horror</p>
            </div>
            <div class="category-card" onclick="showSection('scifi')">
                <div class="category-icon">🚀</div>
                <h2 class="category-title">زانستی خەیاڵی</h2>
                <p class="category-subtitle">Sci-Fi</p>
            </div>
        </div>
    </div>

    <div id="twist-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>🧩 فیلمی ئاڵۆز</h1>
        <p class="subtitle">فیلمەکان کە کۆتاییەکەیان هەموو شتێک دەگۆڕێت</p>
        <div class="movie-grid" id="twist-movies"></div>
    </div>

    <div id="drama-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>🎭 فیلمی دراما</h1>
        <p class="subtitle">فیلمە سۆزدارەکان</p>
        <div class="movie-grid" id="drama-movies"></div>
    </div>

    <div id="comedy-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>😂 فیلمی کۆمیدی</h1>
        <p class="subtitle">پێکەنین لەگەڵ کۆتاییەکی نەچاوەڕوان</p>
        <div class="movie-grid" id="comedy-movies"></div>
    </div>

    <div id="action-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>💥 فیلمی ئاکشن</h1>
        <p class="subtitle">هەڵچوون و کۆتاییەکی شۆککەر</p>
        <div class="movie-grid" id="action-movies"></div>
    </div>

    <div id="horror-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>👻 فیلمی ترسناک</h1>
        <p class="subtitle">ترس و کۆتاییەکی بیرت ناچێتەوە</p>
        <div class="movie-grid" id="horror-movies"></div>
    </div>

    <div id="scifi-section" class="movie-section">
        <button class="back-button" onclick="showHome()">← گەڕانەوە</button>
        <h1>🚀 زانستی خەیاڵی</h1>
        <p class="subtitle">داهێنان و کۆتاییەکی مێشک دەسووتێنێت</p>
        <div class="movie-grid" id="scifi-movies"></div>
    </div>
</div>

<footer class="footer">
    <div class="social-links">
        <a href="https://instagram.com/ml.2050ll" target="_blank" class="social-card">
            <div class="social-icon">📸</div>
            <div class="social-name">Muhamed Hamid</div>
            <div class="social-username">@ml.2050ll</div>
        </a>
        <a href="https://instagram.com/9fi.99" target="_blank" class="social-card">
            <div class="social-icon">📸</div>
            <div class="social-name">Srusht</div>
            <div class="social-username">@9fi.99</div>
        </a>
    </div>
    <p class="copyright">© 2025 فیلمەکانی کۆتایی شۆککەر</p>
</footer>

<script>
    const movies = {
        twist: [
            {t:"The Sixth Sense",y:"1999",i:"👁️",d:"کورێک دەتوانێت مردووەکان ببینێت. کۆتاییەکی شۆککەر"},
            {t:"Fight Club",y:"1999",i:"🥊",d:"کۆمەڵگەیەکی شەڕ. کۆتایی هەموو شتێک دەگۆڕێت"},
            {t:"The Usual Suspects",y:"1995",i:"🕵️",d:"پێنج تاوانبار. کێ کەیزەر سۆزەیە؟"},
            {t:"Shutter Island",y:"2010",i:"🏝️",d:"وێستگەی دەروونی لەسەر دوورگە. هیچ وەک دیارە نییە"},
            {t:"Gone Girl",y:"2014",i:"💔",d:"ژنێک ون دەبێت. بەڵام ڕاستی چییە؟"},
            {t:"The Prestige",y:"2006",i:"🎩",d:"دوو شانۆگەری سیحر لە ڕکابەری"},
            {t:"Memento",y:"2000",i:"🧠",d:"بە کورتخایەنی بیرەوەری. فیلم بە پێچەوانە"},
            {t:"The Others",y:"2001",i:"🕯️",d:"دایک و منداڵان لە ماڵێکی تاریک"},
            {t:"Oldboy",y:"2003",i:"🔨",d:"15 ساڵ زیندانی بێ هۆ. بۆچی؟"},
            {t:"Arrival",y:"2016",i:"🛸",d:"بیانییەکان هاتوون. زمانزان ڕاستی دەدۆزێتەوە"}
        ],
        drama: [
            {t:"Shawshank Redemption",y:"1994",i:"⛓️",d:"هیوا و ئازادی لەناو زیندان"},
            {t:"Schindler's List",y:"1993",i:"🕎",d:"ڕزگارکردنی هەزاران جولەکە لە جەنگ"},
            {t:"Forrest Gump",y:"1994",i:"🏃",d:"ژیانی پیاوێکی سادە لە ڕووداوە گەورەکان"},
            {t:"The Green Mile",y:"1999",i:"⚡",d:"لە زیندان، پیاوێکی تایبەت"},
            {t:"A Beautiful Mind",y:"2001",i:"🧮",d:"زانای بریار دژی نەخۆشی دەروونی"},
            {t:"Good Will Hunting",y:"1997",i:"📐",d:"گەنجێکی ئاسایی بە مێشکێکی نائاسایی"},
            {t:"The Pianist",y:"2002",i:"🎹",d:"پیانۆژەن لە جەنگی جیهانی دووەم"},
            {t:"12 Years a Slave",y:"2013",i:"⛓️",d:"پیاوێکی ئازاد وەک کۆیلە دەفرۆشرێت"},
            {t:"Manchester by the Sea",y:"2016",i:"🌊",d:"گەڕانەوە دوای تراژیدیا"},
            {t:"Room",y:"2015",i:"🚪",d:"دایک و کوڕ زیندانی لە ژوورێک"}
        ],
        comedy: [
            {t:"Grand Budapest Hotel",y:"2014",i:"🏨",d:"کۆنسێرج و سەرپەرشتیار لە هۆتێل"},
            {t:"Parasite",y:"2019",i:"🪜",d:"خێزانی هەژار و خێزانی دەوڵەمەند"},
            {t:"Little Miss Sunshine",y:"2006",i:"🚐",d:"خێزان بۆ پێشبڕکێی کچەکەیان"},
            {t:"Life is Beautiful",y:"1997",i:"🎭",d:"باوک لە کامپی جولەکە وا دەکات یارییە"},
            {t:"Jojo Rabbit",y:"2019",i:"🐰",d:"کوڕ لە جەنگ بە هاوڕێیەکی خەیاڵی: هیتلەر"},
            {t:"The Truman Show",y:"1998",i:"📺",d:"هەموو ژیان شۆی تەلەڤیزیۆنی بووە"},
            {t:"Moonrise Kingdom",y:"2012",i:"⛺",d:"دوو منداڵ هەڵدێن بۆ دوورگە"},
            {t:"Hunt for Wilderpeople",y:"2016",i:"🌲",d:"کوڕ و پیرەپیاو لە دارستان"},
            {t:"About Time",y:"2013",i:"⏰",d:"گەڕانەوە بۆ رابردوو. وانەیەکی گەورە"},
            {t:"Amélie",y:"2001",i:"🎨",d:"کچی خەونبینەر لە پاریس"}
        ],
        action: [
            {t:"Inception",y:"2010",i:"🌀",d:"دزی بیر لە خەوەکان"},
            {t:"The Departed",y:"2006",i:"🚔",d:"پۆلیس و مافیا. سیخوڕەکان"},
            {t:"No Country for Old Men",y:"2007",i:"💰",d:"پارە و کوشندەیەکی بێبەزەیی"},
            {t:"The Town",y:"2010",i:"🏦",d:"دزی بانک دەیەوێت وازبهێنێت"},
            {t:"Blood Diamond",y:"2006",i:"💎",d:"جەنگی ئەهلی و ئەڵماس"},
            {t:"Mad Max: Fury Road",y:"2015",i:"🚗",d:"دنیای پۆست-ئەپۆکالیپتیک و ئازادی"},
            {t:"The Raid",y:"2011",i:"🥋",d:"تیمی تایبەت لە بینای تاوانکاران"},
            {t:"Logan",y:"2017",i:"🦾",d:"وولڤەرین لە کۆتایی ژیان"},
            {t:"The Dark Knight",y:"2008",i:"🦇",d:"باتمان دژی جۆکەر"},
            {t:"Skyfall",y:"2012",i:"🔫",d:"جەیمس بۆند و رابردووی"}
        ],
        horror: [
            {t:"The Sixth Sense",y:"1999",i:"👻",d:"کۆتاییەکی گەورەترین تویست"},
            {t:"The Others",y:"2001",i:"🏚️",d:"دایک و منداڵ. کێ مردووەکانن؟"},
            {t:"Get Out",y:"2017",i:"🎭",d:"چاوپێکەوتنی خێزان. نهێنییەک هەیە"},
            {t:"The Orphanage",y:"2007",i:"👶",d:"گەڕانەوە بۆ ماڵی منداڵی"},
            {t:"The Mist",y:"2007",i:"🌫️",d:"گیر لە دوکان بەهۆی میست"},
            {t:"Cabin in the Woods",y:"2012",i:"🏕️",d:"کەپری نائاسایی"},
            {t:"Hereditary",y:"2018",i:"👪",d:"نهێنیە ترسناکەکانی خێزان"},
            {t:"The Wailing",y:"2016",i:"😱",d:"گوندی کۆریا و کوشتنە سەیرەکان"},
            {t:"Orphan",y:"2009",i:"👧",d:"منداڵێکی هەتیو. بەڵام چی نهێنییەکی هەیە؟"},
            {t:"The Witch",y:"2015",i:"🕯️",d:"خێزان لە 1600 و جادووگەری"}
        ],
        scifi: [
            {t:"Interstellar",y:"2014",i:"🌌",d:"گەشت بۆ دۆزینەوەی ماڵێکی نوێ بۆ مرۆڤ"},
            {t:"The Matrix",y:"1999",i:"💊",d:"دنیای ڕاستەقینە چییە؟ کۆتاییەکی شۆککەر"},
            {t:"Blade Runner 2049",y:"2017",i:"🤖",d:"لە داهاتوو، کێ مرۆڤە و کێ ڕۆبۆتە؟"},
            {t:"Ex Machina",y:"2014",i:"🤖",d:"تاقیکردنەوەی مێشکی دەستکرد"},
            {t:"Arrival",y:"2016",i:"🛸",d:"پەیوەندی لەگەڵ بیانییەکان"},
            {t:"The Prestige",y:"2006",i:"⚡",d:"سیحر یان زانست؟"},
            {t:"Looper",y:"2012",i:"🔄",d:"کوشندە لە داهاتوو خۆی لە رابردوو دەکوژێت"},
            {t:"Source Code",y:"2011",i:"⏱️",d:"دووبارە ژیان بۆ ڕزگارکردنی خەڵک"},
            {t:"Moon",y:"2009",i:"🌙",d:"تەنها لەسەر مانگ. بەڵام ڕاستی چییە؟"},
            {t:"Coherence",y:"2013",i:"🌠",d:"شەوێکی ئاسایی دەبێتە شتێکی سەیر"}
        ]
    };

    function showSection(cat) {
        document.getElementById('home').classList.add('hidden');
        const sec = document.getElementById(cat + '-section');
        sec.classList.add('active');
        const grid = document.getElementById(cat + '-movies');
        grid.innerHTML = movies[cat].map((m,idx) => `
            <div class="movie-card" style="animation-delay: ${idx*0.1}s">
                <div class="movie-poster">${m.i}</div>
                <div class="movie-content">
                    <div class="movie-title">${m.t}</div>
                    <div class="movie-year">${m.y}</div>
                    <div class="movie-description">${m.d}</div>
                </div>
            </div>
        `).join('');
        window.scrollTo({top:0,behavior:'smooth'});
    }

    function showHome() {
        document.querySelectorAll('.movie-section').forEach(s => s.classList.remove('active'));
        document.getElementById('home').classList.remove('hidden');
        window.scrollTo({top:0,behavior:'smooth'});
    }
</script>
```

</body>
</html>
