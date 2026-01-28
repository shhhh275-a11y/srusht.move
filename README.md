<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shocking Ending Movies</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: system-ui, -apple-system, sans-serif;
            background: #0f172a;
            color: #f8fafc;
            transition: background 0.3s, color 0.3s;
            padding-top: 40px;
        }
        body.light-mode { background: #f1f5f9; color: #0f172a; }
        .container { max-width: 1400px; margin: 0 auto; padding: 20px; }
        
        /* ===== مۆدی شەو/ڕۆژ لە لای چەپی سەرەوە ===== */
        .mode-toggle {
            position: fixed;
            top: 10px;
            left: 10px;
            z-index: 1000;
        }
        .mode-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            border-radius: 20px;
            padding: 8px 15px;
            cursor: pointer;
            font-size: 0.9em;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .light-mode .mode-btn {
            background: rgba(15,23,42,0.1);
            border-color: rgba(15,23,42,0.2);
            color: #0f172a;
        }
        
        /* ===== سەردێڕ ===== */
        .header { text-align: center; margin: 20px 0 40px; }
        .brand-name {
            font-size: 2.8em;
            background: linear-gradient(45deg, #f59e0b, #ef4444);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
        }
        
        /* ===== گەڕان ===== */
        .search-section { max-width: 600px; margin: 0 auto 30px; }
        .search-box {
            display: flex;
            background: rgba(255,255,255,0.1);
            border-radius: 50px;
            padding: 4px;
        }
        .light-mode .search-box { background: rgba(15,23,42,0.1); }
        .search-input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 15px 20px;
            color: inherit;
            font-size: 1em;
        }
        .search-button {
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            border: none;
            border-radius: 50px;
            padding: 15px 30px;
            color: white;
            cursor: pointer;
        }
        
        /* ===== ئینستاگرام ===== */
        .instagram-section {
            text-align: center;
            margin: 0 auto 40px;
            max-width: 500px;
        }
        .instagram-btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: white;
            padding: 12px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
        }
        
        /* ===== فیلمەکان ===== */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        .movie-card {
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
            overflow: hidden;
            transition: transform 0.3s;
        }
        .light-mode .movie-card { background: rgba(15,23,42,0.05); }
        .movie-card:hover { transform: translateY(-5px); }
        .movie-poster {
            width: 100%;
            height: 350px;
            background-size: cover;
            background-position: center;
        }
        .movie-info { padding: 20px; }
        .movie-title { font-size: 1.3em; margin-bottom: 8px; }
        .movie-meta {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
        }
        
        /* ===== پەڕەکردن ===== */
        .pagination {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 30px 0;
        }
        .page-btn {
            padding: 8px 15px;
            background: rgba(255,255,255,0.1);
            border: none;
            border-radius: 8px;
            color: inherit;
            cursor: pointer;
        }
        .load-more {
            display: block;
            margin: 40px auto;
            padding: 15px 40px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.1em;
        }
        
        @media (max-width: 768px) {
            .movie-grid { grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); }
            .brand-name { font-size: 2.2em; }
        }
    </style>
