<template>
<h3>Your Cart</h3>
<main id="cart">
  <div class="container-fluid" v-if="cart"> 
    <div class="row ">
      <div class="col-12 col-sm-8 items"  v-for="carts of cart" :key="carts._id">
        <!--1-->
        <div class="cartItem row" v-for="data of carts.cart" :key="data._id">
          <div class="col-3 mb-2">
            <img class="w-100" :src="data.img" alt="alt image">
          </div>
          <div class="col-5 mb-2">
            <h6 class=""></h6>
    
            <p class="pl-1 mb-0">Item: {{data.title}}</p>
          </div>
          <div class="col-2" >
            <p class="cartItemQuantity p-1 text-center">Quantity: {{data.quantity.quantity}} </p>
          </div>
          <div class="col-4">
            <p id="cartItem1Price">PRICE: R{{data.price}}</p>
             
          </div>

        </div>
        <hr>

        
        
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
    fetch("https://mullins-marine-api.herokuapp.com/cart/", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.cart = json;
          console.log(this.cart)
         
            
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
