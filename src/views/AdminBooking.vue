<template>
  <div class="price-title">
    <div class="container text-center">
      <ul class=" nav-links">
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="" to="/admin/services"
            >Services</router-link
          ></a
        >

        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="" to="/admin/users"
            >Users</router-link
          ></a
        >
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="" to="/admin/adminbookings"
            >bookings</router-link
          ></a
        >
      </ul>

    </div>
  </div>
  <!-- SORT/FILTER/ADD -->
  <div v-if="admin" class="">
    <div class=" container text-center">
      <div style="" class="sort-content justify-content-center row">
        <div class="col-5 col-lg-4 col-md-6 col-8 " id="main">
          
          
            <input placeholder="Search booking" type="text" v-model="search" />
         
          <!-- <div v-for="customer in filteredCustomers">
                  <span>{{ customer.firstName }} {{ customer.lastName }}</span>
                </div> -->
        </div>
      </div>
    </div>
 


  <div v-if="admin" class="container">
          <div class="mt-5 text-center">
        <h5 class="">Bookings</h5> 
      </div>
    <div v-if="bookings" class="pb-5 cont justify-content-center">
      <div class="row col-lg-12 proji" style="row-gap: 30px">
        <div
          v-for="booking in filteredBookings"
          :key="booking._id"
          class="col-lg-3 col-sm-6 col-6 col-md-4"
          style="display: flex; justify-content: center"
        >
          <div class="card shadow" style="width: 18rem">
            <ul class="list-group list-group-flush">
              <li class="list-group-item">
                <b>User name: </b> {{ booking.username }}
              </li>
              <li class="list-group-item">
                <b>Email: </b> {{ booking.email }}
              </li>
              <li class="list-group-item">
                <b>Phone number: </b> {{ booking.phone }}
              </li>
              <li class="list-group-item">
                <b>Service: </b> {{ booking.service }}
              </li>
              <li class="list-group-item">
                <b>Amount: </b> {{ booking.amount }}
              </li>
              <li class="list-group-item"><b>Date: </b>{{ booking.date }}</li>
              <li class="list-group-item"><b>Time: </b> {{ booking.time }}</li>
            </ul>
            <button
              type="button"
              class="btn card-btn"
              @click.prevent="deleteBooking(booking._id)"
            >
              <i class="bi bi-trash3"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-else class="loaderDiv">
      <div class="loader-"></div>
    </div>
  </div>
   </div>
  <div class="load" v-else>
  <div class="loading" > ONLY ADMIN IS ALLOWED TO VIEW ALL BOOKINGS. LOG-IN AS AN ADMIN!!!</div>
</div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      bookings: null,
      search: "",
      admin: false
    };
  },
  // GETTING USERS
  mounted() {
    this.user = this.$route.params;

    if (localStorage.getItem("Admin") === "true") {
      this.admin = true;
    }

    if (localStorage.getItem("jwt")) {
      fetch("https://laundry-villa.herokuapp.com/users", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      });
      console.log("after");
      fetch("https://laundry-villa.herokuapp.com/book", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          console.log("after");
          console.log(json);
          this.bookings = json;
        })
        .catch((err) => {
          console.log(err);
        });
      fetch("https://laundry-villa.herokuapp.com/users", {
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
    } else {
      alert("Login");
      this.$router.push({ name: "Admin" });
    }
  },
  methods: {
    // DELETE PRODUCT(done)
    deleteBooking(id) {
      const config = {
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      };
      let apiURL = `https://laundry-villa.herokuapp.com/book/${id}`;
      let indexOfArrayItem = this.bookings.findIndex((i) => i._id === id);
      if (window.confirm("Do you really want to delete?")) {
        axios
          .delete(apiURL, config)
          .then(() => {
            this.bookings.splice(indexOfArrayItem, 1);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
  computed: {
    filteredBookings: function () {
      return this.bookings.filter((booking) => {
        return booking.username.match(this.search);
      });
    },
  },
};
</script>

<style scoped>
.load {
  height: 100vh;
  justify-content: center;
  display: flex;
  align-items: center;
}
.sort-content {
  padding: 30px 5px 20px 5px;
  /* display: flex; 
  flex-wrap: wrap !important; */
  margin-top: 150px;
}
input {
  width: 100% !important;
}
#nav a.router-link-exact-active {
  color: rgba(23, 83, 139, 0.924);
}
.content {
  padding-top: 20px;
}
.nav-link {
  display: inline;
}

h5 {
  color: rgba(10, 81, 139, 0.979);
}
.price-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  z-index: 100;
  position: fixed;
  top: 110px;
}
a {
  text-decoration-line: none;
  color: white;
}
.loaderDiv {
  height: 100vh;
}
.loader {
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
.cont {
  padding-top: 15px;
}
.a:hover{
  color:rgba(36, 53, 128, 0.924) !important;
}
</style>
