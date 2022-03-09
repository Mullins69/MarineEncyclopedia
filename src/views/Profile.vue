<template>
  <div class="container rounded bg-white mt-5 mb-5"  v-if="users">
    <div class="row">
        <div class="col-md-3 border-right">
            <div class="d-flex flex-column align-items-center text-center p-3 py-5"><img class="rounded-circle mt-5" width="150px" :src="users.img"><span class="font-weight-bold">{{users.fullname}}</span><span class="text-black-50">{{users.email}}</span><span> </span></div>
        </div>
        <div class="col-md-5 border-right">
            <div class="p-3 py-5">
                <div class="d-flex justify-content-between align-items-center mb-3">
                    <h4 class="text-right">Profile Settings</h4>
                </div>
                <div class="row mt-2">
                    <div class="col-md-6"><label class="labels">Name</label><input type="text" class="form-control" :placeholder="users.fullname" value=""></div>
                </div>
                <div class="row mt-3">
                    <div class="col-md-12"><label class="labels">Mobile Number</label><input type="text" class="form-control" :placeholder="users.phone_number" value=""></div>
                    <div class="col-md-12"><label class="labels">Street Address</label><input type="text" class="form-control" :placeholder="users.street" value=""></div>
                    <div class="col-md-12"><label class="labels">Zipcode</label><input type="text" class="form-control" :placeholder="users.zipcode" value=""></div>
                    <div class="col-md-12"><label class="labels">Email</label><input type="text" class="form-control" :placeholder="users.email" value=""></div>
                </div>
                <div class="row mt-3">
                    <div class="col-md-6"><label class="labels">Country</label><input type="text" class="form-control" :placeholder="users.country" value=""></div>
                    <div class="col-md-6"><label class="labels">City/Region</label><input type="text" class="form-control" value="" :placeholder="users.city"></div>
                </div>
                <div class="mt-5 text-center"><button data-bs-toggle="modal" data-bs-target="#editUser" class="btn btn-primary profile-button" type="button">Edit</button></div>
            </div>
        </div>
    </div>
</div>
<!-- Modal -->
<div class="modal fade" id="editUser" tabindex="-1" aria-labelledby="editUserLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-body">
        <ProfileEdit/>
      </div>
    </div>
  </div>
</div>
<!-- Modal -->
</template>

<script>
import ProfileEdit from "../views/ProfileEdit.vue"
export default {
  components: {
    ProfileEdit
  },
  data() {

    return {
      users: null,
      renderComponent: true,
      
    };
  },
methods: {
  deleteUser(){
    if(confirm("Do you really want to delete your profile?")){
            if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch('https://mullins-marine-api.herokuapp.com/users', {
      method: 'DELETE',
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("DELETED USER")
          localStorage.clear();
          return this.$router.push({ name: "Home" });
        })
        .catch((err) => {
          alert(err);
        });
            }},
  forceRerender() {
        // Removing my-component from the DOM
        this.renderComponent = false;

        this.$nextTick(() => {
          // Adding the component back in
          this.renderComponent = true;
        });
      }
    ,

  
    },
    mounted(){
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
          this.users = json
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
    border-color: #222222
}

.profile-button {
    background: rgb(0, 0, 0);
    box-shadow: none;
    border: none
}

.profile-button:hover {
    background: #222222
}

.profile-button:focus {
    background: #682773;
    box-shadow: none
}

.profile-button:active {
    background: #682773;
    box-shadow: none
}

.back:hover {
    color: #682773;
    cursor: pointer
}

.labels {
    font-size: 11px
}

.add-experience:hover {
    background: #222222;
    color: #fff;
    cursor: pointer;
    border: solid 1px #111111
}
</style>