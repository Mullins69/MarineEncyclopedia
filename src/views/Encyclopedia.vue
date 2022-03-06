<template>
  <section id="Encyclopedia">
    <div class="container">
      <div class="row toprow">
        <div class="col-12 topcol">
          <h1>Marine Life Encyclopedia</h1>
        </div>
        <div class="col-3"></div>
        <div class="col-6">
          <p class="para">
            Explore the Marine Life Encyclopedia to learn fun facts and more
            about your favorite marine animals. From sharks and sea turtles to
            ecosystems and corals, you’re in the right place to take a deep dive
            into life under the sea.
          </p>
        </div>
        <div class="col-3"></div>
      </div>
      <div class="row">
        <router-link to="Cephalopods" class="col-12 col-sm-12 col-md-12 col-lg-6 cephalopods enchover">
          <h2>CEPHALOPODS, CRUSTACEANS & OTHER SHELLFISH</h2>
        </router-link>
        <router-link to="Corals" class="col-12 col-sm-12 col-lg-6 corals enchover">
          <h2>CORALS AND OTHER INVERTEBRATES</h2>
        </router-link>
      </div>
      <div class="row">
        <router-link to="Mammals" class="col-12 col-sm-12 col-lg-6 mammals enchover">
          <h2>MARINE MAMMALS</h2>
        </router-link>
        <router-link to="ScienceAndEcosystems" class="col-12 col-sm-12 col-lg-6 ecosystems enchover">
          <h2>MARINE SCIENCE AND ECOSYSTEMS</h2>
        </router-link>
      </div>
      <div class="row">
        <router-link to="Fishes" class="col-12 col-sm-12 col-lg-6 fishes enchover">
          <h2>OCEAN FISHES</h2>
        </router-link>
        <router-link to="TurtlesAndReptiles" class="col-12 col-sm-12 col-lg-6 turtles enchover">
          <h2>SEA TURTLES & REPTILES</h2>
        </router-link>
      </div>
      <div class="row">
        <router-link to="Seabirds" class="col-12 col-sm-12 col-lg-6 seabirds enchover">
          <h2>SEABIRDS</h2>
        </router-link>
        <router-link to="SharkAndRays" class="col-12 col-sm-12 col-lg-6 sharks enchover">
          <h2>SHARKS & RAYS</h2>
        </router-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style scoped>
.cephalopods {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),url("../assets/encyclopediaimg/cephalopods/cephalopods.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.corals {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/corals/coral.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.mammals {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/marinemammals/marinemammals.jpg");

  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.ecosystems {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/ecosystems/ecosystems.jpg");

  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.fishes {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/fish/fishes_alt.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.turtles {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/seaturtlesandreptiles/seaturtlesandreptiles.jpg");

  background-repeat: no-repeat;
  background-size: cover;
}
.seabirds {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/seabirds/seabirds.jpg");

  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.sharks {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("../assets/encyclopediaimg/sharksandrays/sharks_0.jpg");

  background-repeat: no-repeat;
  background-size: cover;
  min-height: 500px;
  background-position: center;
}
.cephalopods,
.corals,
.mammals,
.ecosystems,
.fishes,
.turtles,
.seabirds,
.sharks {
  text-decoration: none;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.enchover:hover {
  cursor: pointer;
  filter: blur(1px) brightness(90%);
  transition: all 250ms ease-in-out;
}

@media (min-width: 1200px) {
  .container {
    max-width: 100%;
  }
  .topcol {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
}
</style>