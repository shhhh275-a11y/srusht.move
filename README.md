<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</title>
  <style>
    :root{
      --bg-1: #07070a;
      --bg-2: #0f1720;
      --card: rgba(255,255,255,0.04);
      --muted: rgba(255,255,255,0.72);
      --accent: #e50914; /* Netflix red-like */
      --glass: rgba(255,255,255,0.03);
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family: "Segoe UI", Tahoma, Arial, sans-serif;background:linear-gradient(180deg,var(--bg-1),var(--bg-2));color:#fff}
    body{padding:24px; -webkit-font-smoothing:antialiased}

    .container{max-width:1200px;margin:0 auto;position:relative}

    /* Header */
    header{display:flex;flex-direction:column;align-items:center;gap:10px;margin-bottom:18px;text-align:center}
    .site-title{
      display:inline-block;padding:10px 18px;border-radius:999px;background:linear-gradient(90deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.04);font-weight:700;font-size:1.05rem
    }
    .brand{
      font-size:2.6rem;font-weight:900;letter-spacing:2px;
      background:linear-gradient(90deg,#fff,#cfcfcf);
      -webkit-background-clip:text;-webkit-text-fill-color:transparent;
      text-shadow:0 10px 30px rgba(0,0,0,0.6);
    }
    .subtitle{color:var(--muted);font-size:0.95rem;margin-top:2px}

    /* Search */
    .controls{display:flex;justify-content:center;margin:18px 0}
    .search{
      width:100%;max-width:720px;display:flex;gap:8px;
      background:var(--glass);padding:8px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);
      box-shadow: 0 8px 30px rgba(0,0,0,0.6);
    }
    .search input{
      flex:1;padding:12px 14px;border:0;background:transparent;color:#fff;font-size:0.98rem;
      outline:none;
    }
    .search button{
      background:var(--accent);border:0;color:#fff;padding:10px 14px;border-radius:8px;font-weight:700;cursor:pointer;
    }

    /* Grid: 2 columns on >=700px, otherwise 1 col */
    .movie-grid{
      display:grid;grid-template-columns: repeat(2, 1fr);gap:18px;
    }
    @media (max-width:760px){ .movie-grid{grid-template-columns: 1fr} }

    .movie-card{
      background:var(--card);border-radius:12px;padding:10px;position:relative;overflow:visible;
      transition: transform .25s cubic-bezier(.2,.9,.2,1), box-shadow .25s;
      border:1px solid rgba(255,255,255,0.035);
    }
    .movie-card:focus{outline:2px solid rgba(255,255,255,0.06)}
    .movie-card:hover{transform:translateY(-8px);box-shadow:0 30px 80px rgba(0,0,0,0.6);z-index:3}

    /* Poster area: uses aspect ratio 16:9 */
    .poster{
      width:100%;aspect-ratio:16/9;border-radius:10px;background-size:cover;background-position:center;
      position:relative;overflow:hidden;border:1px solid rgba(255,255,255,0.04);
    }

    /* second image thumbnail (upper-left small) */
    .thumb{
      position:absolute;left:12px;top:12px;width:76px;height:42px;border-radius:6px;overflow:hidden;
      border:2px solid rgba(0,0,0,0.45);box-shadow:0 6px 20px rgba(0,0,0,0.6);
      transform:translateX(0);transition:transform .25s;
    }
    .movie-card:hover .thumb{transform:translateX(-6px)}

    /* play overlay on hover */
    .poster .overlay{
      position:absolute;inset:0;display:flex;align-items:center;justify-content:center;
      background:linear-gradient(180deg, rgba(0,0,0,0) 40%, rgba(0,0,0,0.5) 100%);opacity:0;transition:opacity .25s;
    }
    .movie-card:hover .poster .overlay{opacity:1}
    .play-btn{
      width:56px;height:56px;border-radius:999px;background:rgba(255,255,255,0.08);display:flex;align-items:center;justify-content:center;
      border:1px solid rgba(255,255,255,0.06);font-size:22px;color:#fff;backdrop-filter:blur(4px)
    }

    .info{display:flex;justify-content:space-between;align-items:flex-start;padding:10px 6px}
    .left{max-width:72%}
    .title{font-weight:800;font-size:1.05rem;line-height:1.05;color:#fff}
    .meta{display:flex;gap:8px;align-items:center;margin-top:8px}
    .imdb{background:linear-gradient(135deg,#f5c518,#d4af37);color:#000;padding:6px 10px;border-radius:8px;font-weight:800;font-size:0.9rem}
    .age{background:rgba(255,255,255,0.04);padding:6px 8px;border-radius:8px;font-weight:700;font-size:0.82rem;color:var(--muted)}
    .plot{color:var(--muted);font-size:0.9rem;margin-top:8px;height:56px;overflow:hidden;text-align:justify}

    /* rank circle */
    .rank{position:absolute;right:12px;top:12px;background:rgba(0,0,0,0.6);color:var(--accent);width:46px;height:46px;border-radius:999px;display:flex;align-items:center;justify-content:center;font-weight:900;border:2px solid var(--accent);box-shadow:0 10px 30px rgba(229,9,20,0.06)}

    /* footer */
    footer{margin-top:26px;text-align:center;color:var(--muted);font-size:0.95rem;padding-bottom:40px}

    /* Modal (movie details) */
    .modal-backdrop{position:fixed;inset:0;background:rgba(0,0,0,0.7);display:none;align-items:center;justify-content:center;z-index:50;padding:20px}
    .modal{width:100%;max-width:900px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:12px;padding:18px;border:1px solid rgba(255,255,255,0.04);box-shadow:0 40px 120px rgba(0,0,0,0.8);color:#fff;overflow:hidden}
    .modal-head{display:flex;gap:16px;align-items:flex-start}
    .modal-poster{width:48%;aspect-ratio:16/9;border-radius:8px;background-size:cover;background-position:center;position:relative;overflow:hidden}
    .modal-gallery{display:flex;flex-direction:column;gap:8px;width:52%}
    .modal-title{font-size:1.4rem;font-weight:900}
    .modal-meta{color:var(--muted);margin-top:6px}
    .modal-plot{margin-top:12px;color:var(--muted);line-height:1.5}
    .close-btn{position:absolute;top:12px;left:12px;background:rgba(255,255,255,0.04);border:0;padding:8px 10px;border-radius:8px;color:#fff;cursor:pointer}
    .gallery-row{display:flex;gap:8px;margin-top:10px}
    .gallery-row img{width:100%;height:120px;object-fit:cover;border-radius:8px;border:2px solid rgba(255,255,255,0.03);cursor:pointer}
    .modal-actions{display:flex;gap:10px;margin-top:12px}
    .btn{background:var(--accent);color:#fff;padding:10px 14px;border-radius:8px;border:0;font-weight:800;cursor:pointer}
    .btn.secondary{background:transparent;border:1px solid rgba(255,255,255,0.06)}
    @media (max-width:900px){
      .modal-head{flex-direction:column}
      .modal-poster{width:100%}
      .modal-gallery{width:100%}
      .gallery-row img{height:96px}
    }

  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="site-title">🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</div>
      <div class="brand">Filmi Nayab</div>
      <div class="subtitle">Discover rare & thrilling films — Kurdish curated picks</div>
    </header>

    <div class="controls" role="search" aria-label="Search movies">
      <div class="search">
        <input id="searchInput" type="search" placeholder="گەرەکە بۆ ناوی فیلم ... (Search by title)" aria-label="Search movies by title" />
        <button id="clearBtn" title="Clear search">✕</button>
        <button id="searchBtn" title="Search">🔍</button>
      </div>
    </div>

    <main>
      <section class="movie-grid" id="movieGrid" aria-live="polite">
        <!-- Movie cards will be injected by JS -->
      </section>
    </main>

    <footer>© ٢٠٢٥ Filmi Nayab — All rights reserved</footer>
  </div>

  <!-- Modal for movie details -->
  <div class="modal-backdrop" id="modalBackdrop" aria-hidden="true">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
      <button class="close-btn" id="modalClose" aria-label="Close">✕</button>
      <div class="modal-head">
        <div class="modal-poster" id="modalPoster" style="background-image:url('')"></div>
        <div class="modal-gallery">
          <div>
            <div id="modalTitle" class="modal-title">Title</div>
            <div id="modalMeta" class="modal-meta">Year • Rating</div>
          </div>
          <div class="modal-plot" id="modalPlot">Plot</div>

          <div class="gallery-row" id="galleryRow"></div>

          <div class="modal-actions">
            <button class="btn" id="playNow">Play ▶</button>
            <button class="btn secondary" id="addWatchlist">+ Watchlist</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Data: 10 movies with two images each
    const movies = [
      { id:1, title:"Dune: Part Two", year:2024, rating: "8.1", plot:"Paul Atreides continues his journey among the Fremen as political and cosmic storms converge.", img1:"https://picsum.photos/seed/dune1/1200/675", img2:"https://picsum.photos/seed/dune2/1200/675"},
      { id:2, title:"Oppenheimer", year:2023, rating: "8.5", plot:"The story of J. Robert Oppenheimer and the creation of the atomic bomb.", img1:"https://picsum.photos/seed/op1/1200/675", img2:"https://picsum.photos/seed/op2/1200/675"},
      { id:3, title:"John Wick: Chapter 4", year:2023, rating: "7.9", plot:"John Wick uncovers a path to defeating the High Table, but before he can earn his freedom, he must face new enemies.", img1:"https://picsum.photos/seed/jw1/1200/675", img2:"https://picsum.photos/seed/jw2/1200/675"},
      { id:4, title:"Joker", year:2019, rating: "8.4", plot:"A gritty character study of Arthur Fleck, a man disregarded by society, who transforms into the criminal Joker.", img1:"https://picsum.photos/seed/joker1/1200/675", img2:"https://picsum.photos/seed/joker2/1200/675"},
      { id:5, title:"The Batman", year:2022, rating: "7.8", plot:"Bruce Wayne seeks justice in Gotham as threats emerge and long-buried secrets surface.", img1:"https://picsum.photos/seed/bat1/1200/675", img2:"https://picsum.photos/seed/bat2/1200/675"},
      { id:6, title:"Inception", year:2010, rating: "8.8", plot:"A thief who steals corporate secrets through the use of dream-sharing technology takes on a final job with a dangerous twist.", img1:"https://picsum.photos/seed/inc1/1200/675", img2:"https://picsum.photos/seed/inc2/1200/675"},
      { id:7, title:"Avengers: Endgame", year:2019, rating: "8.4", plot:"The Avengers assemble once more to undo Thanos's actions and restore balance to the universe.", img1:"https://picsum.photos/seed/av1/1200/675", img2:"https://picsum.photos/seed/av2/1200/675"},
      { id:8, title:"Interstellar", year:2014, rating: "8.6", plot:"A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.", img1:"https://picsum.photos/seed/inter1/1200/675", img2:"https://picsum.photos/seed/inter2/1200/675"},
      { id:9, title:"Gladiator II", year:2024, rating: "7.5", plot:"A new story in the gladiatorial world, where honor and revenge collide in epic battles.", img1:"https://picsum.photos/seed/glad1/1200/675", img2:"https://picsum.photos/seed/glad2/1200/675"},
      { id:10, title:"The Dark Knight", year:2008, rating: "9.0", plot:"Batman faces the Joker, an agent of chaos, who seeks to undermine the city's moral order.", img1:"https://picsum.photos/seed/dk1/1200/675", img2:"https://picsum.photos/seed/dk2/1200/675"}
    ];

    // references
    const grid = document.getElementById('movieGrid');
    const searchInput = document.getElementById('searchInput');
    const searchBtn = document.getElementById('searchBtn');
    const clearBtn = document.getElementById('clearBtn');

    // modal refs
    const modalBackdrop = document.getElementById('modalBackdrop');
    const modalPoster = document.getElementById('modalPoster');
    const modalTitle = document.getElementById('modalTitle');
    const modalMeta = document.getElementById('modalMeta');
    const modalPlot = document.getElementById('modalPlot');
    const galleryRow = document.getElementById('galleryRow');
    const modalClose = document.getElementById('modalClose');

    // render function
    function renderMovies(list){
      grid.innerHTML = '';
      if(list.length === 0){
        grid.innerHTML = '<div style="grid-column:1/-1;padding:24px;text-align:center;color:var(--muted)">ئەگەر هیچ فیلمێک نەدۆزرایەوە — تکایە ناوی دروست بنووسە</div>';
        return;
      }
      list.forEach((m, idx) => {
        const card = document.createElement('article');
        card.className = 'movie-card';
        card.tabIndex = 0;
        card.setAttribute('data-id', m.id);
        card.innerHTML = `
          <div class="rank">${idx+1}</div>
          <div class="poster" style="background-image:url('${m.img1}')">
            <div class="thumb"><img src="${m.img2}" alt="${m.title} thumbnail" style="width:100%;height:100%;object-fit:cover"/></div>
            <div class="overlay"><div class="play-btn" aria-hidden="true">▶</div></div>
          </div>
          <div class="info">
            <div class="left">
              <div class="title">${m.title}</div>
              <div class="meta">
                <div class="imdb">⭐ ${m.rating}</div>
                <div class="age">${m.year}</div>
              </div>
              <div class="plot">${m.plot}</div>
            </div>
          </div>
        `;
        // click and keyboard
        card.addEventListener('click', ()=> openModal(m));
        card.addEventListener('keydown', (e)=>{ if(e.key==='Enter' || e.key===' ') { e.preventDefault(); openModal(m); }});
        grid.appendChild(card);
      });
    }

    // open modal
    function openModal(movie){
      modalPoster.style.backgroundImage = `url('${movie.img1}')`;
      modalTitle.textContent = movie.title;
      modalMeta.textContent = `${movie.year} • Rating: ${movie.rating}`;
      modalPlot.textContent = movie.plot;
      // gallery
      galleryRow.innerHTML = '';
      [movie.img1, movie.img2].forEach((src, i) => {
        const img = document.createElement('img');
        img.src = src;
        img.alt = `${movie.title} gallery ${i+1}`;
        img.tabIndex = 0;
        img.addEventListener('click', ()=> {
          modalPoster.style.backgroundImage = `url('${src}')`;
        });
        img.addEventListener('keydown', (e)=>{ if(e.key==='Enter') modalPoster.style.backgroundImage = `url('${src}')`; });
        galleryRow.appendChild(img);
      });

      modalBackdrop.style.display = 'flex';
      modalBackdrop.setAttribute('aria-hidden','false');
      // focus for accessibility
      modalClose.focus();
      // trap ESC to close
      document.addEventListener('keydown', escClose);
    }

    function closeModal(){
      modalBackdrop.style.display = 'none';
      modalBackdrop.setAttribute('aria-hidden','true');
      document.removeEventListener('keydown', escClose);
    }
    function escClose(e){
      if(e.key === 'Escape') closeModal();
    }

    modalClose.addEventListener('click', closeModal);
    modalBackdrop.addEventListener('click', function(e){
      if(e.target === modalBackdrop) closeModal();
    });

    // search
    function doSearch(){
      const q = searchInput.value.trim().toLowerCase();
      if(!q){ renderMovies(movies); return; }
      const filtered = movies.filter(m => m.title.toLowerCase().includes(q));
      renderMovies(filtered);
    }
    searchBtn.addEventListener('click', doSearch);
    clearBtn.addEventListener('click', ()=>{ searchInput.value=''; renderMovies(movies); searchInput.focus(); });
    searchInput.addEventListener('keydown', (e)=>{ if(e.key==='Enter') doSearch(); });

    // play and watchlist (demo)
    document.getElementById('playNow').addEventListener('click', ()=> alert('Play pressed — لە دەمەوە دەتوانیت پلێیەری وێدیۆ زیاد بکەیت.'));
    document.getElementById('addWatchlist').addEventListener('click', ()=> alert('زانیاری: فیلم زیادکرا بە watchlist (Demo).'));

    // initial render
    renderMovies(movies);
  </script>
</body>
</html>
