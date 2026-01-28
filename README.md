<!DOCTYPE html>
<html lang="ku">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SRUSHT MOVE</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
:root {
  --bg:#0b0b0b;
  --text:#fff;
}
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:Segoe UI, sans-serif;
}
body{
  background:var(--bg);
  color:var(--text);
}

/* HEADER */
.header{
  min-height:80vh;
  background:
  linear-gradient(to top,rgba(0,0,0,.85),rgba(0,0,0,.3)),
  url('https://images.unsplash.com/photo-1606112219348-204d7d8b94ee')
  center/cover;
  padding:60px;
  display:flex;
  flex-direction:column;
  justify-content:center;
}
.header h1{
  font-size:3.5rem;
}
.header p{
  max-width:450px;
  opacity:.85;
}

/* MOVIES */
.movies{
  padding:40px;
}
.movie-row{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:20px;
}
.movie-card{
  position:relative;
  overflow:hidden;
  border-radius:14px;
}
.movie-card img{
  width:100%;
  height:320px;
  object-fit:cover;
  transition:.4s;
}
.movie-card:hover img{
  transform:scale(1.12);
}
.movie-info{
  position:absolute;
  bottom:0;
  width:100%;
  padding:15px;
  background:linear-gradient(to top,rgba(0,0,0,.85),transparent);
  transform:translateY(40%);
  transition:.4s;
}
.movie-card:hover .movie-info{
  transform:translateY(0);
}

/* INSTAGRAM OWNER */
.floating-social{
  position:fixed;
  left:25px;
  bottom:25px;
  display:flex;
  flex-direction:column;
  gap:15px;
  z-index:999;
}
.floating-social a{
  display:flex;
  align-items:center;
  gap:12px;
  padding:12px 18px;
  border-radius:40px;
  background:linear-gradient(45deg,#833ab4,#fd1d1d,#fcb045);
  color:white;
  text-decoration:none;
  box-shadow:0 0 30px rgba(253,29,29,.7);
  transition:.35s;
}
.floating-social a:hover{
  transform:scale(1.08);
  box-shadow:0 0 45px rgba(253,29,29,.9);
}
.floating-social i{
  font-size:1.5em;
}
.floating-social small{
  font-size:.75rem;
  opacity:.85;
}

/* FOOTER */
footer{
  text-align:center;
  padding:20px;
  opacity:.5;
}
</style>
</head>

<body>

<section class="header">
  <h1>SRUSHT MOVE</h1>
  <p>بینینی فیلم بە شێوەیەکی مۆدرن و سینەمایی</p>
</section>

<section class="movies">
  <h2>Trending Now</h2>
  <div class="movie-row">
    <div class="movie-card">
      <img src="https://picsum.photos/400/600?1">
      <div class="movie-info">Movie One</div>
    </div>
    <div class="movie-card">
      <img src="https://picsum.photos/400/600?2">
      <div class="movie-info">Movie Two</div>
    </div>
    <div class="movie-card">
      <img src="https://picsum.photos/400/600?3">
      <div class="movie-info">Movie Three</div>
    </div>
  </div>
</section>

<!-- INSTAGRAM OWNERS -->
<div class="floating-social">
  <a href="https://www.instagram.com/ml.2050ll" target="_blank">
    <i class="fab fa-instagram"></i>
    <span>
      ML Team<br>
      <small>لە ئینستاگرام لەگەڵمان بن</small>
    </span>
  </a>

  <a href="https://www.instagram.com/lipri_26" target="_blank">
    <i class="fab fa-instagram"></i>
    <span>
      Lipri Team<br>
      <small>لە ئینستاگرام لەگەڵمان بن</small>
    </span>
  </a>
</div>

<footer>
  © 2026 SRUSHT MOVE
</footer>

</body>
</html>
