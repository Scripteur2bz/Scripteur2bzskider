<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>SCRIPTEUR2BZskider</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family:Arial, sans-serif;
    }

    body{
      background: radial-gradient(circle at top, #0d0f1a, #05060a);
      color:white;
      min-height:100vh;
      display:flex;
      flex-direction:column;
      align-items:center;
    }

    header{
      text-align:center;
      margin-top:20px;
    }

    .title-main{
      font-size:42px;
      font-weight:900;
      background: linear-gradient(90deg,#00b7ff,#0066ff,#00e1ff);
      -webkit-background-clip:text;
      -webkit-text-fill-color:transparent;
    }

    .title-sub{
      font-size:20px;
      color:#ff2d2d;
    }

    .container{
      width:90%;
      max-width:900px;
      margin-top:25px;
      background: rgba(255,255,255,0.05);
      padding:20px;
      border-radius:15px;
    }

    label{
      display:block;
      margin-top:10px;
      font-size:14px;
      opacity:0.8;
    }

    textarea, input{
      width:100%;
      margin-top:5px;
      padding:10px;
      border-radius:8px;
      border:none;
      outline:none;
      background:#0b0f1a;
      color:white;
    }

    textarea{ height:140px; }

    button{
      margin-top:15px;
      padding:10px;
      border:none;
      border-radius:8px;
      cursor:pointer;
      font-weight:bold;
      width:100%;
    }

    .primary{ background:#00aaff; color:white; }
    .copy{ background:#00ff88; }

    .preview{
      margin-top:15px;
      padding:12px;
      background:#05070f;
      border-radius:10px;
      white-space:pre-wrap;
      word-break:break-word;
      min-height:60px;
    }

    .highlight{
      background:red;
      padding:2px;
      color:white;
    }

    .error{
      color:red;
      margin-top:10px;
      font-size:14px;
    }
  </style>
</head>

<body>

<header>
  <div class="title-main">SCRIPTEUR2BZ</div>
  <div class="title-sub">skider</div>
</header>

<div class="container">

  <label id="lbl-script">Script original</label>
  <textarea id="script"></textarea>

  <label id="lbl-search">Mot à chercher</label>
  <input id="search" type="text"/>

  <label id="lbl-replace">Nouveau mot</label>
  <input id="replace" type="text"/>

  <button class="primary" onclick="preview()" id="btn-preview">Prévisualiser</button>
  <button class="primary" onclick="startProcess()" id="btn-run">Remplacer</button>

  <div class="error" id="error"></div>

  <div class="preview" id="preview"></div>

  <button class="copy" onclick="copyResult()" id="btn-copy">Copier</button>

</div>

<script>
const t = {
  fr:{
    script:"Script original",
    search:"Mot à chercher",
    replace:"Nouveau mot",
    preview:"Prévisualiser",
    run:"Remplacer",
    copy:"Copier",
    error:"Mot introuvable dans le script",
    copied:"Copié !"
  },
  en:{
    script:"Original script",
    search:"Word to find",
    replace:"New word",
    preview:"Preview",
    run:"Replace",
    copy:"Copy",
    error:"Word not found in script",
    copied:"Copied!"
  }
};

function lang(){
  return (navigator.language || "fr").slice(0,2);
}

function setLang(){
  let tr = t[lang()] || t.fr;

  document.getElementById("lbl-script").innerText = tr.script;
  document.getElementById("lbl-search").innerText = tr.search;
  document.getElementById("lbl-replace").innerText = tr.replace;

  document.getElementById("btn-preview").innerText = tr.preview;
  document.getElementById("btn-run").innerText = tr.run;
  document.getElementById("btn-copy").innerText = tr.copy;
}

function escapeRegex(t){
  return t.replace(/[.*+?^${}()|[\]\\]/g,'\\$&');
}

function preview(){
  let script = document.getElementById("script").value;
  let word = document.getElementById("search").value;
  let out = document.getElementById("preview");

  if(!word) return;

  let regex = new RegExp(escapeRegex(word),"gi");

  if(!script.match(regex)){
    document.getElementById("error").innerText = t[lang()].error;
    return;
  }

  document.getElementById("error").innerText = "";

  out.innerHTML = script.replace(regex,m=>`<span class="highlight">${m}</span>`);
}

function startProcess(){
  let script = document.getElementById("script").value;
  let word = document.getElementById("search").value;
  let replace = document.getElementById("replace").value;

  let regex = new RegExp(escapeRegex(word),"gi");

  if(!script.match(regex)){
    document.getElementById("error").innerText = t[lang()].error;
    return;
  }

  document.getElementById("preview").textContent = script.replace(regex,replace);
}

function copyResult(){
  navigator.clipboard.writeText(
    document.getElementById("preview").innerText
  );

  alert(t[lang()].copied);
}

setLang();
</script>

</body>
</html>
