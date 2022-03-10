<template>
  <form
    class="container rounded bg-white mb-5 text-center"
    @submit.prevent="register"
  >
    <div class="row">
      <div class="col-md-12 border-right">
        <div class="">
          <div class="d-flex justify-content-between align-items-center mb-3">
            <h4 class="text-right">Registration</h4>
          </div>
        </div>
      </div>
      <div class="row mt-2">
        <div class="col-md-12">
          <label class="labels">Name</label
          ><input type="text" class="form-control" v-model="name" required />
        </div>
      </div>
      <div class="row mt-3">
        <div class="col-md-12">
          <label class="labels">Email</label
          ><input type="text" class="form-control" v-model="email" required />
        </div>
        <div class="col-md-12">
          <label class="labels">Password</label
          ><input
            type="password"
            class="form-control"
            v-model="password"
            required
          />
        </div>

        <div class="col-md-12">
          <label class="labels">Mobile Number</label
          ><input
            type="text"
            class="form-control"
            v-model="phone_number"
            required
          />
        </div>
        <div class="col-md-12">
          <label class="labels">Street Address</label
          ><input type="text" class="form-control" v-model="street" required />
        </div>
        <div class="col-md-12">
          <label class="labels">Zipcode</label
          ><input type="text" class="form-control" v-model="zipcode" required />
        </div>
      </div>
      <div class="row mt-3">
        <div class="col-md-6">
          <label class="labels">Country</label
          ><input type="text" class="form-control" v-model="country" required />
        </div>
        <div class="col-md-6">
          <label class="labels">City/Region</label
          ><input type="text" class="form-control" v-model="city" required />
        </div>
      </div>
      <div class="mt-5 text-center">
        <button class="btn btn-primary profile-button" type="submit">
          Create Account
        </button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      phone_number: "",
      password: "",
      street: "",
      zipcode: "",
      country: "",
      city: "",
    };
  },
  methods: {
    register() {
      fetch("https://mullins-marine-api.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          fullname: this.name,
          email: this.email,
          phone_number: this.phone_number,
          password: this.password,
          street: this.street,
          zipcode: this.zipcode,
          country: this.country,
          city: this.city,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Profile" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style scoped>
.form-control:focus {
  box-shadow: none;
  border-color: #222222;
}

.profile-button {
  background: rgb(0, 0, 0);
  box-shadow: none;
  border: none;
}

.profile-button:hover {
  background: #222222;
}

.profile-button:focus {
  background: #682773;
  box-shadow: none;
}

.profile-button:active {
  background: #682773;
  box-shadow: none;
}

.back:hover {
  color: #682773;
  cursor: pointer;
}

.labels {
  font-size: 11px;
}

.add-experience:hover {
  background: #222222;
  color: #fff;
  cursor: pointer;
  border: solid 1px #111111;
}
</style>