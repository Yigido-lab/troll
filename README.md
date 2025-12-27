<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Instagram</title>
<style>
body{
  background:#fafafa;
  font-family:Arial;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
}
.box{
  background:white;
  border:1px solid #dbdbdb;
  padding:40px;
  width:300px;
  text-align:center;
}
input{
  width:100%;
  padding:10px;
  margin:5px 0;
  background:#fafafa;
  border:1px solid #dbdbdb;
}
button{
  width:100%;
  background:#0095f6;
  color:white;
  border:none;
  padding:10px;
  margin-top:10px;
  font-weight:bold;
}
#scare{
  display:none;
}
img{
  width:100vw;height:100vh;
  position:fixed;top:0;left:0;
}
</style>
</head>
<body>

<div class="box" id="login">
  <h1 style="font-family:cursive">Instagram</h1>
  <input type="text" placeholder="Telefon, kullanıcı adı veya e-posta">
  <input type="password" placeholder="Şifre">
  <button onclick="fakeLogin()">Giriş Yap</button>
  <p style="color:gray;font-size:12px;margin-top:15px">
    © Meta
  </p>
</div>

<audio id="sound">
  <source src="https://www.myinstants.com/media/sounds/jumpscare.mp3">
</audio>

<div id="scare">
  <img src="https://i.imgur.com/8Km9tLL.jpg">
</div>

<script>
function fakeLogin(){
  document.getElementById("login").innerHTML =
    "<p>Giriş yapılıyor...</p>";

  setTimeout(()=>{
    // Tam ekran
    if(document.documentElement.requestFullscreen){
      document.documentElement.requestFullscreen();
    }

    document.body.innerHTML =
      document.getElementById("scare").innerHTML;

    // SES
    const audio=document.getElementById("sound");
    audio.volume=1.0;
    audio.play();

    // TİTREŞİM
    if(navigator.vibrate){
      navigator.vibrate([500,200,500,200,1000]);
    }
  },1000);
}
</script>

</body>
</html>
