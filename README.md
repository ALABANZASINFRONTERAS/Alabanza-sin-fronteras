
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Alabanza Sin Fronteras</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#090909;color:#fff;font-family:Arial,sans-serif}
header{text-align:center;padding:38px 15px;background:linear-gradient(135deg,#30230b,#080808 70%);border-bottom:2px solid #c9a449}
.logo{font-size:42px}
h1{color:#e5c36b;letter-spacing:2px;font-size:clamp(22px,5vw,34px)}
header p{color:#ddd}
main{max-width:950px;margin:auto;padding:22px 16px}
h2{color:#e5c36b}
.filters{display:flex;gap:8px;flex-wrap:wrap;margin:20px 0}
button{cursor:pointer;border:1px solid #c9a449;background:#17130a;color:#e5c36b;padding:11px 14px;border-radius:22px}
button.active,button:hover{background:#d8b65b;color:#111}
.catalog{display:grid;grid-template-columns:repeat(auto-fit,minmax(145px,1fr));gap:14px}
.card{background:#171717;border:1px solid #493a1a;border-radius:12px;padding:14px;display:flex;flex-direction:column;gap:9px}
.cover{aspect-ratio:1.2;background:linear-gradient(145deg,#493714,#101010);display:flex;align-items:center;justify-content:center;border-radius:8px;font-size:42px}
.card h3{font-size:16px;margin:2px 0;color:#f2d98d}
.card p{font-size:12px;color:#bbb;margin:0}
.card button{margin-top:auto;border-radius:7px}
.player{margin-top:28px;background:#171717;border:1px solid #c9a449;border-radius:12px;padding:15px}
iframe{width:100%;aspect-ratio:16/9;border:0;border-radius:8px}
#now{color:#e5c36b}
.mission{text-align:center;margin:35px 0;color:#ccc}
footer{text-align:center;padding:25px;color:#aaa;border-top:1px solid #443719}
</style>
</head>
<body>
<header>
  <div class="logo">✝️ 🎵</div>
  <h1>ALABANZA SIN FRONTERAS</h1>
  <p>La música que glorifica a Dios, sin límites.</p>
</header>

<main>
  <h2>🎶 Nuestro catálogo cristiano</h2>
  <p>Elige una categoría y disfruta de nuestras alabanzas.</p>

  <div class="filters">
    <button class="active" onclick="filterSongs('Todos',this)">Todas</button>
    <button onclick="filterSongs('Balada',this)">Baladas</button>
    <button onclick="filterSongs('Reggae',this)">Reggae cristiano</button>
    <button onclick="filterSongs('Corridos',this)">Corridos cristianos</button>
  </div>

  <div class="catalog" id="catalog"></div>

  <section class="player">
    <h2>▶️ Reproductor musical</h2>
    <p id="now">Selecciona una canción del catálogo.</p>
    <div id="video"></div>
  </section>

  <section class="mission">
    <h2>🙏 Nuestra misión</h2>
    <p>Llevar el mensaje de Jesucristo a cada corazón a través de la música cristiana.</p>
  </section>
</main>

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
  document.getElementById("video").innerHTML=
    '<iframe src="https://www.youtube.com/embed/'+id+
    '" title="Reproductor de '+title+
    '" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>';
  document.querySelector(".player").scrollIntoView({behavior:"smooth",block:"start"});
}

function filterSongs(genre,button){
  document.querySelectorAll(".filters button").forEach(b=>b.classList.remove("active"));
  button.classList.add("active");
  const list=genre==="Todos"?songs:songs.filter(s=>
    genre==="Corridos"?s.genre==="Corridos":s.genre===genre);
  document.getElementById("catalog").innerHTML=list.map(s=>
    '<article class="card">'+
    '<div class="cover">🎵</div>'+
    '<p>'+s.genre+'</p>'+
    '<h3>'+s.title+'</h3>'+
    '<button onclick="playSong(\''+s.id+'\',\''+s.title+'\')">▶ Reproducir</button>'+
    '</article>'
  ).join("");
}

filterSongs("Todos",document.querySelector(".
