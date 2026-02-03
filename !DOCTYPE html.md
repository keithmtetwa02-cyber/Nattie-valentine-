<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<title>For Nattie 💖</title>  
  
<style>  
body{  
  margin:0;  
  height:100vh;  
  display:flex;  
  justify-content:center;  
  align-items:center;  
  background:linear-gradient(135deg,#ff9a9e,#fad0c4);  
  font-family:'Segoe UI',sans-serif;  
  overflow:hidden;  
  color:#5a0f2e;  
}  
  
.card{  
  background:white;  
  padding:30px;  
  border-radius:20px;  
  box-shadow:0 10px 30px rgba(0,0,0,.25);  
  max-width:360px;  
  width:90%;  
  text-align:center;  
  position:relative;  
  z-index:2;  
}  
  
button{  
  padding:12px 25px;  
  margin:10px;  
  border:none;  
  border-radius:30px;  
  font-size:16px;  
  cursor:pointer;  
}  
  
.yes{background:#ff4d6d;color:white;}  
.no{background:#ddd;}  
  
.heart{  
  position:absolute;  
  animation:float 6s linear infinite;  
  font-size:18px;  
  opacity:.7;  
}  
  
@keyframes float{  
  from{transform:translateY(100vh);opacity:0;}  
  20%{opacity:1;}  
  to{transform:translateY(-10vh);opacity:0;}  
}  
  
.confetti{  
  position:absolute;  
  animation:fall 3s linear forwards;  
}  
  
@keyframes fall{  
  from{transform:translateY(0);opacity:1;}  
  to{transform:translateY(100vh);opacity:0;}  
}  
</style>  
</head>  
  
<body>  
  
<audio id="music" loop>  
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_5e0e1f7c85.mp3">  
</audio>  
  
<div class="card" id="content"></div>  
  
<script>  
const content = document.getElementById("content");  
const music = document.getElementById("music");  
  
function start(){  
  const saved = localStorage.getItem("answer");  
  if(saved){  
    content.innerHTML = saved;  
    return;  
  }  
  content.innerHTML = `  
    <h1>💌 Will you be my Valentine, Nattie?</h1>  
    <button class="yes" onclick="yes()">Yes 💕</button>  
    <button class="no" onmouseover="moveNo()">No 😅</button>  
  `;  
}  
start();  
  
function yes(){  
  music.play();  
  confetti();  
  typeText(  
    "💖 You complete me, mi amor.<br>Wifing you is all I think about.<br><br>📸 Screenshot this and send it back 💕"  
  );  
}  
  
function moveNo(){  
  event.target.style.transform =  
    `translate(${Math.random()*200-100}px,${Math.random()*200-100}px)`;  
}  
  
function typeText(text){  
  let i=0;  
  content.innerHTML="<h1></h1><p id='t'></p>";  
  const t=document.getElementById("t");  
  const typing=setInterval(()=>{  
    t.innerHTML=text.slice(0,i);  
    i++;  
    if(i>text.length){  
      clearInterval(typing);  
      localStorage.setItem("answer",content.innerHTML);  
    }  
  },40);  
}  
  
function confetti(){  
  for(let i=0;i<30;i++){  
    const c=document.createElement("div");  
    c.className="confetti";  
    c.innerHTML="💗";  
    c.style.left=Math.random()*100+"vw";  
    c.style.top="-20px";  
    c.style.fontSize=Math.random()*20+10+"px";  
    document.body.appendChild(c);  
    setTimeout(()=>c.remove(),3000);  
  }  
}  
  
// floating background hearts  
setInterval(()=>{  
  const h=document.createElement("div");  
  h.className="heart";  
  h.innerHTML="💗";  
  h.style.left=Math.random()*100+"vw";  
  h.style.fontSize=Math.random()*20+10+"px";  
  document.body.appendChild(h);  
  setTimeout(()=>h.remove(),6000);  
},500);  
</script>  
  
</body>  
</html>  
