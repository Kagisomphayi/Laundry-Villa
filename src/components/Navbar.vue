<template>
  <!-- main bar -->
  <div class="">
    <nav class="navbar border-bottom navbar-expand-lg navbar-light bg-light fixed-top">
      <div class=" container">
        <a class="navbar-brand" href="#">Laundry Villa</a>
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
              <a class="nav-link text-truncate" href="#spy0"><router-link to="/">Home</router-link></a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate" href="#spy1"><router-link to="/about">About</router-link></a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate" href="#spy2">FAQs</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate" href="##">Contact</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate" href="#spy3">Login</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-truncate" href="#spy3">Register</a>
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
            <a class="nav-link text-truncate" href="#spy0">Link</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate" href="#spy1">Morelink</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate" href="#spy2">Another link</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate" href="#spy3">Link</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-truncate" href="##">Link</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <div class="container-fluid py-2">
    <p>
      And then there is page content here. Narrow the viewport to see the
      toggler.
    </p>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
a{
  text-decoration-line: none;
}
body {
  padding-top: 55px;
}
nav {
  background-color: rgb(255, 255, 255) !important;
  position: fixed;
  top: 40px;
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
</style>
