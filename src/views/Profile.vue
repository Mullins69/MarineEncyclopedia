<template>

  <div class="container rounded bg-white mt-5 mb-5 text-center" v-if="users">
    <div class="row">
      <div class="col-md-3 border-right">
        <div class="d-flex flex-column align-items-center text-center p-3 py-5">
          <img
            class="rounded-circle mt-5"
            
            src="https://mpchsschool.in/wp-content/uploads/2019/10/default-profile-picture.png"
          /><span class="font-weight-bold">{{ users.fullname }}</span
          ><span class="text-black-50">{{ users.email }}</span
          ><span> </span>
        </div>
      </div>
      <div class="col-md-5 border-right">
        <div class="p-3 py-5">
          <div class="d-flex justify-content-between align-items-center mb-3">
            <h4 class="text-right">Profile & Shipping Address</h4>
          </div>
          <div class="row mt-2">
            <table class="table table-user-information">
                    <tbody>
                      <tr>
                        <td>Name:</td>
                        <td>{{users.fullname}}</td>
                      </tr>
                      <tr>
                        <td>Email:</td>
                        <td>{{users.email}}</td>
                      </tr>
                      <tr>
                        <td>Shipping Address:</td>
                        <td>{{users.street}}<br><br>
                        {{users.city}}<br><br>
                        {{users.zipcode}}<br><br>
                        {{users.country}}
                        </td>
                      </tr>
                      <tr>
                        <td>Phone:</td>
                        <td>{{users.phone_number}}
                        </td>
                           
                      </tr>

                     
                    </tbody>
                  </table>
          </div>

          <div class="mt-5 text-center">
            <button
              data-bs-toggle="modal"
              data-bs-target="#editUser"
              class="btn btn-primary profilebtn"
              type="button"
            >
              Edit
            </button>
          </div>
          <div class="mt-5 text-center">
            <button
              class="btn btn-danger profile-button"
              type="button"
              @click="deleteUser"
            >
              Destroy User
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- Modal -->
  <div
    class="modal fade"
    id="editUser"
    tabindex="-1"
    aria-labelledby="editUserLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-body">
          <ProfileEdit />
        </div>
      </div>
    </div>
  </div>
  <!-- Modal -->
</template>

<script>
import ProfileEdit from "../views/ProfileEdit.vue";
export default {
  components: {
    ProfileEdit,
  },
  data() {
    return {
      users: null,
    };
  },
  methods: {
    deleteUser() {
      if (confirm("Do you really want to delete your profile?")) {
        if (!localStorage.getItem("jwt")) {
          alert("User not logged in");
          return this.$router.push({ name: "Login" });
        }
        fetch("https://mullins-marine-api.herokuapp.com/users", {
          method: "DELETE",
          headers: {
            "Content-type": "application/json; charset=UTF-8",
            Authorization: `Bearer ${localStorage.getItem("jwt")}`,
          },
        })
          .then((response) => response.json())
          .then((json) => {
            alert("DELETED USER");
            localStorage.clear();
            return this.$router.push({ name: "Home" });
          })
          .catch((err) => {
            alert(err);
          });
      }
    },
    forceRerender() {
      // Removing my-component from the DOM
      this.renderComponent = false;

      this.$nextTick(() => {
        // Adding the component back in
        this.renderComponent = true;
      });
    },
  },
  mounted() {
    if (!localStorage.getItem("jwt")) {
      alert("User not logged in");
      return this.$router.push({ name: "Home" });
    }
    fetch("https://mullins-marine-api.herokuapp.com/users/oneuser/", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
        Authorization: `Bearer ${localStorage.getItem("jwt")}`,
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.users = json;
      })
      .catch((err) => {
        alert(err);
      });
  },
};
</script>

<style scoped>
.form-control:focus {
  box-shadow: none;
  border-color: #222222;
}

.profilebtn {
  background: rgb(0, 0, 0);
  box-shadow: none;
  border: none;
}

.profile-button:hover {
  background: #222222;
}

.profile-button:active {
  background: red;
  box-shadow: none;
}

.back:hover {
  color: #003459;
  cursor: pointer;
}

.labels {
  font-size: 11px;
}
.rounded-circle{
  height: 300px;
}

.add-experience:hover {
  background: #222222;
  color: #fff;
  cursor: pointer;
  border: solid 1px #111111;
}
</style>