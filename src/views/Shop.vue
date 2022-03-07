<template>
  <section id="shop">
      <button type="button" class="cart" data-bs-toggle="modal" data-bs-target="#exampleModal">
  Cart
</button>
    <div class="container" v-if="product">
      
      <div class="row">
        <div class="col">
          <h1>Shop</h1>
        </div>
      </div>
      <div class="row">
        <div class="col-4">
          <select class="form-select" aria-label="Default select example">
            <option selected>Filter</option>
            <option value="mask">Masks</option>
            <option value="wetsuits">Wetsuits</option>
            <option value="camera">Camera</option>
          </select>
        </div>
        <div class="col-4">
          <form class="d-flex">
            <input
              class="form-control me-2"
              type="text"
              v-model="search"
              placeholder="Search"
              aria-label="Search"
            />
          </form>
        </div>
        <div class="col-4"></div>
      </div>
      <div class="row">
          <div class="col-lg-4 col-md-6 mb-3" v-for="products of filterProducts" :key="products._id">
        <div class="card py-4 px-lg-5 h-100">
          <div class="card-body d-flex flex-column">
            <div class="text-center">
              <img :src="products.img" class="img-fluid  mb-5" alt="Websearch">
            </div>

            <h2 class="card-title mb-4 text-center ">{{products.title}}</h2>
            <div class="pricing">

                              <ul class="list-unstyled">
                <li class="mb-3">
                  <span class="small ms-3">{{products.description}}</span>
                </li>
              </ul>

            </div>
            <div class="text-center mt-auto mb-4">
              <span class="fw-bold fs-2 ">R{{products.price}}</span>
            </div>
            <div class="text-center"><button type="button" class="btn btncolor">Add to cart</button></div>

          </div>
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
  </section>
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    data(){
        return{
            product : null,
            search: "",
        }
    },
    mounted() {
      fetch("https://mullins-marine-api.herokuapp.com/product", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",

        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.product = json;
        })
        .catch((err) => {
          alert(console.log(err));
        });
  },
  computed:{
    filterProducts:function(){
      return this.product.filter((product) =>{
        return product.title.match(this.search)
      })
    }
  }
};
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

.cart {

  background-color: #003459;
  float: right;
  color: white;
  border-radius: 300px;
  border: none;
  width: 100px;
  height: 40px;


}

.cart:hover {
  transform: scale(1.1);
  color: white;
}
.container{
    text-align: center;
}
.img-fluid{
    height: 250px;
}


.btncolor{
  background-color: #003459;;
  border-radius: 55555px;
  padding: 1rem 2rem!important;
  color: #ffff;
  margin-bottom: 2rem;
  
}


.package{
  list-style-type: none;
}


.parent{
  height: 300px;
  display: flex;
  border:2px solid yellow;
}

.child{
  background-color: red;
  margin-bottom: auto;
  margin-left: auto;
  margin-right: auto;
  color: white;
}

.icon-color
{
  color:#1f38fa;

}
</style>