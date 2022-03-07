<template>
  <div class="container" v-if="coral">
      <div class="row">
          <div class="col">
              <h1>Corals and Other Invertebrates</h1>
          </div>
      </div>
      <div class="row">
          <div class="col">
            <p>Oceans are home to a diverse assortment of corals, starfish, jellyfish, sea slugs, kelp and more. Corals are living creatures that often live in compact colonies and build up coral reefs, the biggest of which is the Great Barrier Reef off the coast of Queensland, Australia. Corals and other invertebrates face major threats from climate change and destructive fishing like dynamite fishing, bottom trawling and more.

</p>
            <p>Learn fun facts about how you can help protect corals and other invertebrates by click a species below.</p>
          </div>
      </div>
      <div class="row justify-content-center">
			<div class="col-12 col-lg-4" v-for="corals of coral" :key="corals._id">
				<div class="card my-5">
					<img :src="corals.img" class="card-img-top" alt="...">
					<h5 class="card-title text-light">
						{{corals.title}}
					</h5>
					<router-link class="btn btn-light" to="coralDetails">Read More</router-link>
				</div>
			</div>
		</div>
  </div>
  <div class="else" v-else>
    <div class="boxes">
    <div class="box">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
    <div class="box">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
    <div class="box">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
    <div class="box">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </div>
</div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            coral : null
        }
    },
    mounted() {
      fetch("https://mullins-marine-api.herokuapp.com/coral", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",

        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.coral = json;
        })
        .catch((err) => {
          alert(console.log(err));
        });
  },
}
</script>

<style scoped>
.else {
    min-height: 100vh;
    font-family: Roboto, Arial;
    color: #ADAFB6;
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(249, 251, 255,0.6);  
    }

.boxes {
    height: 32px;
    width: 32px;
    position: relative;
    -webkit-transform-style: preserve-3d;
    transform-style: preserve-3d;
    -webkit-transform-origin: 50% 50%;
    transform-origin: 50% 50%;
    margin-top: 32px;
    -webkit-transform: rotateX(60deg) rotateZ(45deg) rotateY(0deg) translateZ(0px);
    transform: rotateX(60deg) rotateZ(45deg) rotateY(0deg) translateZ(0px);
}
.boxes .box {
    width: 32px;
    height: 32px;
    top: 0px;
    left: 0;
    position: absolute;
    -webkit-transform-style: preserve-3d;
    transform-style: preserve-3d;
}



.boxes .box:nth-child(1) {
    -webkit-transform: translate(100%, 0);
    transform: translate(100%, 0);
    -webkit-animation: box1 1s linear infinite;
    animation: box1 1s linear infinite;
}
.boxes .box:nth-child(2) {
    -webkit-transform: translate(0, 100%);
    transform: translate(0, 100%);
    -webkit-animation: box2 1s linear infinite;
    animation: box2 1s linear infinite;
}
.boxes .box:nth-child(3) {
    -webkit-transform: translate(100%, 100%);
    transform: translate(100%, 100%);
    -webkit-animation: box3 1s linear infinite;
    animation: box3 1s linear infinite;
}
.boxes .box:nth-child(4) {
    -webkit-transform: translate(200%, 0);
    transform: translate(200%, 0);
    -webkit-animation: box4 1s linear infinite;
    animation: box4 1s linear infinite;
}



.boxes .box > div {
    background: #5C8DF6;
    --translateZ: 15.5px;
    --rotateY: 0deg;
    --rotateX: 0deg;
    position: absolute;
    width: 100%;
    height: 100%;
    background: #5C8DF6;
    top: auto;
    right: auto;
    bottom: auto;
    left: auto;
    -webkit-transform: rotateY(var(--rotateY)) rotateX(var(--rotateX)) translateZ(var(--translateZ));
    transform: rotateY(var(--rotateY)) rotateX(var(--rotateX)) translateZ(var(--translateZ));
}

