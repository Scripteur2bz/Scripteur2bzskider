<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SCRIPTEUR2BZskider</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family: Arial, Helvetica, sans-serif;
}

body{
    background: radial-gradient(circle at top, #0d0f1a, #05060a);
    color:white;
    min-height:100vh;
    display:flex;
    flex-direction:column;
    align-items:center;
    overflow-x:hidden;
}

/* HEADER */
header{
    text-align:center;
    margin-top:20px;
}

.title-main{
    font-size:48px;
    font-weight:900;
    background: linear-gradient(90deg,#00b7ff,#0066ff,#00e1ff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    animation: shine 3s infinite linear;
}

.title-sub{
    font-size:22px;
    color:#ff2d2d;
    margin-top:-10px;
}

@keyframes shine{
    0%{filter:brightness(1);}
    50%{filter:brightness(2);}
    100%{filter:brightness(1);}
}

/* CONTAINER */
.container{
    width:90%;
    max-width:1000px;
    margin-top:30px;
    background: rgba(255,255,255,0.05);
    border:1px solid rgba(255,255,255,0.1);
    border-radius:15px;
    padding:20px;
    backdrop-filter: blur(10px);
    position:relative;
    overflow:hidden;
}

/* LIGHT EFFECT */
.container::before{
    content:"";
    position:absolute;
    top:-50%;
    left:-50%;
    width:200%;
    height:200%;
    background: linear-gradient(120deg,transparent,rgba(0,255,255,0.1),transparent);
    transform:rotate(25deg);
    animation: moveLight 6s infinite linear;
}

@keyframes moveLight{
    0%{transform:translateX(-100%) rotate(25deg);}
    100%{transform:translateX(100%) rotate(25deg);}
}

/* INPUTS */
textarea, input{
    width:100%;
    margin-top:10px;
    padding:10px;
    border-radius:8px;
    border:none;
    outline:none;
    background:#0b0f1a;
    color:white;
}

textarea{ height:150px; }

/* BUTTONS */
button{
    margin-top:15px;
    padding:10px 15px;
    border:none;
    border-radius:8px;
    cursor:pointer;
    font-weight:bold;
    transition:0.3s;
}

button:hover{ transform:scale(1.05); }

.primary{ background:#00aaff; color:white; }
.copy{ background:#00ff88; }

/* RESULT BOX */
.preview{
    margin-top:15px;
    padding:12px;
    background:#05070f;
    border-radius:10px;

    max-height:320px;
    overflow-y:auto;
    overflow-x:hidden;

    white-space:pre-wrap;
    word-break:break-word;

    border:1px solid rgba(255,255,255,0.1);
}

/* highlight */
.highlight{
    background:red;
    color:white;
    padding:2px;
}

/* loading */
.loading-box{ display:none; margin-top:15px; }
.bar{ width:100%; height:10px; background:#222; border-radius:5px; overflow:hidden; }
.progress{ height:100%; width:0%; background:linear-gradient(90deg,#00b7ff,#00ffcc); }

/* ERROR */
.error{
    color:#ff3b3b;
    margin-top:10px;
    font-weight:bold;
}

/* FOOTER */
footer{
    margin-top:40px;
    padding:20px;
    text-align:center;
    font-size:14px;
    opacity:0.7;
    max-width:900px;
}

/* CREDIT */
.credit{
    margin-top:10px;
    background:#ff0000;
    color:white;
    padding:10px 15px;
    border-radius:8px;
    display:inline-flex;
    align-items:center;
    gap:8px;
    cursor:pointer;
    transition:0.3s;
}

.credit:hover{
    background:#cc0000;
    transform:scale(1.05);
}
</style>
</head>

<body>

<header>
    <div class="title-main">SCRIPTEUR2BZ</div>
    <div class="title-sub">skider</div>
</header>

<div class="container">

    <label id="label-script">Script original</label>
    <textarea id="script"></textarea>

    <label id="label-search">Mot à chercher</label>
    <input id="search" type="text">

    <label id="label-replace">Nouveau mot</label>
    <input id="replace" type="text">

    <button class="primary" onclick="preview()" id="btn-preview">Prévisualiser</button>
    <button class="primary" onclick="startProcess()" id="btn-run">Remplacer</button>

    <div class="error" id="error"></div>

    <div class="loading-box" id="loadingBox">
        <div id="loadingText">Loading...</div>
        <div class="bar">
            <div class="progress" id="progress"></div>
        </div>
    </div>

    <div class="preview" id="preview"></div>

    <button class="copy" onclick="copyResult()" id="btn-copy">Copier le résultat</button>

</div>

<footer id="footerText">
Ce site est créé pour aider les petits créateurs de script qui n’ont pas d’inspiration, cela les aide simplement à modifier plus rapidement les scripts et changer les noms.
<br>

<div class="credit" onclick="window.open('https://youtube.com/@scripteur2bz?si=FwLg8DBPWS1UFEtj')">
▶ YouTube - Scripteur2bz
</div>
</footer>

<script>

/* ===== LANGUAGE SYSTEM ===== */
const t = {
  fr:{
    script:"Script original",
    search:"Mot à chercher",
    replace:"Nouveau mot",
    preview:"Prévisualiser",
    run:"Remplacer",
    copy:"Copier le résultat",
    loading:"Chargement...",
    error:"ERROR : mot introuvable dans le script",
    footer:"Ce site est créé pour aider les petits créateurs de script qui n’ont pas d’inspiration, cela les aide simplement à modifier plus rapidement les scripts et changer les noms."
  },
  en:{
    script:"Original script",
    search:"Word to find",
    replace:"New word",
    preview:"Preview",
    run:"Replace",
    copy:"Copy result",
    loading:"Loading...",
    error:"ERROR: word not found in script",
    footer:"This site helps small script creators to edit scripts faster and rename values easily."
  }
};

function setLang(){
    let lang = navigator.language.slice(0,2);
    let tr = t[lang] || t.fr;

    document.getElementById("label-script").innerText = tr.script;
    document.getElementById("label-search").innerText = tr.search;
    document.getElementById("label-replace").innerText = tr.replace;

    document.getElementById("btn-preview").innerText = tr.preview;
    document.getElementById("btn-run").innerText = tr.run;
    document.getElementById("btn-copy").innerText = tr.copy;

    document.getElementById("loadingText").innerText = tr.loading;
    document.getElementById("footerText").childNodes[0].textContent = tr.footer + "\n";
}

/* ===== FUNCTIONS ===== */

function preview(){
    let script = document.getElementById("script").value;
    let word = document.getElementById("search").value;
    let preview = document.getElementById("preview");
    let error = document.getElementById("error");

    let regex = new RegExp(word,"gi");

    if(!script.match(regex)){
        error.innerText = (t[navigator.language.slice(0,2)]||t.fr).error;
        return;
    }

    preview.innerHTML = script.replace(regex,m=>`<span class="highlight">${m}</span>`);
}

function startProcess(){
    let script = document.getElementById("script").value;
    let word = document.getElementById("search").value;
    let replace = document.getElementById("replace").value;

    let regex = new RegExp(word,"gi");

    if(!script.match(regex)){
        document.getElementById("error").innerText = (t[navigator.language.slice(0,2)]||t.fr).error;
        return;
    }

    document.getElementById("loadingBox").style.display="block";

    let bar = document.getElementById("progress");
    let p=0;

    let load=setInterval(()=>{
        p+=5;
        bar.style.width=p+"%";

        if(p>=100){
            clearInterval(load);
            document.getElementById("loadingBox").style.display="none";

            let result = script.replace(regex,replace);
            document.getElementById("preview").textContent=result;
        }
    },50);
}

function copyResult(){
    navigator.clipboard.writeText(document.getElementById("preview").innerText);
    alert("Copié !");
}

setLang();

</script>

</body>
</html>
