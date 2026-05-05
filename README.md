<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies - Live</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #0a0a0a;
            --bg2: #141414;
            --card: #1a1a1a;
            --accent: #e50914;
            --gold: #f5c518;
            --text: #ffffff;
            --text2: #b3b3b3;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Cairo', sans-serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.6;
        }

        /* Navbar */
        header {
            background: var(--bg2);
            padding: 1rem 5%;
            position: sticky;
            top: 0;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo { font-size: 1.5rem; font-weight: 700; color: var(--accent); }

        .search-box {
            display: flex;
            gap: 10px;
            background: #222;
            padding: 5px 15px;
            border-radius: 25px;
            width: 40%;
        }

        .search-box input {
            background: none;
            border: none;
            color: white;
            outline: none;
            width: 100%;
            font-family: 'Cairo';
        }

        .search-box i { color: var(--text2); align-self: center; cursor: pointer; }

        /* Grid */
        #movieGrid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 25px;
            padding: 30px 5%;
        }

        .movie-card {
            background: var(--card);
            border-radius: 12px;
            overflow: hidden;
            transition: 0.3s;
            cursor: pointer;
            position: relative;
        }

        .movie-card:hover { transform: translateY(-10px); }

        .movie-img { position: relative; aspect-ratio: 2/3; }
        .movie-img img { width: 100%; height: 100%; object-fit: cover; }

        .rating-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(0,0,0,0.8);
            color: var(--gold);
            padding: 2px 8px;
            border-radius: 5px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .movie-info { padding: 12px; }
        .movie-info h3 { font-size: 0.95rem; margin-bottom: 5px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        .movie-info span { color: var(--text2); font-size: 0.85rem; }

        /* Load More */
        .controls { text-align: center; padding: 40px; }
        #loadMore {
            background: var(--accent);
            color: white;
            border: none;
            padding: 10px 35px;
            border-radius: 25px;
            font-family: 'Cairo';
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }
        #loadMore:hover { opacity: 0.8; }

        /* Responsive */
        @media (max-width: 768px) {
            .search-box { width: 60%; }
            #movieGrid { grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); }
        }
    </style>
</head>
<body>

<header>
    <div class="logo">SRUSHT MOVIES</div>
    <div class="search-box">
        <input type="text" id="searchInput" placeholder="بگەڕێ بۆ فیلم...">
        <i class="fas fa-search" onclick="handleSearch()"></i>
    </div>
</header>

<main id="movieGrid">
    </main>

<div class="controls">
    <button id="loadMore">بینینی زیاتر</button>
</div>

<script>
    // تنظیمات سەرەکی
    const API_KEY = 'Df3194b0b76a3ac936ceb1b11c3e63d3';
    const BASE_URL = 'https://api.themoviedb.org/3';
    const IMG_URL = 'https://image.tmdb.org/t/p/w500';

    let page = 1;
    let isSearching = false;
    let query = '';

    // فەنکشن بۆ هێنانی داتا
    async function fetchMovies(url, append = false) {
        try {
            const response = await fetch(url);
            const data = await response.json();
            displayMovies(data.results, append);
        } catch (error) {
            console.error("هەڵە ڕوویدا:", error);
        }
    }

    // پیشاندانی فیلمەکان
    function displayMovies(movies, append) {
        const grid = document.getElementById('movieGrid');
        if (!append) grid.innerHTML = '';

        movies.forEach(movie => {
            const movieDiv = document.createElement('div');
            movieDiv.className = 'movie-card';
            
            const poster = movie.poster_path ? IMG_URL + movie.poster_path : 'https://via.placeholder.com/500x750?text=No+Image';
            const year = movie.release_date ? movie.release_date.split('-')[0] : 'نادیار';

            movieDiv.innerHTML = `
                <div class="movie-img">
                    <img src="${poster}" alt="${movie.title}">
                    <div class="rating-badge"><i class="fas fa-star"></i> ${movie.vote_average.toFixed(1)}</div>
                </div>
                <div class="movie-info">
                    <h3>${movie.title}</h3>
                    <span>${year}</span>
                </div>
            `;
            grid.appendChild(movieDiv);
        });
    }

    // کرداری گەڕان
    function handleSearch() {
        const input = document.getElementById('searchInput').value;
        if (input.trim() !== "") {
            query = input;
            isSearching = true;
            page = 1;
            fetchMovies(`${BASE_URL}/search/movie?api_key=${API_KEY}&query=${query}&page=1`);
        } else {
            isSearching = false;
            page = 1;
            loadInitialMovies();
        }
    }

    // لۆدکردنی سەرەتایی
    function loadInitialMovies() {
        fetchMovies(`${BASE_URL}/discover/movie?sort_by=popularity.desc&api_key=${API_KEY}&page=1`);
    }

    // دوگمەی Load More
    document.getElementById('loadMore').addEventListener('click', () => {
        page++;
        const url = isSearching 
            ? `${BASE_URL}/search/movie?api_key=${API_KEY}&query=${query}&page=${page}`
            : `${BASE_URL}/discover/movie?sort_by=popularity.desc&api_key=${API_KEY}&page=${page}`;
        fetchMovies(url, true);
    });

    // گەڕان بە Enter
    document.getElementById('searchInput').addEventListener('keypress', (e) => {
        if (e.key === 'Enter') handleSearch();
    });

    // دەستپێکردن
    loadInitialMovies();
</script>

</body>
</html>
