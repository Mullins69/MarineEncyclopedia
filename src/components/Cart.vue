<template>
<h3>Your Cart</h3>
<main id="cart">
  <div class="container-fluid" v-if="cart"> 
    <div class="row ">
      <div class="col-12 col-sm-8 items">
        <!--1-->
        <div class="cartItem row" v-for="carts of cart" :key="carts._id">
          <div class="col-3 mb-2">
            <img class="w-100" :src="carts.img" alt="art image">
          </div>
          <div class="col-5 mb-2">
            <h6 class=""></h6>
    
            <p class="pl-1 mb-0">Item: {{carts.title}}</p>
          </div>
          <div class="col-2" >
            <p class="cartItemQuantity p-1 text-center">Quantity: {{carts.quantity.quantity}}</p>
          </div>
          <div class="col-4">
            <p id="cartItem1Price">PRICE: R{{carts.price}}</p>
             <button @click="deleteCart(carts._id)">Remove</button>
          </div>

        </div>
        <hr>

        <a href="#"><button id="btn-checkout" class="shopnow"><span>Checkout</span></button></a>
      </div>
    </div>
  </div>
  
</main>
</template>

<script>
export default {
  data(){
    return {
      cart: null,
    }
  },
  methods: {
   },
  mounted(){
    if (!localStorage.getItem("jwt")) {
        alert("Please Create Account First");
        return this.$router.push({ name: "Shop" });
      }
      else{
    fetch("https://mullins-marine-api.herokuapp.com/users/cart", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.cart = json 
            
          })
        .catch((err) => {
          alert(err);
        });
  }
  }
}
</script>

<style scoped>


</style>
