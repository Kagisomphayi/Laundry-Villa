<template>
  <section class="contact-background" id="contact">
    <div class="cont container">
      <div class="justify-content-center formm">
        <form @submit.prevent="register" class="contactMe container">
          <h2 class="text-center display-6 fw-bold mb-3 subtitlee">
            <u>Register</u>
          </h2>

          <label class="text-black">Name:</label>
          <input
            class="form-input neu-border-inset"
            type="text"
            v-model="user_name"
          />
          <label class="text-black">Email:</label>
          <input
            class="form-input neu-border-inset"
            type="email"
            v-model="user_email"
          />

          <label class="text-black">Contact:</label>
          <input
            class="form-input neu-border-inset"
            type="text"
            v-model="user_contactNumber"
          />

          <label class="text-black">Password:</label>
          <input
            class="form-input neu-border-inset"
            type="password"
            v-model="user_password"
          />

          <div class="submit mb-3">
            <button type="Submit" class="mb-3 btn button-body">
              <h5 id="sub" class="text-black mb-0">Register</h5>
            </button>
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      user_name: "",
      user_email: "",
      user_contactNumber: "",
      user_password: "",
    };
  },
  methods: {
    register() {
      fetch("https://groupapibackend.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          user_name: this.user_name,
          user_email: this.user_email,
          user_contactNumber: this.user_contactNumber,
          user_password: this.user_password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          console.log()
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Login" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style scoped>
section {
  padding-top: 50px;
}

form {
  max-width: 100%;
  margin: 30px auto;
  text-align: left;
  border-radius: 10px;
  background-color: white;
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
.subtitlee {
  padding-top: 50px;
}

@media all and (max-width: 800px) {
  .formm {
    width: 100%;
  }
}
</style>