<!DOCTYPE html>
<html>
<head>
<title>Shooter Game</title>
<style>
body{
margin:0;
background:black;
overflow:hidden;
}
#player{
width:40px;
height:40px;
background:blue;
position:absolute;
bottom:20px;
left:50%;
}
.bullet{
width:6px;
height:12px;
background:yellow;
position:absolute;
}
.enemy{
width:40px;
height:40px;
background:red;
position:absolute;
top:0;
}
</style>
</head>
<body>

<div id="player"></div>

<script>

let player = document.getElementById("player");
let playerX = window.innerWidth/2;

document.addEventListener("keydown", function(e){

if(e.key=="a") playerX -= 20;
if(e.key=="d") playerX += 20;

player.style.left = playerX + "px";

if(e.key==" "){
shoot();
}

});

function shoot(){

let bullet = document.createElement("div");
bullet.className="bullet";

bullet.style.left = (playerX+17)+"px";
bullet.style.bottom="60px";

document.body.appendChild(bullet);

let move = setInterval(()=>{

bullet.style.bottom = (parseInt(bullet.style.bottom)+10)+"px";

if(parseInt(bullet.style.bottom)>window.innerHeight){
bullet.remove();
clearInterval(move);
}

},20);

}

function spawnEnemy(){

let enemy = document.createElement("div");
enemy.className="enemy";

enemy.style.left = Math.random()*window.innerWidth+"px";
enemy.style.top="0px";

document.body.appendChild(enemy);

let move = setInterval(()=>{

enemy.style.top = (parseInt(enemy.style.top)+3)+"px";

if(parseInt(enemy.style.top)>window.innerHeight){
enemy.remove();
clearInterval(move);
}

},20);

}

setInterval(spawnEnemy,1500);

</script>

</body>
</html>
