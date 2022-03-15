<template>
  <div class="home">
    <div
      id="carouselExampleCaptions"
      class="carousel slide"
      data-bs-ride="carousel"
    >
      <div class="carousel-inner justity-content-center">
        <div class="but-cont">
          <div class="container button-div">
            <h1 class="display-1 title text-bold mb-5">Laundry Villa</h1>
            <p>Login to make a booking</p>
            <button type="button" class="btn btn-primary">Primary</button>
          </div>
        </div>
        <div class="carousel-item active">
          <img
            src="https://cdn.pixabay.com/photo/2018/08/10/16/44/laundry-mat-3597216_960_720.jpg"
            class="d-block w-100"
            alt="..."
          />
        </div>
        <div class="carousel-item">
          <img
            src="https://images.unsplash.com/photo-1545173168-9f1947eebb7f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1471&q=80"
            class="d-block w-100"
            alt="..."
          />
        </div>
        <div class="carousel-item">
          <img
            src="https://images.unsplash.com/photo-1561053720-76cd73ff22c3?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80"
            class="d-block w-100"
            alt="..."
          />
        </div>
      </div>

      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselExampleCaptions"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselExampleCaptions"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
  <section>
    <div class=" container  text-center">
    <h2 class="display-6 subtitle mt-5"><u>We Have The Best Services You Can Get</u> </h2>   
        <div class="instructions text-black">
      <div class="row  ">
        <div class="col-lg-4 col-sm-4 coL-md-3 ">
          <h5>Make A Booking</h5>
          <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Nam, esse? Officia ex, maiores praesentium eius velit ipsa quae distinctio quisquam quod illum, voluptatibus quam tempore nobis similique sequi molestiae accusantium.</p>
        </div>
        <div class="col col-lg-4 col-sm-4 coL-md-3 mx-">
          <h5>Drop Your Laundry</h5>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni eum impedit id voluptates laboriosam dicta numquam sit excepturi ipsa illo similique minus atque soluta aspernatur, explicabo vero deleniti odio accusantium?</p>
        </div>
        <div class="col col-lg-4 col-sm-4 coL-md-6">
          <h5>Collect Your Laundry</h5>
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quae similique dignissimos incidunt distinctio quos molestias accusantium sint veritatis, quisquam dolorem voluptatum magni itaque quo consequuntur error, libero, sequi dicta voluptatibus?
        </div>
      </div>
    </div>
    </div>

  </section>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>
<style scoped>
.d-block {
  height: 100vh;
  object-fit: cover;

}

.button-div {
  width: 100%;
  text-align: center !important;
}
.but-cont {
  width: 100%;
  position: absolute;
  z-index: 100;
}
.title {
  margin-top: 30%;
  color: rgba(10, 81, 139, 0.979);
}
.carousel-control-next,
.carousel-control-prev {
  z-index: 999;
}
.subtitle{
color: rgba(139, 102, 96, 0.924);;
letter-spacing: 1px;
}
.instructions {
  margin:100px 100px;
}
h5{
   color: rgba(10, 81, 139, 0.979);
}
/* RESPONSIVENESS */
@media all and (max-width: 992px) {
  .title {
    margin-top: 45%;
    color: rgba(10, 81, 139, 0.979);
  }
}
@media all and (max-width: 768px) {
  .title {
    margin-top: 55%;
    color: rgba(10, 81, 139, 0.979);
  }
}
@media all and (max-width: 500px) {
  .title {
    margin-top: 65%;
    color: rgba(10, 81, 139, 0.979);
  }
}
</style>
