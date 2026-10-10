
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Alabanza Sin Fronteras</title>
<style>
body{margin:0;background:#090909;color:white;font-family:Arial,sans-serif;text-align:center}
header{padding:35px 15px;background:#15120b;border-bottom:2px solid #d4af37}
h1{color:#d4af37}
p{line-height:1.5}
section{padding:20px 12px}
button{background:#d4af37;color:#111;border:0;border-radius:8px;padding:12px;margin:5px;font-weight:bold;cursor:pointer}
.filters{padding:10px}
#catalog{display:grid;grid-template-columns:repeat(auto-fit,minmax(145px,1fr));gap:12px;padding:12px;max-width:900px;margin:auto}
.card{background:#191919;border:1px solid #8d7427;border-radius:12px;padding:16px}
.card h3{font-size:16px}
.card p{color:#d4af37}
.player{max-width:800px;margin:auto}
#video iframe{width:100%;aspect-ratio:16/9;border:0;border-radius:10px}
footer{padding:25px;color:#d4af37}
</style>
</head>
<body>
<header>
<div style="font-size:38px">✝️ 🎵</div>
<h1>ALABANZA SIN FRONTERAS</h1>
<p>La música que glorifica a Dios, sin límites.</p>
</header>

<section>
<h2>🎶 Nuestro catálogo cristiano</h2>
<p>Elige una categoría y disfruta de nuestras alabanzas.</p>
<div class="filters">
<button onclick="filterSongs('Todos')">Todas</button>
<button onclick="filterSongs('Balada')">Baladas</button>
<button onclick="filterSongs('Reggae')">Reggae cristiano</button>
<button onclick="filterSongs('Corridos')">Corridos cristianos</button>
</div>
<div id="catalog"></div>
</section>

<section class="player">
<h2>▶️ Reproductor musical</h2>
<p id="now">Selecciona una canción del catálogo.</p>
<div id="video"></div>
</section>

<section>
<h2>🙏 Nuestra misión</h2>
<p>Llevar el mensaje de Jesucristo a cada corazón a través de la música cristiana.</p>
</section>

<footer>© Alabanza Sin Fronteras · Música para la gloria de Dios ✝️</footer>

<script>
const songs = [
{title:"Balada cristiana 1",genre:"Balada",id:"mQupxw2fpXA"},
{title:"Reggae cristiano 1",genre:"Reggae",id:"Lp-k9--sQhY"},
{title:"Reggae cristiano 2",genre:"Reggae",id:"k06o3QhEyxQ"},
{title:"Reggae cristiano 3",genre:"Reggae",id:"t2ldRak7uZs"},
{title:"Balada cristiana 2",genre:"Balada",id:"keClpljVWGo"},
{title:"Reggae cristiano 4",genre:"Reggae",id:"HVS6dWgfTFE"},
{title:"Balada cristiana 3",genre:"Balada",id:"ABpRAanjPhE"}
];

function playSong(id,title){
document.getElementById("now").textContent="Reproduciendo: "+title;
document.getElementById("video").innerHTML='<iframe src="https://www.youtube.com/embed/'+id+'" title="'+title+'" allowfullscreen></iframe>';
document.querySelector(".player").scrollIntoView({behavior:"smooth"});
}

function filterSongs(genre){
const catalog=document.getElementById("catalog");
catalog.innerHTML="";
const list=genre==="Todos"?songs:songs.filter(function(s){return s.genre===genre});
list.forEach(function(s){
const card=document.createElement("div");
card.className="card";
const icon=document.createElement("div");
icon.textContent="🎵";
const category=document.createElement("p");
category.textContent=s.genre;
const title=document.createElement("h3");
title.textContent=s.title;
const button=document.createElement("button");
button.textContent="▶ Reproducir";
button.onclick=function(){playSong(s.id,s.title)};
card.append(icon,category,title,button);
catalog.appendChild(card);
});
}
filterSongs("Todos");
</script>
</body>
</html>
