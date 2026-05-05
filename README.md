<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Movie UI</title>

<style>
body{
    margin:0;
    font-family:sans-serif;
    background:#0b0b0f;
    color:white;
}

/* Navbar */
.nav{
    display:flex;
    justify-content:space-between;
    padding:15px 30px;
    background:linear-gradient(to bottom, rgba(0,0,0,0.8), transparent);
    position:fixed;
    width:100%;
}
.logo{
    color:#ff0055;
    font-size:1.5em;
    font-weight:bold;
}

/* Hero */
.hero{
    height:80vh;
    background:url('https://picsum.photos/1200/700') center/cover;
    display:flex;
    align-items:center;
    padding:40px;
}
.hero h1{
    font-size:3em;
}

/* Rows */
.row{
    margin:20px;
}
.row h2{
    margin-bottom:10px;
}

.movies{
    display:flex;
    gap:10px;
    overflow-x:auto;
}
.card{
    min-width:150px;
    height:220px;
    background:#111;
    border-radius:8px;
    overflow:hidden;
    transition:0.3s;
}
.card:hover{
    transform:scale(1.1);
}
.card img{
    width:100%;
    height:100%;
    object-fit:cover;
}
</style>
</head>

<body>

<div class="nav">
<div class="logo">MOVIES</div>
<div>🔍</div>
</div>

<div class="hero">
<h1>🔥 Best Shocking Movies</h1>
</div>

<div class="row">
<h2>Trending</h2>
<div class="movies">
<div class="card"><img src="https://picsum.photos/200/300?1"></div>
<div class="card"><img src="https://picsum.photos/200/300?2"></div>
<div class="card"><img src="https://picsum.photos/200/300?3"></div>
<div class="card"><img src="https://picsum.photos/200/300?4"></div>
</div>
</div>

<div class="row">
<h2>Top Rated</h2>
<div class="movies">
<div class="card"><img src="https://picsum.photos/200/300?5"></div>
<div class="card"><img src="https://picsum.photos/200/300?6"></div>
<div class="card"><img src="https://picsum.photos/200/300?7"></div>
</div>
</div>

</body>
</html>
