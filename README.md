<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Yükleniyor...</title>
<style>
body{
  background:black;color:white;
  font-family:Arial;text-align:center;
  margin-top:20%;
}
#bar{
  width:80%;height:30px;
  border:2px solid white;
  margin:20px auto;
}
#fill{
  height:100%;width:0%;
  background:red;
}
#text{font-size:20px}
#count{font-size:80px;display:none}
#scare{display:none}
img{
  width:100vw;height:100vh;
  position:fixed;top:0;left:0
}
</style>
</head>
<body>

<h1>Gerçek sigma bekler.</h1>
<p id="text">Sakın sayfayı kapatma.</p>

<div id="bar"><div id="fill"></div></div>
<div id="count">3</div>

<audio id="sound">
  <source src="https://www.myinstants.com/media/sounds/jumpscare.mp3">
</audio>

<div id="scare">
  <img src="https://i.imgur.com/8Km9tLL.jpg">
</div>

<script>
let load=0;
let bar=setInterval(()=>{
  load++;
  document.getElementById("fill").style.width=load+"%";
  if(load>=99){
    clearInterval(bar);
    startCount();
  }
},50);

function startCount(){
  document.getElementById("bar").style.display="none";
  document.getElementById("text").innerText="Hazırlan...";
  const count=document.getElementById("count");
  count.style.display="block";

  let n=3;
  let timer=setInterval(()=>{
    count.innerText=n;
    n--;
    if(n<0){
      clearInterval(timer);
      jumpscare();
    }
  },1000);
}

function jumpscare(){
  if(document.documentElement.requestFullscreen){
    document.documentElement.requestFullscreen();
  }

  document.body.innerHTML=document.getElementById("scare").innerHTML;

  const audio=document.getElementById("sound");
  audio.volume=1.0;
  audio.play();

  if(navigator.vibrate){
    navigator.vibrate([600,200,600,200,1200]);
  }
}
</script>

</body>
</html>
