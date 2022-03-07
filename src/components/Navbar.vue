<template>
  <nav class="navbar navbar-expand-lg  ">
  <div class="container-fluid">
    <a class="navbar-brand" href="#"><img class="logo" src="../assets/logo.png" alt=""></a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="About">About</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="Encyclopedia">Encyclopedia</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="Shop">Shop</router-link>
        </li>
        <li class="nav-item">
           <router-link class="nav-link" to="Support">Support</router-link>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
      <ul class="navbar-nav dr mb-2 mb-lg-0">
         <li class="nav-item">
          <div class="nav-link"  data-bs-toggle="modal" data-bs-target="#mullinsModal">Login</div>
        </li>
          <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            <i class="bi bi-person-circle"></i>
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Profile</a></li>
            <li><a class="dropdown-item" href="#">Logout</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
<!-- Modal -->
<div class="modal fade" id="mullinsModal" tabindex="-1" aria-labelledby="mullinsModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-body">
        <Login/>
      </div>
    </div>
  </div>
</div>
</template>

<script>
  import Login from './Login.vue'

export default {


  components: {
    Login
  }
}
</script>

<style scoped>

.dr{
  margin-right: auto;
  margin-left: auto;
}
.navbar{
  background-color: #003459 ;
  position: sticky;
  top: 0;
  z-index: 1000;
}
.logo{
  height: 50px;
}
.nav-link {

  margin-left: 10%;
  color: white;

}

</style>