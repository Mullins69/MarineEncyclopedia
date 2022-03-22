<template>
  <div class="container">
    <h1>Admin Dashboard</h1>
    <div class="row">
      <div class="col">
        <h2>All users:</h2>
      </div>
    </div>
    <div class="row">
      <div
        class="col-12 col-md-4 col-lg-4"
        v-for="user of users"
        :key="user._id"
      >
        <p>
          <span>Is Admin: {{ user.isadmin }}</span>
          <br />
          <span>name :</span> {{ user.fullname }}
          <br />
          <span>email :</span> {{ user.email }}
          <br />
          <span>contact :</span> {{ user.phone_number }}
          <br />
          <span>Street Address :</span> {{ user.street }}
          <br />
          <span>City :</span> {{ user.city }}
          <br />
          <span>Zipcode :</span> {{ user.zipcode }}
          <br />
          <span>Country :</span> {{ user.country }}
          <br />
        </p>
      </div>
    </div>
    <div class="row">
      <h1>All Products</h1>
      <button class="btn btn-primary">Create Product</button>
      <div class="row">
        <div class="col-4">
          <select
            v-model="selected"
            class="form-select"
            aria-label="Default select example"
          >
            <option selected value="">Display All</option>
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
      <div
        class="col-12 col-md-4 col-lg-4"
        v-for="products of filterProducts"
        :key="products._id"
      >
        <div class="card py-4 px-lg-5 h-100">
          <div class="card-body d-flex flex-column">
            <div class="text-center">
              <img :src="products.img" class="img-fluid mb-5" alt="Websearch" />
            </div>

            <h2 class="card-title mb-4 text-center">{{ products.title }}</h2>
            <div class="pricing">
              <ul class="list-unstyled">
                <li class="mb-3">
                  <span class="small ms-3">{{ products.description }}</span>
                </li>
              </ul>
            </div>
            <div class="text-center mt-auto mb-4">
              <span class="fw-bold fs-2">R{{ products.price }}</span>
            </div>
            <div class="text-center">
              <div>
                <router-link
                  class="btn btn-warning"
                  :to="{ name: 'EditProduct', params: { id: products._id } }"
                >
                  Edit product
                </router-link>
                <button
                  type="button"
                  class="btn btn-danger"
                  @click="deleteProduct(products._id)"
                >
                  Delete product
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: null,
      product: null,
      search: "",
      selected: "",
    };
  },
  methods: {
    deleteProduct(id) {
      if (confirm("Do you really want to delete this product?")) {
        if (this.isadmin == true) {
          fetch("https://mullins-marine-api.herokuapp.com/product/" + id, {
            method: "DELETE",
            headers: {
              "Content-type": "application/json; charset=UTF-8",
              Authorization: `Bearer ${localStorage.getItem("jwt")}`,
            },
          })
            .then((response) => response.json())
            .then((json) => {
              alert("DELETED PRODUCT");
              location.reload();
            })
            .catch((err) => {
              alert(err);
            });
        }
      }
    },
  },
  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://mullins-marine-api.herokuapp.com/users/oneuser/", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          let isadmin = json.isadmin;
          if (isadmin == true) {
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
                alert(err);
                console.log(err);
              });
            fetch("https://mullins-marine-api.herokuapp.com/users/", {
              method: "GET",
              headers: {
                "Content-type": "application/json; charset=UTF-8",
              },
            })
              .then((response) => response.json())
              .then((json) => {
                this.users = json;
              })
              .catch((err) => {
                alert(err);
              });
          }
          if (isadmin == false) {
            alert("You are Not ADMIN");
            this.$router.push({ name: "Home" });
          }
        })
        .catch((err) => {
          alert(err);
        });
    }
    else{
      alert("Please Login")
      this.$router.push({ name: "Home" });
    }
  },
  computed: {
    filterProducts: function () {
      if (this.product) {
        let filtered = this.product;
        if (this.selected == "") {
          filtered = filtered.filter((product) => {
            return product.category.match(this.selected);
          });
          if (this.search) {
            filtered = filtered.filter((product) => {
              return product.title.match(this.search);
            });
          }
          return filtered;
        }
        if (this.selected) {
          filtered = filtered.filter((product) => {
            return product.category.match(this.selected);
          });
          if (this.search) {
            filtered = filtered.filter((product) => {
              return product.title.match(this.search);
            });
          }
          return filtered;
        }
      }
    },
  },
};
</script>

<style scoped>
</style>