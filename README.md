<!DOCTYPE html>
<html>
<head>
<style>
body {
  margin:0;
  background:#000;
  overflow:hidden;
}

.eye {
  position:absolute;
  top:40px;
  left:50%;
  transform:translateX(-50%);
  width:180px;
  height:100px;
}

.iris {
  position:absolute;
  width:55px;
  height:55px;
  background:#ff2200;
  border-radius:50%;
  box-shadow:
  0 0 20px red,
  0 0 60px orange,
  0 0 100px red;
  top:22px;
  left:62px;
  transition:0.5s;
}

.eye-shape {
  width:180px;
  height:100px;
  border-radius:100% 0;
  background:#fff;
  transform:rotate(45deg);
  opacity:.15;
}


.point {
  position:absolute;
  width:10px;
  height:10px;
  background:white;
  border-radius:50%;
  box-shadow:
  0 0 20px white,
  0 0 50px red;
}


.explosion {
  position:absolute;
  width:10px;
  height:10px;
  border-radius:50%;
  background:red;
  animation:boom .8s forwards;
}


@keyframes boom {
  to {
    width:120px;
    height:120px;
    opacity:0;
  }
}

</style>
</head>

<body>


<div class="eye">
<div class="eye-shape"></div>
<div class="iris"></div>
</div>


<script>

const iris=document.querySelector(".iris");


function moveEye(x,y){

let eyeX=window.innerWidth/2;
let eyeY=90;


let angle=Math.atan2(
y-eyeY,
x-eyeX
);


let distance=30;


iris.style.left=
62+Math.cos(angle)*distance+"px";

iris.style.top=
22+Math.sin(angle)*distance+"px";

}



function createPoint(){

let x=Math.random()*window.innerWidth;
let y=180+Math.random()*(window.innerHeight-200);


let p=document.createElement("div");

p.className="point";

p.style.left=x+"px";
p.style.top=y+"px";


document.body.appendChild(p);



setTimeout(()=>{

moveEye(x,y);


p.className="explosion";


setTimeout(()=>{

p.remove();

},800);


},600);


}




function search(){

let x=Math.random()*window.innerWidth;
let y=Math.random()*window.innerHeight;


moveEye(x,y);


}



setInterval(()=>{

createPoint();

},2500);



setInterval(()=>{

search();

},1000);


</script>


</body>
</html>
