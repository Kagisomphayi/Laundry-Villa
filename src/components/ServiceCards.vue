<template>
  <section id="products" class="products">
    <div class="container">
      <div v-if="services" class="pb-5 cont justify-content-center">
        <div class="row col-lg-12 proji" style="row-gap: 30px">
          <div
            v-for="service in services"
            :key="service._id"
            class="col-lg-3 col-md-6"
            style="display: flex; justify-content: center"
          >
            <div class="card shadow ani-card" style="width: 18rem">
              <img
                :src="service.service_image"
                class="card-img-top"
                alt="..."
              />
              <div class="card-body">
                <h4 class="card-title text-black">
                  {{ service.laundry_service }}
                </h4>
                <p class="card-text text-black">R{{ service.service_price }}</p>
              </div>

              <div class="card-body text-center">
                <button
                  type="button"
                  class="btn mx-2 border-dark card-btn"
                  @click="addToBookings(index)"
                >
                  <i class="bi mx-1 bi-pen"></i>BOOK!
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="loading" v-else></div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      services: null,
    };
  },
  // GETTING SERVICES
  mounted() {
    fetch("https://laundry-villa.herokuapp.com/services")
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        this.services = data;
      });
  },
  methods: {

  },
};
</script>

<style>
.card-img-top {
  border-radius: 10px;
  height: 200px;
  object-fit: cover;
}
</style>