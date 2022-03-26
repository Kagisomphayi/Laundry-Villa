<template>
  <div class="price-title">
    <div class="container text-center">
      <ul class="">
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/admin/services"
            >Services</router-link
          ></a
        >

        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/admin/users"
            >Users</router-link
          ></a
        >
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/admin/adminbookings"
            >bookings</router-link
          ></a
        >
      </ul>
    </div>
  </div>
  <div class="container">
    <div v-if="bookings" class="pb-5 cont justify-content-center">
      <div class="row col-lg-12 proji" style="row-gap: 30px">
        <div
                      v-for="booking in bookings"
            :key="booking._id"
          class="col-lg-3 col-sm-6 col-6 col-md-4"
          style="display: flex; justify-content: center"
        >
          <div
            class="card shadow"
            style="width: 18rem"

          >
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
          </div>
        </div>
      </div>
    </div>
    <div v-else class="load">
      <div class="loading"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bookings: null,
    };
  },
  // GETTING USERS
  mounted() {
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
};
</script>

<style scoped>
#nav a.router-link-exact-active {
  color: rgba(23, 83, 139, 0.924);
}
.content {
  padding-top: 250px;
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
}
.load {
  height: 100vh;
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
.cont{
  padding-top: 250px;
}
</style>
