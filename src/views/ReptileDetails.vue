<template>
<div class="container mt-4" v-if="reptile">
  <div class="row">
    <div class="col text-center">
      <h1>
        {{reptile.title}}
      </h1>
    </div>
  </div>
     <div class="row">
      <!-- Blog entries-->
      <div class="col-lg-8">
        <!-- Featured blog post-->
        <div class="card mb-4">
          <a href="#!"><img class="card-img-top" :src="reptile.img" alt="..." /></a>
          <div class="card-body">
            <p class="card-text">{{reptile.description}}</p>
          </div>
        </div>
        <!-- Nested row for non-featured blog posts-->
      </div>
      <!-- Side widgets-->
      <div class="col-lg-4">
        <!--  widget-->
        <div class="card mb-4">
          <div class="card-header">DISTRIBUTION</div>
          <div class="card-body">
            <div class="row">
              <div class="col-sm-12">
                {{reptile.distribution}}
              </div>
            </div>
          </div>
        </div>
        <!-- Side widget-->
        <div class="card mb-4">
          <div class="card-header">ECOSYSTEM/HABITAT</div>
          <div class="card-body">{{reptile.habitat}}</div>
        </div>
        <div class="card mb-4">
          <div class="card-header"> FEEDING HABITS</div>
          <div class="card-body">{{reptile.feedinghabits}}</div>
        </div>
        <div class="card mb-4">
          <div class="card-header">TAXONOMY</div>
          <div class="card-body">{{reptile.taxonomy}}</div>
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
    props: ['id'],
  data() {
    return {
      reptile: null,
    };
  },
  mounted() {
    fetch("https://mullins-marine-api.herokuapp.com/reptile/" + this.id  ,{
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.reptile = json;
      })
      .catch((err) => {
        alert(console.log(err));
      });
  },
};
</script>

<style>
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
}</style>