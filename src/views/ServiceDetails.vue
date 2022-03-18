<template>
  <div class="container">
    <div class="service-detail">
      <div v-if="service" class="card" style="width: 50rem">
        <div class="card-body">
          <h4 class="card-title text-black">
            <img
              :src="service.service_image"
              class="card-img-top"
              alt="Service"
            />
            {{ service.laundry_service }}
          </h4>
          <p class="card-text text-black">R{{ service.service_price }}</p>
        </div>
        <div class="card-body card-body-button text-center">
          <button
            type="button"
            class="btn border-dark card-btn"
            @click="addToBookings(index)"
          >
            <i class="bi mx-1 bi-pen"></i>BOOK!
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      service: null,
    };
  },
  mounted() {
    fetch("https://laundry-villa.herokuapp.com/services/" + this.id, {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.service = json;
      })
      .catch((err) => {
        alert(console.log(err));
      });
  },
};
</script>

<style>
.service-detail {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
a{
  text-decoration: none;
}
.card-img-top {
  border-radius: 10px;
  height: 400px;
  object-fit: cover;
}
</style>
