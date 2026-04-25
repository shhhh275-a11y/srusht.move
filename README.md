<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        :root { --bg: #0a0a0a; --bg2: #141414; --card: #1a1a1a; --accent: #e50914; --gold: #f5c518; --text: #fff; --text2: #999; }
        * { margin:0; padding:0; box-sizing:border-box; }
        body { font-family: 'Cairo', sans-serif; background: var(--bg); color: var(--text); direction: rtl; }
        .navbar { height: 70px; background: rgba(10,10,10,0.95); display: flex; align-items: center; justify-content: space-between; padding: 0 5%; position: fixed; width: 100%; top: 0; z-index: 1000; border-bottom: 1px solid rgba(255,255,255,0.1); }
        .logo { color: var(--accent); font-size: 24px; font-weight: 900; text-decoration: none; }
        .container { max-width: 1200px; margin: 100px auto 50px; padding: 0 20px; }
        .movie-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 20px; }
        .movie-card { background: var(--card); border-radius: 12px; overflow: hidden; transition: 0.3s; cursor: pointer; border: 1px solid rgba(255,255,255,0.05); }
        .movie-card:hover { transform: translateY(-10px); border-color: var(--accent); }
        .card-poster { width: 100%; height: 270px; object-fit: cover; }
        .card-info { padding: 12px; }
        .card-info h3 { font-size: 14px; margin-bottom: 8px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        .card-meta { display: flex; justify-content: space-between; font-size: 12px; color: var(--text2); }
        .rating { color: var(--gold); }
        #loadMore { display: block; margin: 40px auto; padding: 10px 30px; background: var(--accent); color: white; border: none; border-radius: 5px; cursor: pointer; }
    </style>
</head>
<body>

<nav class="navbar">
    <a href="#" class="logo">SRUSHT MOVIES</a>
</nav>

<div class="container">
    <div class="movie-grid" id="movieGrid"></div>
    <button id="loadMore">زیاتر نیشان بدە</button>
</div>

<script>
    // لێرەدا ٢٠ فیلمی نوێ و وێنەی کارام داناوە
    const movies = [
        { id: 1, title: "Inception", year: 2010, rating: 8.8, genre: "Sci-Fi", image: "https://image.tmdb.org/t/p/w500/o0s7uAtvHcfsS7BqZuSfkMlhZpI.jpg" },
        { id: 2, title: "The Dark Knight", year: 2008, rating: 9.0, genre: "Action", image: "https://image.tmdb.org/t/p/w500/qJ2tW6WMUDp9sWZuBFnCptGHRP1.jpg" },
        { id: 3, title: "Interstellar", year: 2014, rating: 8.7, genre: "Sci-Fi", image: "https://image.tmdb.org/t/p/w500/gEU2QniE6EJBv4vU4BMYpP6Kyqz.jpg" },
        { id: 4, title: "The Godfather", year: 1972, rating: 9.2, genre: "Crime", image: "https://image.tmdb.org/t/p/w500/3bhkrjOiZ4Ejv9UGv2LpY9YyOFC.jpg" },
        { id: 5, title: "Breaking Bad", year: 2008, rating: 9.5, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/ggFHnq8vlk099Fv933fsITUqJtG.jpg" },
        { id: 6, title: "The Prestige", year: 2006, rating: 8.5, genre: "Thriller", image: "https://image.tmdb.org/t/p/w500/bdN3g8pA7DTnnVMp9kZpU6qFd6z.jpg" },
        { id: 7, title: "Gladiator", year: 2000, rating: 8.5, genre: "Action", image: "https://image.tmdb.org/t/p/w500/ty8TGRjI4WqWt13mSfwv2ScOV9.jpg" },
        { id: 8, title: "Joker", year: 2019, rating: 8.4, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/udDclsvMblWWS0m20v96QACtAsy.jpg" },
        { id: 9, title: "Spider-Man", year: 2023, rating: 8.7, genre: "Animation", image: "https://image.tmdb.org/t/p/w500/8Vtptm9CAsV1WvSjofjbsCqK90C.jpg" },
        { id: 10, title: "The Last of Us", year: 2023, rating: 8.8, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/uKvH56B29V7uSqvQn0A1Qp668pl.jpg" },
        { id: 11, title: "Oppenheimer", year: 2023, rating: 8.4, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/8GxvA0zMBsuQMRdls6cyuX49Cfs.jpg" },
        { id: 12, title: "The Shawshank Redemption", year: 1994, rating: 9.3, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/lyQBXUEwyd7vS78u9vnu1u9nInM.jpg" },
        { id: 13, title: "Pulp Fiction", year: 1994, rating: 8.9, genre: "Crime", image: "https://image.tmdb.org/t/p/w500/d5iIlCMH0b2hSvp8qPjBaseYwY2.jpg" },
        { id: 14, title: "Avatar 2", year: 2022, rating: 7.6, genre: "Sci-Fi", image: "https://image.tmdb.org/t/p/w500/t6Sna4v9S6S0p3v6uS9Yp9oUS.jpg" },
        { id: 15, title: "Chernobyl", year: 2019, rating: 9.4, genre: "Drama", image: "https://image.tmdb.org/t/p/w500/hlLtx9p96vpe66p9u6Z6i9vvpS3.jpg" },
        { id: 16, title: "The Lion King", year: 1994, rating: 8.5, genre: "Animation", image: "https://image.tmdb.org/t/p/w500/sKCr7SZeroSKm0R3Sqc0hfMBd9t.jpg" },
        { id: 17, title: "Parasite", year: 2019, rating: 8.5, genre: "Thriller", image: "https://image.tmdb.org/t/p/w500/7IiTTjSFeSj7Z3I02mIuQ9sb9sb.jpg" },
        { id: 18, title: "The Matrix", year: 1999, rating: 8.7, genre: "Sci-Fi", image: "https://image.tmdb.org/t/p/w500/f89U3Y9SJuCYFJj79jY9SvbS6pP.jpg" },
        { id: 19, title: "Dune: Part Two", year: 2024, rating: 8.9, genre: "Sci-Fi", image: "https://image.tmdb.org/t/p/w500/66S9S6S9S6S9S6S9S6S9S6S9.jpg" },
        { id: 20, title: "Stranger Things", year: 2016, rating: 8.7, genre: "Thriller", image: "https://image.tmdb.org/t/p/w500/49WJ9vBne1Jm3pS6G6STo0GLCXv.jpg" }
    ];

    let itemsToShow = 8;
    const movieGrid = document.getElementById('movieGrid');

    function renderMovies() {
        movieGrid.innerHTML = '';
        movies.slice(0, itemsToShow).forEach(movie => {
            const card = document.createElement('div');
            card.className = 'movie-card';
            
            const img = document.createElement('img');
            img.className = 'card-poster';
            img.src = movie.image;
            // ئەمە وێنە تێکچووەکان چاک دەکات
            img.onerror = function() {
                this.src = 'https://via.placeholder.com/500x750/1a1a1a/ffffff?text=No+Image';
            };

            card.innerHTML = `
                <div class="card-info">
                    <h3>${movie.title}</h3>
                    <div class="card-meta">
                        <span>${movie.year}</span>
                        <span class="rating"><i class="fas fa-star"></i> ${movie.rating}</span>
                    </div>
                </div>
            `;
            card.prepend(img);
            movieGrid.appendChild(card);
        });
    }

    document.getElementById('loadMore').addEventListener('click', () => {
        itemsToShow += 8;
        renderMovies();
        if(itemsToShow >= movies.length) document.getElementById('loadMore').style.display = 'none';
    });

    renderMovies();
</script>

</body>
</html>
