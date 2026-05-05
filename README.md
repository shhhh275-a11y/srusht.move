<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        /* هەموو ستایلەکانی ناو فایلەکەت بەبێ گۆڕانکاری */
        :root {
            --bg: #0a0a0a; --bg2: #141414; --card: #1a1a1a;
            --accent: #e50914; --accent2: #ff6b35; --gold: #f5c518;
            --text: #fff; --text2: #999; --border: rgba(255,255,255,0.08);
        }
        body.light {
            --bg: #f5f5f7; --bg2: #fff; --card: #fff;
            --text: #1d1d1f; --text2: #6e6e73; --border: rgba(0,0,0,0.05);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body { font-family: 'Cairo', sans-serif; background: var(--bg); color: var(--text); transition: 0.3s; }
        header { background: var(--bg2); padding: 15px 5%; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 10px rgba(0,0,0,0.3); }
        .logo { font-family: 'Bebas Neue'; font-size: 2.2rem; color: var(--accent); letter-spacing: 1px; }
        .search-box { display: flex; background: rgba(255,255,255,0.1); padding: 8px 15px; border-radius: 30px; width: 40%; border: 1px solid var(--border); }
        .search-box input { background: none; border: none; color: var(--text); outline: none; width: 100%; font-family: 'Cairo'; }
        #movieGrid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 25px; padding: 40px 5%; }
        .movie-card { background: var(--card); border-radius: 15px; overflow: hidden; transition: 0.4s; border: 1px solid var(--border); cursor: pointer; }
        .movie-card:hover { transform: translateY(-10px); box-shadow: 0 10px 20px rgba(0,0,0,0.5); }
        .movie-img img { width: 100%; height: 300px; object-fit: cover; }
        .movie-info { padding: 15px; }
        .movie-info h3 { font-size: 1.1rem; margin-bottom: 10px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        .meta { display: flex; justify-content: space-between; align-items: center; font-size: 0.9rem; color: var(--text2); }
        .rating { color: var(--gold); font-weight: bold; }
        .btn-container { text-align: center; padding: 40px; }
        #loadMore { background: var(--accent); color: white; border: none; padding: 12px 40px; border-radius: 30px; font-family: 'Cairo'; font-weight: 700; cursor: pointer; transition: 0.3s; }
        #loadMore:hover { transform: scale(1.05); background: #b20710; }
    </style>
</head>
<body class="dark">

<header id="navbar">
    <div class="logo">SRUSHT MOVIES</div>
    <div class="search-box">
        <input type="text" id="searchInput" placeholder="بگەڕێ بۆ فیلم یان زنجیرە...">
        <i class="fas fa-search" style="cursor:pointer; color:var(--text2)" onclick="doSearch()"></i>
    </div>
    <div id="modeBtn" style="cursor:pointer; padding: 10px; background: var(--card); border-radius: 50%;">
        <i class="fas fa-moon"></i>
    </div>
</header>

<div id="movieGrid"></div>

<div class="btn-container">
    <button id="loadMore">بینینی زیاتر</button>
</div>

<script>
    // ===== API CONFIG =====
    const API_KEY = 'Df3194b0b76a3ac936ceb1b11c3e63d3'; // کلیلەکەی تۆ
    const BASE_URL = 'https://api.themoviedb.org/3';
    const IMG_PATH = 'https://image.tmdb.org/t/p/w500';

    let page = 1;
    let currentSearch = '';

    // هێنانی داتا بەبێ تێکدانی دیزاین
    async function loadMovies(url, clear = false) {
        try {
            const res = await fetch(url);
            const data = await res.json();
            if (clear) document.getElementById('movieGrid').innerHTML = '';
            
            data.results.forEach(movie => {
                const card = document.createElement('div');
                card.className = 'movie-card';
                card.innerHTML = `
                    <div class="movie-img">
                        <img src="${movie.poster_path ? IMG_PATH + movie.poster_path : 'https://via.placeholder.com/500x750'}" alt="${movie.title}">
                    </div>
                    <div class="movie-info">
                        <h3>${movie.title}</h3>
                        <div class="meta">
                            <span class="rating"><i class="fas fa-star"></i> ${movie.vote_average.toFixed(1)}</span>
                            <span>${movie.release_date ? movie.release_date.split('-')[0] : 'N/A'}</span>
                        </div>
                    </div>
                `;
                document.getElementById('movieGrid').appendChild(card);
            });
        } catch (e) { console.log("هەڵە هەیە لە کلیلەکە یان پەیوەندییەکە"); }
    }

    function doSearch() {
        const q = document.getElementById('searchInput').value;
        if(q) {
            currentSearch = q; page = 1;
            loadMovies(`${BASE_URL}/search/movie?api_key=${API_KEY}&query=${q}&page=1`, true);
        }
    }

    // لۆدکردنی سەرەتایی
    loadMovies(`${BASE_URL}/discover/movie?sort_by=popularity.desc&api_key=${API_KEY}&page=1`);

    // دوگمەی بینینی زیاتر
    document.getElementById('loadMore').onclick = () => {
        page++;
        const url = currentSearch 
            ? `${BASE_URL}/search/movie?api_key=${API_KEY}&query=${currentSearch}&page=${page}`
            : `${BASE_URL}/discover/movie?sort_by=popularity.desc&api_key=${API_KEY}&page=${page}`;
        loadMovies(url);
    };

    // مۆدی شەو و ڕۆژ وەک کۆدە کۆنەکەت
    const modeBtn = document.getElementById('modeBtn');
    modeBtn.onclick = () => {
        document.body.classList.toggle('light');
        const isLight = document.body.classList.contains('light');
        modeBtn.innerHTML = isLight ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
    };

    document.getElementById('searchInput').onkeypress = (e) => { if(e.key === 'Enter') doSearch(); };
</script>

</body>
</html>
