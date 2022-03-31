<template>
  <div class="price-title">
    <div class="container text-center">
      <ul class="">
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/adminservices"
            >Services</router-link
          ></a
        >

        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/adminusers"
            >Users</router-link
          ></a
        >
        <a class="nav-link text-truncate p-0 m-2"
          ><router-link class="text-white" to="/adminbookings"
            >bookings</router-link
          ></a
        >
      </ul>
    </div>
  </div>
         <div v-if="admin">
        <div >
          <div class=" container text-center">
            <div style="" class="sort-content justify-content-center row">
              <div class="col-10 col-md-8 col-lg-4" id="main">
                  <input
                    placeholder="Search user"
                    type="text"
                    v-model="search"
                  />
                
                <!-- <div v-for="customer in filteredCustomers">
                  <span>{{ customer.firstName }} {{ customer.lastName }}</span>
                </div> -->
              </div>
            </div>
          </div>
        </div>
  <div v-if="users" class="table-content">
    <div class="container">
      <table>
        <thead>
          <tr>
            <th>user ID:</th>
            <th>Name:</th>
            <th>Email:</th>
            <th>Phone:</th>
            <th>Joined:</th>
            <th>details:</th>
            <th>Delete:</th>
            
          </tr>
        </thead>
        <tbody v-for="user in filteredUsers" :key="user._id">
          <tr>
            <td data-column="UserId:">{{ user._id }}</td>
            <td data-column="Name:">{{ user.user_name }}</td>
            <td data-column="Email:">{{ user.user_email }}</td>
            <td data-column="Phone:">{{ user.user_contactNumber }}</td>
            <td data-column="Joined:">{{ user.join_date }}</td>
            <td data-column="Details:">

              <router-link
                class="text-black more-details"
                :to="{ name: 'User', params: { id: user._id } }"
                ><i class="bi text-black bi-three-dots"></i
              ></router-link>
            </td>
            <td  data-column="Delete:">
                          <button
              type="button"
              class="btn more-details text-black card-btn"
              @click.prevent="deleteUser(user._id)"
            >
              <i class="bi bi-trash3"></i>
            </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  </div>
<div class="load" v-else>
  <div class="loading" > ONLY ADMIN IS ALLOWED TO VIEW ALL USERS. LOG-IN AS AN ADMIN!!!</div>
</div>
</template>

<script>
import axios from "axios"
export default {
  data() {
    return {
      users: null,
      search:"",
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
      })
            console.log("after")
            fetch("https://laundry-villa.herokuapp.com/users", {
              method: "GET",
              headers: {
                "Content-type": "application/json; charset=UTF-8",
                 Authorization: `Bearer ${localStorage.getItem("jwt")}`,
              },
            })
              .then((response) => response.json())
              .then((json) => {
                console.log("after")
                console.log(json)
                this.users = json;
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
    }
    else{
      alert("Login")
      this.$router.push({ name: "Admin" });
    }
  },
  methods:{
    // DELETE PRODUCT(done)
    deleteUser(id) {
      const config = {
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      };
      let apiURL = `https://laundry-villa.herokuapp.com/users/${id}`;
      let indexOfArrayItem = this.users.findIndex((i) => i._id === id);
      if (window.confirm("Do you really want to delete?")) {
        axios
          .delete(apiURL, config)
          .then(() => {
            this.users.splice(indexOfArrayItem, 1);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
      computed: {
    filteredUsers: function () {
      return this.users.filter((user) => {
        return user.user_name.match(this.search);
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
.more-details {
  background: rgba(139, 102, 96, 0.924);
  border: 0;
  padding: 7px 15px;
  margin-top: 20px;
  color: rgb(255, 255, 255);
  border-radius: 10px;
  cursor: pointer;
  margin-bottom: 30px !important;
}
button:hover {
  opacity: 0.8;
  background: rgba(10, 81, 139, 0.979);
  color: white !important;
}
.bi-three-dots:hover {
  color: rgb(255, 255, 255) !important;
}
a {
  text-decoration-line: none;
}
.nav-link {
  display: inline;
}
.table-content {
  padding-top: 10px;
}
.price-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  z-index: 100;
  position: fixed;
  top: 110px;
}
input {
  width: 100% !important;
}
table {
  width: 100%;
  border-collapse: collapse;
  margin: 50px auto;
}

/* Zebra striping */
tr:nth-of-type(odd) {
  background: #eee;
}

th {
  background: rgba(10, 81, 139, 0.979);
  color: white;
  font-weight: bold;
}

td,
th {
  padding: 10px;
  border: 1px solid #ccc;
  text-align: left;
  font-size: 18px;
}

/* 
Max width before this PARTICULAR table gets nasty
This query will take effect for any screen smaller than 760px
and also iPads specifically.
*/
@media only screen and (max-width: 760px),
  (min-device-width: 768px) and (max-device-width: 1024px) {
  .table-content {
    padding-top: 150px;
  }

  table {
    width: 100%;
  }

  /* Force table to not be like tables anymore */
  table,
  thead,
  tbody,
  th,
  td,
  tr {
    display: block;
  }

  /* Hide table headers (but not display: none;, for accessibility) */
  thead tr {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }

  tr {
    border: 1px solid #ccc;
  }

  td {
    /* Behave  like a "row" */
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 30%;
  }

  td:before {
    /* Now like a table header */
    position: absolute;
    /* Top/left values mimic padding */
    top: 6px;
    left: 6px;
    width: 45%;
    padding-right: 10px;
    white-space: nowrap;
    /* Label the data */
    content: attr(data-column);

    color: #000;
    font-weight: bold;
  }
}
</style>
