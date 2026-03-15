<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Heart Animation</title>

<style>
body{
    margin:0;
    background:black;
    overflow:hidden;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    font-family:Arial, sans-serif;
}

.heart{
    position:relative;
    width:650px;
    height:650px;
}

.love{
    position:absolute;
    color:#ff8fb3;
    font-size:22px;
    white-space:nowrap;
    letter-spacing:-2px; /* прибирає відступ */
}
</style>

</head>

<body>

<div class="heart" id="heart"></div>

<script>

const heart = document.getElementById("heart");
const particles = [];

function heartX(t){
    return 16*Math.pow(Math.sin(t),3);
}

function heartY(t){
    return 13*Math.cos(t) - 5*Math.cos(2*t) - 2*Math.cos(3*t) - Math.cos(4*t);
}

for(let i=0;i<120;i++){

    let span=document.createElement("span");
    span.className="love";
    span.innerText="I love you";

    heart.appendChild(span);

    particles.push({
        el:span,
        t:i*0.05
    });
}

function animate(){

    particles.forEach(p=>{

        p.t+=0.001;

        let x=heartX(p.t)*17+325;
        let y=-heartY(p.t)*17+325;

        p.el.style.left=x+"px";
        p.el.style.top=y+"px";

    });

    requestAnimationFrame(animate);
}

animate();

</script>

</body>
</html>
