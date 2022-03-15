<template>
  <section class="contact-background" id="contact">
    <div class="cont container">
      <div class="justify-content-center formm">
        <form @submit.prevent="login" class="contactMe container mt-5">
          <h2 class="text-center display-6 fw-bold mb-3 subtitlee">
            <u>LogIn</u>
          </h2>
          <label class="text-black">Email:</label>
          <input
            class="form-input neu-border-inset"
            type="email"
            v-model="user_email"
          />
          <label class="text-black">Password:</label>
          <input
            class="form-input neu-border-inset"
            type="password"
            v-model="user_password"
          />

          <div class="submit ">
            <button type="Submit" class="mb-3 btn button-body">
              <h5 id="sub" class="text-black mb-0">Login</h5>
            </button>
          </div>
          <div>
            <p class="pb-4">
              Not a member?
              <router-link :to="{ name: 'Register' }"
                >Create an account</router-link
              >
            </p>
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      user_email: "",
      user_password: "",
    };
  },
  methods: {
    login() {
      fetch("https://groupapibackend.herokuapp.com/users", {
        method: "PATCH",
        body: JSON.stringify({
          user_email: this.user_email,
          user_password: this.user_password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          localStorage.setItem("jwt", json.jwt);
          alert("User logged in");
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
form {
  max-width: 100%;
  margin: 30px auto;
  text-align: left;
  border-radius: 10px;
  background-color: white;
  border: solid 2px black;
  box-shadow: #000000;
}
label {
  color: rgb(0, 0, 0);
  display: inline-block;
  margin: 25px 0 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ddd;
  color: rgb(0, 0, 0);
  background-color: rgba(233, 221, 221, 0.25);
}
.button-body {
  background: rgb(255 212 0);
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: rgb(0, 0, 0);
  border-radius: 10px;
  cursor: pointer;
  margin-bottom: 50px !important;
}
button:hover {
  opacity: 0.8;
  background: #000000;
}
.submit {
  text-align: center;
}
#sub:hover {
  color: rgb(255, 255, 255) !important;
}
#sub {
  color: white;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
.contactMe {
  width: 100%;
  margin: 0px;
}
.contact-icons {
  font-size: 20px !important;
}
.formm {
  width: 50%;
  margin-top: 70px;
}
.cont {
  display: flex;
  flex-wrap: wrap;
  justify-content: center !important;
}


@media all and (max-width: 991px) {
  .formm {
    width: 60%;
    margin-top: 70px;
  }
}

@media all and (max-width: 768px) {
  .formm {
    width: 70%;
    margin-top: 70px;
  }
}

@media all and (max-width: 576px) {
  .formm {
    width: 80%;
    margin-top: 70px;
  }
}
@media all and (max-width: 400px) {
}
</style>