<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SRUSHT MOVE</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
:root {
    --bg: #0b0b0b;
    --text: #ffffff;
}
.light {
    --bg: #f4f4f4;
    --text: #000000;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: var(--bg);
    color: var(--text);
    transition: .4s;
}

/* LOADER */
.loader {
    position: fixed;
    inset: 0;
    background: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
}
.loader span {
    width: 60px;
    height: 60px;
    border: 6px solid red;
    border-top-color: transparent;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}
@keyframes spin {to{transform:rotate(360deg)}}

/* HEADER */
.header {
    min-height: 80vh;
    background: linear-gradient(to top, rgba(0,0,0,.85), rgba(0,0,0,.3)),
    url('https://images.unsplash.com/photo-1606112219348-204d7d8b94ee') center/cover;
    padding: 60px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.header h1 {font-size: 3.5rem;}
.header button {
    margin-top: 20px;
    padding: 12px 30px;
    border: none;
    background: red;
    color: white;
    font-size: 1rem;
    border-radius: 6px;
    cursor: pointer;
}

/* MOVIES */
.movies {padding: 40px;}
.movie-row {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 20px;
}
.movie-card {
    position: relative;
    overflow: hidden;
    border-radius: 12px;
}
.movie-card img {
    width: 100%;
    height: 320px;
    object-fit: cover;
    transition: .4s;
}
.movie-card:hover img {transform: scale(1.15);}
.movie-info {
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 15px;
    background: rgba(0,0,0,.75);
    transform: translateY(40%);
    transition: .4s;
}
.movie-card:hover .movie-info {transform: translateY(0);}
.movie-info button {
    margin-top: 10px;
    padding: 6px 10px;
    background: red;
    border: none;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

/* MODAL */
.modal {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,.85);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 999;
}
.modal iframe {
    width: 80%;
    height: 70%;
}

/* FLOATING INSTAGRAM */
.floating-social {
    position: fixed;
    left: 25px;
    bottom: 25px;
    display: flex;
    flex-direction: column;
    gap: 15px;
}
.floating-social a {
    width: 55px;
    height: 55px;
    border-radius: 50%;
    background: linear-gradient(45deg,#833ab4,#fd1d1d,#fcb045);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.6em;
}

/* TOGGLE */
.toggle {
    position: fixed;
    right: 25px;
    bottom: 25px;
    font-size: 1.5em;
    cursor: pointer;
}
</style>
</head>

<body>

<div class="loader"><span></span></div>

<div class="toggle" onclick="toggleMode()">🌙</div>

<section class="header">
    <h1>SRUSHT MOVE</h1>
    <button onclick="openModal()">▶ Watch Trailer</button>
</section>

<section class="movies">
<h2>Trending</h2>
<div class="movie-row">
    <div class="movie-card">
        <img src="https://picsum.photos/400/600?1">
        <div class="movie-info">
            Movie One
            <button onclick="openModal()">▶</button>
        </div>
    </div>
</div>
</section>

<div class="modal" onclick="closeModal()">
    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?autoplay=1"></iframe>
</div>

<div class="floating-social">
    <a href="https://www.instagram.com/ml.2050ll" target="_blank"><i class="fab fa-instagram"></i></a>
    <a href="https://www.instagram.com/lipri_26" target="_blank"><i class="fab fa-instagram"></i></a>
</div>

<script>
window.onload = () => document.querySelector('.loader').style.display = 'none';

function openModal() {
    document.querySelector('.modal').style.display = 'flex';
}
function closeModal() {
    document.querySelector('.modal').style.display = 'none';
}
function toggleMode() {
    document.body.classList.toggle('light');
}
</script>

</body>
</html>