</head>
<body>
    <!-- مۆدی شەو/ڕۆژ لە لای چەپی سەرەوە -->
    <div class="mode-toggle">
        <button class="mode-btn" id="modeToggle">
            <i class="fas fa-moon"></i>
            <span>شەو</span>
        </button>
    </div>
    
    <div class="container">
        <!-- سەردێڕ -->
        <header class="header">
            <h1 class="brand-name">Shocking Ending Movies</h1>
            <p>یەکەمین سایتی کوردی بۆ فیلمەکان</p>
        </header>
        
        <!-- گەڕان -->
        <section class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" placeholder="گەڕان بە ناوی فیلم...">
                <button class="search-button">گەڕان</button>
            </div>
        </section>
        
        <!-- ئینستاگرام -->
        <section class="instagram-section">
            <a href="https://www.instagram.com/lipri_26" class="instagram-btn" target="_blank">
                <i class="fab fa-instagram"></i>
                سەردانی ئینستاگرام
            </a>
        </section>
        
        <!-- فیلمەکان -->
        <section class="movie-grid" id="movieGrid"></section>
        
        <!-- پەڕەکردن -->
        <div class="pagination" id="pagination"></div>
        
        <!-- زیاتر باربکە -->
        <button class="load-more" id="loadMore" style="display:none;">
            <i class="fas fa-plus"></i> زیاتر باربکە
        </button>
    </div>

    <script>
        // ========== مۆدی شەو/ڕۆژ ==========
        const modeToggle = document.getElementById('modeToggle');
        const modeIcon = modeToggle.querySelector('i');
        const modeText = modeToggle.querySelector('span');
        
        modeToggle.addEventListener('click', () => {
            document.body.classList.toggle('light-mode');
            if (document.body.classList.contains('light-mode')) {
                modeIcon.className = 'fas fa-sun';
                modeText.textContent = 'ڕۆژ';
            } else {
                modeIcon.className = 'fas fa-moon';
                modeText.textContent = 'شەو';
            }
        });
        
        // ========== ١٢٢ فیلم ==========
        let allMovies = [];
        const moviesPerPage = 12;
        let currentPage = 1;
        
        // دروستکردنی ١٢٢ فیلمی ساختەی
        function generateMovies() {
            const titles = [
                "ناونیشانی شاراوە", "کۆتایی گەڕان", "دووبارەبوونەوە",
                "نهێنی کۆن", "ڕاستی دوایین", "گەڕانەوە", "ئایدەنی ونبوو",
                "کاتی گۆڕان", "یادی پێشوو", "دەرئەنجامی چاوەڕواننەکراو"
            ];
            
            for (let i = 1; i <= 122; i++) {
                allMovies.push({
                    id: i,
                    title: `${titles[i % titles.length]} ${Math.floor(i/10)+1}`,
                    year: 1990 + Math.floor(Math.random() * 34),
                    rating: (6.5 + Math.random() * 2.5).toFixed(1),
                    plot: `ئەم فیلمە چیرۆکێکی سەرسوڕهێنەری هەیە کە کۆتاییەکی چاوەڕواننەکراوی تێدایە...`,
                    poster: `https://picsum.photos/300/450?random=${i}`,
                    ageRating: Math.random() > 0.5 ? 'pg13' : 'r'
                });
            }
        }
        
        // نیشاندانی فیلمەکان
        function renderMovies() {
            const movieGrid = document.getElementById('movieGrid');
            const startIndex = (currentPage - 1) * moviesPerPage;
            const endIndex = startIndex + moviesPerPage;
            const moviesToShow = allMovies.slice(startIndex, endIndex);
            
            moviesToShow.forEach(movie => {
                const card = document.createElement('div');
                card.className = 'movie-card';
                card.innerHTML = `
                    <div class="movie-poster" style="background-image: url('${movie.poster}')"></div>
                    <div class="movie-info">
                        <h3 class="movie-title">${movie.title} (${movie.year})</h3>
                        <p>${movie.plot}</p>
                        <div class="movie-meta">
                            <span>⭐ ${movie.rating}/10</span>
                            <span>${movie.ageRating === 'pg13' ? 'PG-13' : 'R (18+)'}</span>
                        </div>
                    </div>
                `;
                movieGrid.appendChild(card);
            });
            
            // نیشاندانی دوگمەی "زیاتر"
            document.getElementById('loadMore').style.display = 
                endIndex < allMovies.length ? 'block' : 'none';
        }
        
        // گەڕان
        document.querySelector('.search-button').addEventListener('click', () => {
            const searchTerm = document.querySelector('.search-input').value.toLowerCase();
            const movieCards = document.querySelectorAll('.movie-card');
            let found = false;
            
            movieCards.forEach(card => {
                const title = card.querySelector('.movie-title').textContent.toLowerCase();
                card.style.display = title.includes(searchTerm) ? 'block' : 'none';
                if (title.includes(searchTerm)) found = true;
            });
            
            if (!searchTerm) {
                movieCards.forEach(card => card.style.display = 'block');
            }
        });
        
        // دەستپێکردن
        document.addEventListener('DOMContentLoaded', () => {
            generateMovies();
            renderMovies();
            
            // کلیک لەسەر "زیاتر باربکە"
            document.getElementById('loadMore').addEventListener('click', () => {
                currentPage++;
                renderMovies();
            });
        });
    </script>
</body>
</html>