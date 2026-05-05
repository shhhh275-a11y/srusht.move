<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shocking Ending Movies</title>

<style>
body{
    margin:0;
    font-family:sans-serif;
    background:#0f172a;
    color:white;
}
header{
    text-align:center;
    padding:20px;
    font-size:2em;
    background:linear-gradient(45deg,#ff004c,#ff7a00);
}
.search{
    display:flex;
    justify-content:center;
    margin:20px;
}
.search input{
    padding:10px;
    width:60%;
}
.search button{
    padding:10px;
    background:red;
    color:white;
    border:none;
}
.grid{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax(200px,1fr));
    gap:20px;
    padding:20px;
}
.card{
    background:#1e293b;
    border-radius:10px;
    overflow:hidden;
    transition:0.3s;
}
.card:hover{transform:scale(1.05);}
.card img{width:100%;}
.info{padding:10px;}
.instagram{
    text-align:center;
    margin:20px;
}
</style>
</head>

<body>

<header>🔥 Shocking Ending Movies</header>

<div class="search">
<input id="searchInput" placeholder="گەڕان...">
<button onclick="search()">گەڕان</button>
</div>

<div class="instagram">
<a href="https://www.instagram.com/lipri_09?igsh=MXQ0NG1icnc3Ym11NA==" target="_blank">
Instagram
</a>
</div>

<div class="grid" id="movies"></div>

<script>

const API_KEY = "df3194b0b76a3ac936ceb1b11c3e63d3";

async function getMovies(query="movie"){
    const url = `https://api.themoviedb.org/3/search/movie?api_key=${API_KEY}&query=${query}`;
    const res = await fetch(url);
    const data = await res.json();
    showMovies(data.results);
}

function showMovies(movies){
    const container = document.getElementById("movies");
    container.innerHTML="";
    movies.forEach(m=>{
        const div = document.createElement("div");
        div.className="card";
        div.innerHTML=`
        <img src="https://image.tmdb.org/t/p/w500${m.poster_path}">
        <div class="info">
        <h3>${m.title}</h3>
        <p>⭐ ${m.vote_average}</p>
        </div>`;
        container.appendChild(div);
    });
}

function search(){
    const q = document.getElementById("searchInput").value;
    getMovies(q);
}

getMovies();

</script>

</body>
</html>
