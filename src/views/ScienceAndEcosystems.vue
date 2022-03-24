<template>
  <div class="container" v-if="ecosystems">
      <div class="row">
          <div class="col">
              <h1>Marine Science and ecosystemss</h1>
          </div>
      </div>
      <div class="row">
          <div class="col">
            <p>Marine science and ecosystemss are crucial to understanding how to keep our oceans and marine life healthy and abundant. ecosystemss widely vary from fjords in Scandinavia and Chile to common beaches to deep hydrothermal vents.</p>
            <p>Learn fun facts about marine science and ecosystemss, and learn how you can help by clicking a category below.</p>
          </div>
      </div>
      <div class="row justify-content-center">
			<div class="col-12 col-lg-4" v-for="ecosystem of ecosystems" :key="ecosystem._id">
				<div class="card my-5">
					<img :src="ecosystem.img" class="card-img-top" alt="...">
					<h5 class="card-title text-light">
						{{ecosystem.title}}
					</h5>
					<router-link class="btn btn-light" :to="{name: 'EcosystemDetails', params: {id: ecosystem._id}}">Read More</router-link>
				</div>
			</div>
		</div>
  </div>
  <div class="else" v-else>
    <div id="loading">

<img class="this loading-fish" src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/1465055/single%20circle.svg">
<div class="loading-text">Loading..</div>
</div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            ecosystems : null
        }
    },
    mounted() {
      fetch("https://mullins-marine-api.herokuapp.com/ecosystem", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",

        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.ecosystems = json;
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

.loading-text{
  color: black;
}
.loading-fish {
	 -webkit-backface-visibility: hidden;
	 transform-origin: center center;
	 animation: rotate 1.5s infinite;
}
 @keyframes rotate {
	 100% {
		 transform: rotate(360deg);
	}
}
 .bg-image {
	 position: absolute;
	 left: 0;
	 z-index: 0;
	 opacity: 0;
	 animation: appear 3s linear infinite;
}
 #loading img {
	 height: 200px;
	 weight: 200px;
}
 @keyframes appear {
	 0% {
		 opacity: 0;
	}
	 95% {
		 opacity: 0;
	}
	 96% {
		 opacity: 1;
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
background-color:#003459;
}

div.col-12:nth-child(2) > .card:nth-child(1) > .btn:nth-child(3):hover
{
  background-color:#003459;
}

div.col-12:nth-child(3) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(4) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(5) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(6) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(7) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(8) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
}
div.col-12:nth-child(9) > .card:nth-child(1) > .btn:nth-child(3):hover
{
 background-color:#003459;
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