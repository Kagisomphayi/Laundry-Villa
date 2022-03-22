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
                ><router-link to="/faqs">About</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate p-0 m-2"
                ><router-link to="/contact">Contact</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate py-2" href="#spy3"
                ><router-link to="/confirm">Bookings</router-link></a
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
      <div class="dropdown mt-3 justify-content-right">
        <ul class="navbar-nav bg-light m-0 ml-lg-auto p-3 p-lg-0">
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/">Home</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/service">Service Prices</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/faqs">About</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/contact">Contact</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/login">Login</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate"
              ><router-link to="/register">Register</router-link></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate" href="#spy3"
              ><router-link to="/confirm">Bookings</router-link></a
            >
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
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
  width: 70px;
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