.boxes .box > div:nth-child(1) {
    top: 0;
    left: 0;
    background: #5C8DF6;
}
.boxes .box > div:nth-child(2) {
    background: #145af2;
    right: 0;
    --rotateY: 90deg;
}
.boxes .box > div:nth-child(3) {
    background: #447cf5;
    --rotateX: -90deg;
}
.boxes .box > div:nth-child(4) {
    background: #DBE3F4;
    top: 0;
    left: 0;
    --translateZ: -90px;
}





@keyframes box1 {
    0%,
    50% {
        transform: translate(100%, 0);
    }
    100% {
        transform: translate(200%, 0);
    }
}

@keyframes box2 {
    0%{
        transform: translate(0, 100%);
    }
    50% {
        transform: translate(0, 0);
    }
    100% {
        transform: translate(100%, 0);
    }
}

@keyframes box3 {
    0%,
    50% {
        transform: translate(100%, 100%);
    }
    100% {
        transform: translate(0, 100%);
    }
}

@keyframes box4 {
    0%{
        transform: translate(200%, 0);
    }
    50% {
        transform: translate(200%, 100%);
    }
    100% {
        transform: translate(100%, 100%);
    }
}
@-webkit-keyframes animation-bg {
0% {
  background-position: 50% 100%;
}
100% {
  background-position: 50% 0%;
}
}
@keyframes animation-bg {
0% {
  background-position: 50% 100%;
}
100% {
  background-position: 50% 0%;
}
}
.container{
    text-align: center;
}
section
{
  margin-top:5rem;
}

.card 
{
margin-top:5%;
  -webkit-transition: all .2s ease-out;
-moz-transition: all .2s ease-out;
-ms-transition: all .2s ease-out;
-o-transition: all .2s ease-out;
 transition: all .2s ease-out;
border-radius:15px;
border:none;
  background-color:white;
}


.btn 
{
opacity:0;  
position:absolute;
left:50%;
top: 110%;
 transform: translate(-50%, -50%);
 box-shadow: 0 4px 18px 0 rgba(0, 0, 0, 0);
-webkit-transition: all .2s ease-out;
-moz-transition: all .2s ease-out;
-ms-transition: all .2s ease-out;
-o-transition: all .2s ease-out;
 transition: all .2s ease-out;
border-radius: 10px;
padding:0.8rem 1.7rem;
border:none;
font-weight:bold;
}

.card:hover .btn
{
opacity:1;
top: 100%;
 box-shadow: 0 4px 18px 0 rgba(0, 0, 0, 0.25);
}

.card:hover
{
box-shadow: 0 4px 18px 0 rgba(0,0,0,0.7);

}

h5
{
position: absolute;
left:50%;
top: 50%;
transform: translate(-50%, -50%);
font-size: 2.7rem;
opacity:0.3;
text-shadow: 1px 1px 2px black;
-webkit-transition: all .2s ease-out;
-moz-transition: all .2s ease-out;
-ms-transition: all .2s ease-out;
-o-transition: all .2s ease-out;
 transition: all .2s ease-out;
  font-family: 'Leckerli One', cursive;
}

.card:hover h5
{
opacity:1;
  font-size: 3rem;
}

.btn:hover 
{
color:white;
border:none;
}

div.col-12:nth-child(1) > .card:nth-child(1) > .btn:nth-child(3):hover
{
background-color:Navy;
}

div.col-12:nth-child(2) > .card:nth-child(1) > .btn:nth-child(3):hover
{
  background-color:Navy;
}

div.col-12:nth-child(3) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(4) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(5) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(6) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(7) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(8) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}
div.col-12:nth-child(9) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:Navy;
}

.card img
{
height: 300px;
filter:blur(0px);
  -webkit-transition: all .2s ease-out;
-moz-transition: all .2s ease-out;
-ms-transition: all .2s ease-out;
-o-transition: all .2s ease-out;
 transition: all .2s ease-out;
border-radius:15px;
}

.card:hover img
{
filter:blur(1px);
}



</style>