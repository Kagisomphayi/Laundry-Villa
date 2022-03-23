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
      </ul>
    </div>
  </div>
  <div class="table-content">
    <div class="container">
      <table>
        <thead>
          <tr>
            <th>user ID</th>
            <th>Name</th>
            <th>Email</th>
            <th>Contact number</th>
            <th>Join date</th>
            <th>More details</th>
          </tr>
        </thead>
        <tbody  v-for="user in users" :key="user._id">
          <tr >
              <td data-column="User Id">{{ user._id }}</td>
              <td data-column="User Name">{{ user.user_name }}</td>
              <td data-column="User Email">{{ user.user_email }}</td>
              <td data-column="Contact Number">{{ user.user_contactNumber }}</td>
              <td data-column="Join Date">{{ user.join_date }}</td>
              <td data-column="More Details"><router-link class="text-black more-details" :to="{name: 'User', params: {id: user._id}}"><i class="bi text-black bi-three-dots"></i></router-link></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: null,
    };
  },
  // GETTING SERVICES
  mounted() {
    fetch("http://localhost:3500/users/")
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        this.users = data;
      });
  },
};
</script>

<style scoped>
.more-details{
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
    padding-left: 50%;
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
