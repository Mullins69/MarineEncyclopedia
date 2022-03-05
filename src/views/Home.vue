<template>
  <section class="Home">
   <video autoplay muted loop id="myVideo">
  <source src="../assets/MessyViciousArchaeocete.mp4" type="video/mp4">
</video>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1>Marine Life Encyclopedia</h1>
        <p>Explore the Marine Life Encyclopedia to learn fun facts and more about your favorite marine animals. From sharks and sea turtles to ecosystems and corals, you’re in the right place to take a deep dive into life under the sea.</p>
        <button class="button">Encyclopedia</button>
        <button class="button">Shop</button>
      </div>
    </div>
  </div> 
  </section>
</template>

<script>


export default {
  name: 'Home',
  components: {

  }
}
</script>

<style scoped>
.button{
  margin-left: 30px;
}
.container{
  color: white;
   position: absolute;
   text-align: center;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, -50%);
    z-index: -1;
}
.Home{


}
#myVideo {
  z-index: -1000;
  position: absolute;
  right: 0;
  bottom: 0;
  min-width: 100%;
  min-height: 100%;
}
</style>