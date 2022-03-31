<template>
  <!-- main bar -->
  <div class="">
    <nav
      class="navbar border-bottom navbar-expand-lg navbar-light bg-light fixed-top"
    >
      <div class="container">
        <div>
          <a class="navbar-brand" href="#"
            ><img class="logo" src="../assets/Logo.png" alt="logo"
          /></a>
        </div>

        <button
          class="btn btn-primary offie"
          type="button"
          data-bs-toggle="offcanvas"
          data-bs-target="#offcanvasExample"
          aria-controls="offcanvasExample"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse justify-content-end" id="nav">
          <ul class="navbar-nav bg-light m-0 ml-lg-auto p-3 p-lg-0">
            <li class="d-inline d-lg-none">
              <button
                data-toggle="collapse"
                data-target="#nav"
                class="close float-right"
              >
                &times;
              </button>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/">Home</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/service">Service Prices</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/about">About</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/contact">Contact</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate"
                ><router-link class="p-2 m-0 login" to="/login"
                  >Login</router-link
                ></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate"
                ><router-link class="p-2 mx-2 register" to="/register"
                  >Register</router-link
                ></a
              >
            </li>
          </ul>
          <div class="dropdown">
            <button class="dropbtn">Profile</button>
            <div class="dropdown-content">
              
                <router-link class="profile" to="Profile"
                  ><i class="bi bi-person-circle"></i>Profile</router-link
                >
            
              
                <router-link v-on:click="logout" to="Login"><i class="bi bi-box-arrow-left"></i>Logout</router-link>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <!-- offie -->

  <div
    class="offcanvas offcanvas-start"
    tabindex="-1"
    id="offcanvasExample"
    aria-labelledby="offcanvasExampleLabel"
  >
    <div class="offcanvas-header">
      <h5 class="offcanvas-title" id="offcanvasExampleLabel">Offcanvas</h5>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body">
      <div class="dropdown mt-3 justify-content-start">
        <ul class="navbar-nav bg-light m-0 ml-lg-auto p-3 p-lg-0">

            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/">Home</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/service">Service Prices</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/about">About</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/contact">Contact</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate"
                ><router-link class="p-0 m-2 " to="/login"
                  >Login</router-link
                ></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate"
                ><router-link class=" p-0 m-2 " to="/register"
                  >Register</router-link
                ></a
              >
            </li>
            
        </ul>

      </div>
                        <div class="dropdown">
            <button class="dropbtn">Profile</button>
            <div class="dropdown-content">
              
                <router-link class="profile" to="Profile"
                  ><i class="bi bi-person-circle"></i>Profile</router-link
                >
            
              
                <router-link v-on:click="logout" to="Login"><i class="bi bi-box-arrow-left"></i>Logout</router-link>
            </div>
          </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style scoped>
.offcanvas-start{
  width: 70%;
}
.dropbtn {
  background-color: #ffffff;
  color: rgba(10, 81, 139, 0.979);
  padding: 16px;
  font-size: 16px;
  border: none;
  font-weight: bold;
}
.dropbtn:hover {
  background-color: #ffffff;
  color: rgba(255, 255, 255, 0.979);
  padding: 16px;
  font-size: 16px;
  border: none;
  font: bolder;
}
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {
  background-color: #ddd;
}

.dropdown:hover .dropdown-content {
  display: block;
}

.dropdown:hover .dropbtn {
  background-color: rgba(10, 81, 139, 0.979);
}

.login,
.register {
  border: solid 2px rgba(10, 81, 139, 0.979);
}
a {
  text-decoration-line: none;
}
body {
  padding-top: 55px;
}
.logo {
  width: 55px;
  border: solid 1px;
  border-radius: 100%;
}
nav {
  background-color: rgb(255, 255, 255) !important;
  position: fixed;
  top: 40px;
  height: 70px;
}
/* #nav{
  padding: 0;
} */
.offie {
  display: none;
}
/* mobile navbar sidebar under lg breakpoint */
@media (max-width: 992px) {
  .offie {
    display: initial;
  }
  .navbar-collapse.collapsing .navbar-nav {
    display: block;
    position: fixed;
    top: 0;
    bottom: 0;
    left: -45%;
    transition: all 0.2s ease;
  }
  .nav-link {
    padding: 0px !important;
  }

  .navbar-collapse.show .navbar-nav {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    flex-direction: column;
    height: auto;
    width: 45%;
    transition: left 0.35s ease;
    box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.15);
  }
}
@media all and (max-width: 576px) {
  nav {
    height: 70px;
  }
}
</style>
