# Rain-Bacarat
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Rain Baccarat - VIP PRO</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="rain"></div>
  <h1>💧 Rain Baccarat 💧</h1>
  <p class="subtitle">- VIP PRO TOOL -</p>

  <div class="section">
    <h2>Player</h2>
    <div class="card-row" id="player-cards"></div>
  </div>

  <div class="section">
    <h2>Banker</h2>
    <div class="card-row" id="banker-cards"></div>
  </div>

  <button onclick="calculate()">💡 Tính Điểm & Rút Bài</button>
  <div id="result"></div>

  <script src="script.js"></script>
</body>
</html>
body {font-family:'Segoe UI',sans-serif;padding:20px;background:linear-gradient(to bottom,#1b2735,#090a0f);color:white;text-align:center;}
h1 {font-size:2em;color:#00ccff;margin-bottom:5px;}
.subtitle {font-style:italic;margin-bottom:30px;color:#aad;}
.section {margin-bottom:30px;}
.card-row {display:flex;justify-content:center;gap:10px;flex-wrap:wrap;}
.card-row img {width:60px;height:auto;cursor:pointer;border:2px solid transparent;border-radius:5px;}
.card-row img.selected {border:2px solid #00ccff;}
button {padding:10px 20px;font-size:16px;background:#00ccff;color:#000;border:none;border-radius:8px;cursor:pointer;}
#result {margin-top:20px;font-size:1.3em;font-weight:bold;color:#ffeb3b;}
.rain {position:fixed;top:0;left:0;width:100%;height:100%;background-image:url('assets/rain.png');opacity:0.1;pointer-events:none;animation:rain 1s linear infinite;}
@keyframes rain {from{background-position:0 0;}to{background-position:0 100%;}}
const cards=["A","2","3","4","5","6","7","8","9","10","J","Q","K"];
const values={"A":1,"2":2,"3":3,"4":4,"5":5,"6":6,"7":7,"8":8,"9":9,"10":0,"J":0,"Q":0,"K":0};
function loadCards(id){const c=document.getElementById(id);cards.forEach(v=>{let img=document.createElement("img");img.src="images/"+v+"H.png";img.alt=v;img.onclick=()=>img.classList.toggle("selected");c.appendChild(img);});}
function calculate(){["player-cards","banker-cards"].forEach(id=>{const sel=document.querySelectorAll(`#${id} img.selected`);let sum=0;sel.forEach(i=>sum+=values[i.alt]);const p=id.includes("player")?"Player":"Banker";const pt=sum%10;document.getElementById("result").innerHTML+=`${p}: ${pt} điểm<br>`;});document.getElementById("result").innerHTML+="<br>💧 Gợi ý: Đặt Banker nếu chưa biết chọn gì!";}
loadCards("player-cards");loadCards("banker-cards");
