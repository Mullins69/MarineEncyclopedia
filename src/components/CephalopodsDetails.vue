<template>
<div class="container mt-4" v-if="cephalopods">
  <div class="row">
    <div class="col text-center">
      <h1>
        {{cephalopods.title}}
      </h1>
    </div>
  </div>
     <div class="row">
      <!-- Blog entries-->
      <div class="col-lg-8">
        <!-- Featured blog post-->
        <div class="card mb-4">
          <a href="#!"><img class="card-img-top" :src="cephalopods.img" alt="..." /></a>
          <div class="card-body">
            <p class="card-text">{{cephalopods.description}}</p>
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
                {{cephalopods.distribution}}
              </div>
            </div>
          </div>
        </div>
        <!-- Side widget-->
        <div class="card mb-4">
          <div class="card-header">ECOSYSTEM/HABITAT</div>
          <div class="card-body">{{cephalopods.habitat}}</div>
        </div>
        <div class="card mb-4">
          <div class="card-header"> FEEDING HABITS</div>
          <div class="card-body">{{cephalopods.feedinghabits}}</div>
        </div>
        <div class="card mb-4">
          <div class="card-header">TAXONOMY</div>
          <div class="card-body">{{cephalopods.taxonomy}}</div>
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
    props: ['id'],
  data() {
    return {
      cephalopods: null,
    };
  },
  mounted() {
    fetch("https://mullins-marine-api.herokuapp.com/cephalopod/" + this.id  ,{
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.cephalopods = json;
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
</style>