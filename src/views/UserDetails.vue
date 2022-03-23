<template>
  <div class="price-title">
    <div class="container text-center">
      <p class="text-white p-2">User Details</p>
    </div>
  </div>
  <div class="container content">
    <div v-if="user">
      <div
        class="row col-lg-12 proji justify-content-center"
        style="row-gap: 10px; column-gap: 1px"
      >
        <div class="card pt-5 col-lg-3 text-center col-md-6">
          <i class="bi bi-person-circle"></i>
          <h1>{{ user.user_name }}</h1>
          <p class="title">{{ user.user_email }}</p>
          <p>{{ user.user_contactNumber }}</p>
          <p>{{ user.join_date }}</p>
          <div class="d-inline">
            <button
              type="button"
              class="btn mx-2 card-btn"
              @click.prevent="updateUser(user._id)"
            >
              <i class="bi bi-pencil"></i>
            </button>
            <button
              type="button"
              class="btn mx-2 card-btn"
              @click.prevent="deleteUser(user._id)"
            >
              <i class="bi bi-trash3"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["id"],
  data() {
    return {
      user: null,
    };
  },
  //     mounted() {
  //     fetch("http://localhost:3500/users/", {
  //       method: "GET",
  //       headers: {
  //         "Content-type": "application/json; charset=UTF-8",
  //         Authorization: `Bearer ${localStorage.getItem("jwt")}`,
  //       },
  //     })
  //       .then((response) => response.json())
  //       .then(async (json) => {
  //         this.users = json;
  //         await fetch(
  //           "http://localhost:3500/users/" + json.created_by,
  //           {
  //             method: "GET",
  //             headers: {
  //               "Content-type": "application/json; charset=UTF-8",
  //               Authorization: `Bearer ${localStorage.getItem("jwt")}`,
  //             },
  //           }
  //         )
  //           .then((response) => response.json())
  //           .then((json) => {
  //             this.users.created_by = json.user_name;
  //           });
  //       });
  //   },
  mounted() {
    fetch("https://laundry-villa.herokuapp.com/users/" + this.id, {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.user = json;
      })
      .catch((err) => {
        alert(console.log(err));
      });
  },
  methods: {
    deleteUser(id) {
      const config = {
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      };
      let apiURL = `https://laundry-villa.herokuapp.com/users/${id}`;
      let indexOfArrayItem = this.user.findIndex((i) => i._id === id);
      if (window.confirm("Do you really want to delete?")) {
        axios
          .delete(apiURL, config)
          .then(() => {
            this.user.splice(indexOfArrayItem, 1);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  }
  
};
</script>

<style scoped>
.bi-person-circle {
  font-size: 150px;
}
.content {
  padding-top: 200px;
}
.price-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  z-index: 100;
  position: fixed;
  top: 110px;
}
.loading {
  margin-top: 20%;
  justify-content: center;
}
.loading {
  border: 16px solid #f3f3f3;
  position: fixed;
  top: 20%;
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
.subtitlee {
  margin-top: 100px;
}
.title {
  color: grey;
  font-size: 18px;
}

a {
  text-decoration: none;
  font-size: 22px;
  color: black;
}
button:hover,
a:hover {
  opacity: 0.7;
}
@media all and (max-width: 700px) {
  .loading {
    border: 16px solid #f3f3f3;
    position: fixed;
    top: 15%;
    left: 32%;
    border-radius: 50%;
    border-top: 16px solid #000000;
    width: 120px;
    height: 120px;
    -webkit-animation: spin 2s linear infinite; /* Safari */
    animation: spin 2s linear infinite;
  }
}
</style>
