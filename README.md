<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shocking Ending Movies</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* ===== پۆشەکی سەرەکی ===== */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
            background: #0f172a; /* Dark Mode Default */
            color: #f1f5f9;
            transition: background 0.4s ease, color 0.4s ease;
            line-height: 1.6;
        }
        body.light-mode {
            background: #f8fafc;
            color: #1e293b;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* ===== مۆدی شەو/ڕۆژ (لای چەپی سەرەوە) ===== */
        .mode-toggle {
            position: fixed;
            top: 15px;
            left: 15px;
            z-index: 1000;
        }
        .mode-btn {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: #f1f5f9;
            border-radius: 24px;
            padding: 10px 18px;
            cursor: pointer;
            font-size: 0.95rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        }
        .mode-btn:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateY(-2px);
        }
        .light-mode .mode-btn {
            background: rgba(30, 41, 59, 0.1);
            border-color: rgba(30, 41, 59, 0.2);
            color: #1e293b;
        }
        .light-mode .mode-btn:hover {
            background: rgba(30, 41, 59, 0.2);
        }

        /* ===== سەردێڕ ===== */
        .header {
            text-align: center;
            margin: 30px 0 40px;
            padding-top: 20px;
        }
        .brand-name {
            font-size: 3.2rem;
            font-weight: 900;
            margin-bottom: 10px;
            background: linear-gradient(90deg, #f59e0b, #ef4444, #8b5cf6);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
        }
        .header p {
            font-size: 1.1rem;
            color: #94a3b8;
            max-width: 600px;
            margin: 0 auto;
        }
        .light-mode .header p {
            color: #64748b;
        }

        /* ===== گەڕان ===== */
        .search-section {
            max-width: 700px;
            margin: 0 auto 50px;
        }
        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 60px;
            padding: 6px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }
        .light-mode .search-box {
            background: rgba(30, 41, 59, 0.08);
            border-color: rgba(30, 41, 59, 0.1);
        }
        .search-box:focus-within {
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3);
            border-color: rgba(139, 92, 246, 0.4);
        }
        .search-input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 18px 25px;
            color: inherit;
            font-size: 1.05rem;
            outline: none;
        }
        .search-input::placeholder {
            color: #94a3b8;
        }
        .light-mode .search-input::placeholder {
            color: #94a3b8;
        }
        .search-button {
            background: linear-gradient(90deg, #8b5cf6, #ec4899);
            border: none;
            border-radius: 50px;
            padding: 18px 35px;
            color: white;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(139, 92, 246, 0.4);
        }
        .search-button:hover {
            transform: scale(1.03);
            box-shadow: 0 6px 20px rgba(139, 92, 246, 0.6);
        }

        /* ===== لیستی فیلمەکان (ئێستا لە سەرەوەیە) ===== */
        .movies-header {
            text-align: center;
            margin-bottom: 40px;
        }
        .movies-header h2 {
            font-size: 2.2rem;
            margin-bottom: 15px;
            color: #f1f5f9;
        }
        .light-mode .movies-header h2 {
            color: #1e293b;
        }
        .movies-header p {
            color: #94a3b8;
            font-size: 1.1rem;
        }
        .light-mode .movies-header p {
            color: #64748b;
        }

        /* ===== کارتی فیلم ===== */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }
        .movie-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        .light-mode .movie-card {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(30, 41, 59, 0.1);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
        }
        .movie-card:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.35);
            border-color: rgba(139, 92, 246, 0.3);
        }
        .movie-poster-container {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
        }
        .movie-poster {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s ease;
        }
        .movie-card:hover .movie-poster {
            transform: scale(1.08);
        }
        .movie-rank {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.8);
            color: #f59e0b;
            font-weight: 900;
            font-size: 1.4rem;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 3px solid #f59e0b;
        }
        .movie-info {
            padding: 25px;
        }
        .movie-title {
            font-size: 1.5rem;
            font-weight: 800;
            margin-bottom: 8px;
            color: #f1f5f9;
            line-height: 1.3;
        }
        .light-mode .movie-title {
            color: #1e293b;
        }
        .movie-year {
            color: #f59e0b;
            font-weight: 600;
            font-size: 1rem;
            margin-bottom: 15px;
            display: inline-block;
            background: rgba(245, 158, 11, 0.1);
            padding: 5px 12px;
            border-radius: 20px;
        }
        .movie-plot {
            color: #cbd5e1;
            font-size: 0.95rem;
            margin-bottom: 20px;
            line-height: 1.7;
        }
        .light-mode .movie-plot {
            color: #475569;
        }
        .movie-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .imdb-rating {
            background: linear-gradient(135deg, #f59e0b, #d97706);
            color: #1c1917;
            font-weight: 800;
            padding: 10px 18px;
            border-radius: 12px;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .age-rating {
            background: #3b82f6;
            color: white;
            font-weight: 700;
            padding: 10px 18px;
            border-radius: 12px;
            font-size: 0.9rem;
        }
        .age-rating.pg-13 { background: #3b82f6; }
        .age-rating.r { background: #ef4444; }
        .age-rating.g { background: #10b981; }

        /* ===== پەڕەکردن ===== */
        .pagination-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 50px 0;
            flex-wrap: wrap;
        }
        .page-btn {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.15);
            color: #f1f5f9;
            border-radius: 12px;
            padding: 12px 20px;
            min-width: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        .light-mode .page-btn {
            background: rgba(30, 41, 59, 0.08);
            border-color: rgba(30, 41, 59, 0.15);
            color: #1e293b;
        }
        .page-btn:hover:not(:disabled) {
            background: rgba(139, 92, 246, 0.2);
            border-color: rgba(139, 92, 246, 0.4);
            transform: translateY(-3px);
        }
        .page-btn.active {
            background: linear-gradient(90deg, #8b5cf6, #ec4899);
            color: white;
            border-color: transparent;
        }
        .page-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        .load-more-btn {
            display: block;
            margin: 30px auto 60px;
            padding: 16px 45px;
            background: linear-gradient(90deg, #8b5cf6, #ec4899);
            color: white;
            border: none;
            border-radius: 60px;
            font-weight: 700;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 25px rgba(139, 92, 246, 0.4);
        }
        .load-more-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 12px 35px rgba(139, 92, 246, 0.6);
        }
        .load-more-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        /* ===== بەشی کۆمەڵایەتی (ئینستاگرام - ئێستا لە خوارەوەیە) ===== */
        .social-section {
            text-align: center;
            margin: 80px auto 40px;
            padding: 40px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 30px;
            border: 1px solid rgba(255, 255, 255, 0.08);
            max-width: 800px;
        }
        .light-mode .social-section {
            background: rgba(30, 41, 59, 0.05);
            border-color: rgba(30, 41, 59, 0.1);
        }
        .social-title {
            font-size: 1.8rem;
            margin-bottom: 25px;
            color: #f1f5f9;
        }
        .light-mode .social-title {
            color: #1e293b;
        }
        .instagram-link {
            display: inline-flex;
            align-items: center;
            gap: 15px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: white;
            text-decoration: none;
            padding: 18px 40px;
            border-radius: 60px;
            font-weight: 700;
            font-size: 1.2rem;
            transition: all 0.4s ease;
            box-shadow: 0 10px 30px rgba(253, 29, 29, 0.3);
        }
        .instagram-link:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 40px rgba(253, 29, 29, 0.5);
        }

        /* ===== وەشاندن بۆ مۆبایل ===== */
        @media (max-width: 768px) {
            .container { padding: 15px; }
            .brand-name { font-size: 2.4rem; }
            .search-section { margin-bottom: 40px; }
            .movie-grid { grid-template-columns: 1fr; gap: 25px; }
            .movie-poster-container { height: 350px; }
            .social-section { padding: 30px 20px; margin: 60px auto 30px; }
            .instagram-link { padding: 16px 30px; font-size: 1.1rem; }
            .mode-btn { padding: 8px 16px; font-size: 0.9rem; }
        }
        @media (max-width: 480px) {
            .brand-name { font-size: 2rem; }
            .movie-poster-container { height: 320px; }
            .search-button { padding: 16px 25px; }
            .pagination-container { gap: 10px; }
            .page-btn { padding: 10px 15px; min-width: 45px; }
        }
    </style>
</head>
<body>
    <!-- مۆدی شەو/ڕۆژ (لای چەپی سەرەوە) -->
    <div class="mode-toggle">
        <button class="mode-btn" id="modeToggle">
            <i class="fas fa-moon"></i>
            <span id="modeText">Dark</span>
        </button>
    </div>

    <div class="container">
        <!-- سەردێڕ -->
        <header class="header">
            <h1 class="brand-name">Shocking Ending Movies</h1>
            <p>Discover 122+ films with the most unexpected, mind-blowing, and unforgettable endings in cinema history.</p>
        </header>

        <!-- بەشی گەڕان -->
        <section class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" placeholder="Search movie titles (e.g., 'Inception', 'Shutter Island')...">
                <button class="search-button">Search</button>
            </div>
        </section>

        <!-- ناوەڕۆکی سەرەکی: فیلمەکان (لێرە سەرەتا دێن) -->
        <div class="movies-header">
            <h2>🎬 Featured Movie Collection</h2>
            <p>Browse, search, and explore our curated list. Click any movie for more details.</p>
        </div>

        <!-- لیستی فیلمەکان (کارتەکان) -->
        <section class="movie-grid" id="movieGrid">
            <!-- فیلمەکان لە ڕێگەی JavaScript لێرە دێن -->
        </section>

        <!-- پەڕەکردن -->
        <div class="pagination-container" id="pagination">
            <!-- دوگمەکانی پەڕەکردن لە ڕێگەی JavaScript لێرە دێن -->
        </div>

        <!-- دوگمەی "زیاتر باربکە" -->
        <button class="load-more-btn" id="loadMore">
            <i class="fas fa-plus-circle"></i> Load More Movies
        </button>

        <!-- بەشی کۆمەڵایەتی (ئینستاگرام - لە خوارەوە) -->
        <section class="social-section">
            <h2 class="social-title">Follow Us for More</h2>
            <a href="https://www.instagram.com/lipri_26" class="instagram-link" target="_blank">
                <i class="fab fa-instagram"></i>
                Follow @lipri_26 on Instagram
            </a>
            <p style="margin-top: 20px; color: #94a3b8; font-size: 0.95rem;">
                Get daily recommendations, behind-the-scenes facts, and discussions about shocking movie endings.
            </p>
        </section>
    </div>

    <script>
        // ============================================
        // دەیتای فیلمەکان: ١٢٢ فیلم بە ناوی ئینگلیزی و پلۆتی ڕاستی
        // ============================================
        const movieDatabase = [
            // پەڕەی ١ (١-١٢)
            { id: 1, rank: 1, title: "Inception", year: 2010, rating: 8.8,
              plot: "A thief who steals corporate secrets through dream-sharing technology is given the inverse task of planting an idea into the mind of a C.E.O.",
              poster: "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_.jpg",
              ageRating: "pg-13" },
            { id: 2, rank: 2, title: "The Shawshank Redemption", year: 1994, rating: 9.3,
              plot: "Two imprisoned men bond over a number of years, finding solace and eventual redemption through acts of common decency.",
              poster: "https://m.media-amazon.com/images/M/MV5BNDE3ODcxYzMtY2YzZC00NmNlLWJiNDMtZDViZWM2MzIxZDYwXkEyXkFqcGdeQXVyNjAwNDUxODI@._V1_.jpg",
              ageRating: "r" },
            { id: 3, rank: 3, title: "The Dark Knight", year: 2008, rating: 9.0,
              plot: "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, Batman must accept one of the greatest psychological and physical tests of his ability to fight injustice.",
              poster: "https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_.jpg",
              ageRating: "pg-13" },
            { id: 4, rank: 4, title: "Pulp Fiction", year: 1994, rating: 8.9,
              plot: "The lives of two mob hitmen, a boxer, a gangster and his wife intertwine in four tales of violence and redemption.",
              poster: "https://m.media-amazon.com/images/M/MV5BNGNhMDIzZTUtNTBlZi00MTRlLWFjM2ItYzViMjE3YzI5MjljXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
              ageRating: "r" },
            { id: 5, rank: 5, title: "Fight Club", year: 1999, rating: 8.8,
              plot: "An insomniac office worker and a devil-may-care soap maker form an underground fight club that evolves into much more.",
              poster: "https://m.media-amazon.com/images/M/MV5BNDJiZDgyZjctYmRjMS00ZjdkLTkwMTEtNGU1NDg3NDQ0Yzk1XkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
              ageRating: "r" },
            { id: 6, rank: 6, title: "Forrest Gump", year: 1994, rating: 8.8,
              plot: "The presidencies of Kennedy and Johnson, the events of Vietnam, Watergate, and other historical events unfold through the perspective of an Alabama man with an IQ of 75.",
              poster: "https://m.media-amazon.com/images/M/MV5BNWIwODRlZTUtY2U3ZS00Yzg1LWJhNzYtMmZiYmEyNmU1NjMzXkEyXkFqcGdeQXVyMTQxNzMzNDI@._V1_.jpg",
              ageRating: "pg-13" },
            { id: 7, rank: 7, title: "The Matrix", year: 1999, rating: 8.7,
              plot: "A computer hacker learns from mysterious rebels about the true nature of his reality and his role in the war against its controllers.",
              poster: "https://m.media-amazon.com/images/M/MV5BNzQzOTk3OTAtNDQ0Zi00ZTVkLWI0MTEtMDllZjNkYzNjNTc4L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg",
              ageRating: "r" },
            { id: 8, rank: 8, title: "Goodfellas", year: 1990, rating: 8.7,
              plot: "The story of Henry Hill and his life in the mob, covering his relationship with his wife Karen Hill and his mob partners Jimmy Conway and Tommy DeVito in the Italian-American crime syndicate.",
              poster: "https://m.media-amazon.com/images/M/MV5BY2NkZjEzMDgtN2RjYy00YzM1LWI4ZmQtMjIwYjFjNmI3ZGEwXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
              ageRating: "r" },
            { id: 9, rank: 9, title: "The Silence of the Lambs", year: 1991, rating: 8.6,
              plot: "A young F.B.I. cadet must receive the help of an incarcerated and manipulative cannibal killer to help catch another serial killer.",
              poster: "https://m.media-amazon.com/images/M/MV5BNjNhZTk0ZmEtNjJhMi00YzFlLWE1MmEtYzM1M2ZmMGMwMTU4XkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg",
              ageRating: "r" },
            { id: 10, rank: 10, title: "Saving Private Ryan", year: 1998, rating: 8.6,
              plot: "Following the Normandy Landings, a group of U.S. soldiers go behind enemy lines to retrieve a paratrooper whose brothers have been killed in action.",
              poster: "https://m.media-amazon.com/images/M/MV5BZjhkMDM4MWItZTVjOC00ZDRhLThmYTAtM2I5NzBmNmNlMzI1XkEyXkFqcGdeQXVyNDYyMDk5MTU@._V1_.jpg",
              ageRating: "r" },
            { id: 11, rank: 11, title: "The Green Mile", year: 1999, rating: 8.6,
              plot: "The lives of guards on Death Row are affected by one of their charges: a black man accused of child murder and rape, yet who has a mysterious gift.",
              poster: "https://m.media-amazon.com/images/M/MV5BMTUxMzQyNjA5MF5BMl5BanBnXkFtZTYwOTU2NTY3._V1_.jpg",
              ageRating: "r" },
            { id: 12, rank: 12, title: "Interstellar", year: 2014, rating: 8.6,
              plot: "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
              poster: "https://m.media-amazon.com/images/M/MV5BZjdkOTU3MDktN2IxOS00OGEyLWFmMjktY2FiMmZkNWIyODZiXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg",
              ageRating: "pg-13" },
            // ١١٠ فیلمی دیکە لێرە دادەنرێت...
            // بۆ نمونە، تەنها ١٢ فیلمی سەرەتا نیشان دەدرێت.
        ];

        // ============================================
        // گۆڕاوە گشتییەکان و فەنکشنە سەرەکییەکان
        // ============================================
        let allMovies = [...movieDatabase];
        let filteredMovies = [...allMovies];
        const MOVIES_PER_PAGE = 12;
        let currentPage = 1;
        let totalPages = 1;

        // فەنکشنی نیشاندانی فیلمەکان بۆ پەڕەیەک
        function renderMoviesPage(page = 1) {
            const movieGrid = document.getElementById('movieGrid');
            movieGrid.innerHTML = '';
            
            const startIndex = (page - 1) * MOVIES_PER_PAGE;
            const endIndex = startIndex + MOVIES_PER_PAGE;
            const moviesToShow = filteredMovies.slice(startIndex, endIndex);
            
            if (moviesToShow.length === 0) {
                movieGrid.innerHTML = `
                    <div style="grid-column: 1 / -1; text-align: center; padding: 60px 20px; color: #94a3b8;">
                        <i class="fas fa-film fa-3x" style="margin-bottom: 20px; opacity: 0.5;"></i>
                        <h3>No movies found</h3>
                        <p>Try a different search term.</p>
                    </div>
                `;
                return;
            }
            
            moviesToShow.forEach(movie => {
                const movieCard = document.createElement('div');
                movieCard.className = 'movie-card';
                movieCard.innerHTML = `
                    <div class="movie-poster-container">
                        <img src="${movie.poster}" alt="${movie.title}" class="movie-poster" 
                             onerror="this.src='https://via.placeholder.com/300x450/1e293b/94a3b8?text=Poster+Not+Found'">
                        <div class="movie-rank">${movie.rank}</div>
                    </div>
                    <div class="movie-info">
                        <h3 class="movie-title">${movie.title}</h3>
                        <span class="movie-year">${movie.year}</span>
                        <p class="movie-plot">${movie.plot}</p>
                        <div class="movie-meta">
                            <div class="imdb-rating">
                                <i class="fas fa-star"></i> ${movie.rating}/10
                            </div>
                            <div class="age-rating ${movie.ageRating}">
                                ${movie.ageRating.toUpperCase()}
                            </div>
                        </div>
                    </div>
                `;
                movieGrid.appendChild(movieCard);
            });
        }

        // فەنکشنی نیشاندانی سیستەمی پەڕەکردن
        function renderPagination() {
            const paginationContainer = document.getElementById('pagination');
            paginationContainer.innerHTML = '';
            
            totalPages = Math.ceil(filteredMovies.length / MOVIES_PER_PAGE);
            if (totalPages <= 1) {
                document.getElementById('loadMore').style.display = 'block';
                return;
            }
            
            // دوگمەی پێشوو
            const prevButton = document.createElement('button');
            prevButton.className = `page-btn ${currentPage === 1 ? 'disabled' : ''}`;
            prevButton.innerHTML = '<i class="fas fa-chevron-left"></i>';
            prevButton.disabled = currentPage === 1;
            prevButton.addEventListener('click', () => {
                if (currentPage > 1) {
                    currentPage--;
                    renderMoviesPage(currentPage);
                    renderPagination();
                    window.scrollTo({ top: 700, behavior: 'smooth' });
                }
            });
            paginationContainer.appendChild(prevButton);
            
            // دوگمەکانی پەڕەکان
            const startPage = Math.max(1, currentPage - 2);
            const endPage = Math.min(totalPages, startPage + 4);
            
            for (let i = startPage; i <= endPage; i++) {
                const pageButton = document.createElement('button');
                pageButton.className = `page-btn ${i === currentPage ? 'active' : ''}`;
                pageButton.textContent = i;
                pageButton.addEventListener('click', () => {
                    currentPage = i;
                    renderMoviesPage(currentPage);
                    renderPagination();
                    window.scrollTo({ top: 700, behavior: 'smooth' });
                });
                paginationContainer.appendChild(pageButton);
            }
            
            // دوگمەی داهاتوو
            const nextButton = document.createElement('button');
            nextButton.className = `page-btn ${currentPage === totalPages ? 'disabled' : ''}`;
            nextButton.innerHTML = '<i class="fas fa-chevron-right"></i>';
            nextButton.disabled = currentPage === totalPages;
            nextButton.addEventListener('click', () => {
                if (currentPage < totalPages) {
                    currentPage++;
                    renderMoviesPage(currentPage);
                    renderPagination();
                    window.scrollTo({ top: 700, behavior: 'smooth' });
                }
            });
            paginationContainer.appendChild(nextButton);
            
            document.getElementById('loadMore').style.display = 'none';
        }

        // فەنکشنی گەڕان
        function setupSearch() {
            const searchInput = document.querySelector('.search-input');
            const searchButton = document.querySelector('.search-button');
            
            const performSearch = () => {
                const searchTerm = searchInput.value.trim().toLowerCase();
                if (searchTerm === '') {
                    filteredMovies = [...allMovies];
                } else {
                    filteredMovies = allMovies.filter(movie => 
                        movie.title.toLowerCase().includes(searchTerm) ||
                        movie.plot.toLowerCase().includes(searchTerm) ||
                        movie.year.toString().includes(searchTerm)
                    );
                }
                currentPage = 1;
                renderMoviesPage(currentPage);
                renderPagination();
            };
            
            searchButton.addEventListener('click', performSearch);
            searchInput.addEventListener('keyup', (event) => {
                if (event.key === 'Enter') performSearch();
            });
            
            // دەستپێکردنی گەڕان بەبێ هیچ وشەیەک
            searchInput.addEventListener('input', () => {
                if (searchInput.value.trim() === '') {
                    filteredMovies = [...allMovies];
                    currentPage = 1;
                    renderMoviesPage(currentPage);
                    renderPagination();
                }
            });
        }

        // فەنکشنی مۆدی شەو/ڕۆژ
        function setupDarkMode() {
            const modeToggle = document.getElementById('modeToggle');
            const modeIcon = modeToggle.querySelector('i');
            const modeText = document.getElementById('modeText');
            
            // چێکردنی دۆخی سەرەتا لەسەر بنەمای ڕەنگی پێشوەختەی سیستەم
            const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
            if (prefersDark) {
                document.body.classList.remove('light-mode');
                modeIcon.className = 'fas fa-moon';
                modeText.textContent = 'Dark';
            } else {
                document.body.classList.add('light-mode');
                modeIcon.className = 'fas fa-sun';
                modeText.textContent = 'Light';
            }
            
            modeToggle.addEventListener('click', () => {
                document.body.classList.toggle('light-mode');
                
                if (document.body.classList.contains('light-mode')) {
                    modeIcon.className = 'fas fa-sun';
                    modeText.textContent = 'Light';
                    localStorage.setItem('theme', 'light');
                } else {
                    modeIcon.className = 'fas fa-moon';
                    modeText.textContent = 'Dark';
                    localStorage.setItem('theme', 'dark');
                }
            });
            
            // چێکردنی دۆخی پاشەکەوتکراو لە یادگا
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme) {
                if (savedTheme === 'light') {
                    document.body.classList.add('light-mode');
                    modeIcon.className = 'fas fa-sun';
                    modeText.textContent = 'Light';
                } else {
                    document.body.classList.remove('light-mode');
                    modeIcon.className = 'fas fa-moon';
                    modeText.textContent = 'Dark';
                }
            }
        }

        // فەنکشنی دوگمەی "زیاتر باربکە"
        function setupLoadMore() {
            const loadMoreBtn = document.getElementById('loadMore');
            
            loadMoreBtn.addEventListener('click', () => {
                const nextPage = currentPage + 1;
                const startIndex = currentPage * MOVIES_PER_PAGE;
                const endIndex = startIndex + MOVIES_PER_PAGE;
                const nextMovies = filteredMovies.slice(startIndex, endIndex);
                
                if (nextMovies.length > 0) {
                    const movieGrid = document.getElementById('movieGrid');
                    
                    nextMovies.forEach(movie => {
                        const movieCard = document.createElement('div');
                        movieCard.className = 'movie-card';
                        movieCard.innerHTML = `
                            <div class="movie-poster-container">
                                <img src="${movie.poster}" alt="${movie.title}" class="movie-poster" 
                                     onerror="this.src='https://via.placeholder.com/300x450/1e293b/94a3b8?text=Poster+Not+Found'">
                                <div class="movie-rank">${movie.rank}</div>
                            </div>
                            <div class="movie-info">
                                <h3 class="movie-title">${movie.title}</h3>
                                <span class="movie-year">${movie.year}</span>
                                <p class="movie-plot">${movie.plot}</p>
                                <div class="movie-meta">
                                    <div class="imdb-rating">
                                        <i class="fas fa-star"></i> ${movie.rating}/10
                                    </div>
                                    <div class="age-rating ${movie.ageRating}">
                                        ${movie.ageRating.toUpperCase()}
                                    </div>
                                </div>
                            </div>
                        `;
                        movieGrid.appendChild(movieCard);
                    });
                    
                    currentPage = nextPage;
                    
                    // حاڵەتی دوگمەی "زیاتر باربکە" نوێ دەکەینەوە
                    const hasMoreMovies = (currentPage * MOVIES_PER_PAGE) < filteredMovies.length;
                    loadMoreBtn.style.display = hasMoreMovies ? 'block' : 'none';
                    
                    // پەڕەکردن نوێ دەکەینەوە
                    renderPagination();
                }
            });
        }

        // فەنکشنی سەرەکی بۆ دەستپێکردنی هەموو شتێک
        function initializeApp() {
            setupDarkMode();
            renderMoviesPage(currentPage);
            renderPagination();
            setupSearch();
            setupLoadMore();
            
            // نیشاندانی ژمارەی گشتی فیلمەکان لە ناونیشاندا
            const movieCountElement = document.querySelector('.movies-header p');
            if (movieCountElement) {
                movieCountElement.innerHTML = `Browse our collection of <strong>${allMovies.length}+ films</strong>. Click any movie for more details.`;
            }
        }

        // دەستپێکردنی بەرنامەکە کاتێک پەڕە بار دەکرێت
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>