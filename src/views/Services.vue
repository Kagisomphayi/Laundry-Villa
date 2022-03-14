<template>
  <!-- projects section -->
  <section id="services" class="services">
    <div class="about-title">
      <div class="container text-center">
        <p class="text-white p-2">Prices</p>
      </div>
    </div>
    <div class="container">
      <div class="pb-5 cont justify-content-center">
        <!-- SORT/FILTER/ADD -->
        <div >
          <div class="sort">
            <div style="display: flex; justify-content: center" class="sort-content">
              <div>
                <h6 class="mb-0">SortByPrice:</h6>
                <select
                  class="form-select text-center"
                  name=""
                  id="sortPrice"
                  onchange="sortPrice()"
                >
                  <option value="ascending">Ascending</option>
                  <option value="descending">Descending</option>
                </select>
              </div>
              <div>
                <select
                  class="form-select text-center"
                  name=""
                  id="sortTitle"
                  onchange="sortTitle()"
                >
                  <option value="ascending">Ascending</option>
                  <option value="descending">Descending</option>
                </select>
              </div>
              <h6>SortByTitle:</h6>
            </div>
          </div>
        </div>
        <!-- CARDS -->
        <ProductCard />
      </div>
      <!-- <div class="loading" v-else></div> -->
    </div>
  </section>
</template>

<script>
// import ProductCard from "../components/ProductCard";
export default {
  components: {
    // ProductCard
  },
  methods: {
    // ADD TO CART(not done)
    addToCart(index) {
      this.cart.push(index);
    },
    addToCart() {
      fetch("", {
        method: "POST",
        body: JSON.stringify({
          name: "Yellow Butter Cake",
          cost: "",
          image: 1,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((res) => {
          if (res.status == 201) {
            swal({
              text: "Product added in cart",
              icon: "success",
            });
          }
        })
        .catch((err) => console.log("err", err));
    },
    // CREATE PRODUCT(done)
    createProduct() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://groupapibackend.herokuapp.com/products", {
        method: "POST",
        body: JSON.stringify({
          product_name: this.product_name,
          product_price: this.product_price,
          product_image: this.product_image,
          product_category: this.product_category,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style scoped>
.about-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  position: fixed;
  top: 140px !important;
}
.services {
  padding-top: 180px;
}
.loading {
  margin-top: 20%;
  justify-content: center;
}
.loading {
  border: 16px solid #f3f3f3;
  position: fixed;
  top: 5%;
  left: 50%;
  border-radius: 50%;
  border-top: 16px solid #000000;
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite; /* Safari */
  animation: spin 2s linear infinite;
}
@-webkit-keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
  }
}
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.button-body {
  background: rgb(255 212 0);
  border: 0;
  margin-top: 20px;
  color: rgb(0, 0, 0);
  border-radius: 10px;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
  background: #000000;
}
.sub:hover {
  color: rgb(255, 255, 255) !important;
}
.sub {
  color: rgb(0, 0, 0);
}
.sort-content {
  padding: 30px 5px 20px 5px;
}
.sort {
  background-color: white;
  width: 50%;
  border-radius: 15px;
  margin-bottom: 30px;
}
.products {
  padding-top: 50px;
}
.card {
  border-radius: 10px;
}
.subtitlee {
  margin-top: 70px;
}
.containe {
  justify-content: center !important;
}
@media all and (max-width: 991px) {
  .sort {
    width: 60%;
    margin-top: 70px;
  }
}
@media all and (max-width: 768px) {
  .sort {
    width: 70%;
    margin-top: 70px;
  }
  .loading {
    border: 16px solid #f3f3f3;
    position: fixed;
    top: 30%;
    left: 32%;
    border-radius: 50%;
    border-top: 16px solid #000000;
    width: 120px;
    height: 120px;
    -webkit-animation: spin 2s linear infinite; /* Safari */
    animation: spin 2s linear infinite;
  }
}
@media all and (max-width: 576px) {
  .sort {
    width: 80%;
    margin-top: 70px;
  }
}
@media all and (max-width: 400px) {
}
</style>
