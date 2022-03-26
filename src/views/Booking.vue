<template>
  <section class="contact-background" id="contact">
    <div class="login-title">
      <div class="container text-center">
        <p class="text-white p-2">Book</p>
      </div>
    </div>
    <div class="cont container">
      <div class="formm">
        <div class="form-cont">
          <form @submit.prevent="register" class="contactMe container">
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

            <label class="text-black">Contact Number:</label>
            <input
              class="form-input neu-border-inset"
              type="text"
              v-model="user_contactNumber"
            />
        <div class="row"> 
            <div class="col-8 col-sm-7">
            <label class="text-black">Service:</label>
            <select required class="form-select" aria-label="Default select example">
              <option selected>Select Service</option>
              <option value="wash">Wash</option>
              <option value="dry">Dry</option>
              <option value="iron">Iron</option>              
              <option value="iron and fold">Iron & Fold</option>
              <option value="wash and dry">Wash & Dry</option>
              <option value="wash,dry and iron">Wash,Dry & Iron</option>
              <option value="curtains">Curtains</option>
              <option value="couch covers">Couch Covers</option>
              <option value="blankets">Blankets</option>
              <option value="shoes">Shoes</option>
            </select>            
        </div>
        <div class="col-4 col-sm-5">
            <label class="text-black">Baskets:</label>
            <input placeholder="No." type="number" id="quantity" name="quantity" min="1" max="5">
        </div>
        </div>


            <div class="row">
              <div class="col-md-6">
                <div class="form-group">
                  <label class="text-black">date:</label>
                  <input
                    class="form-control"
                    type="date"
                    required
                    v-model="date"
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label class="text-black">Time:</label>
                  <input
                    class="form-control"
                    type="time"
                    required
                    v-model="time"
                  />
                </div>
              </div>
            </div>

            <div class="submit mb-3">
              <button type="Submit" class="mb-3 btn button-body">
                <h5 id="sub" class="text-black mb-0">Confirm booking</h5>
              </button>
            </div>
          </form>
        </div>
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
      fetch("https://laundry-villa.herokuapp.com/users", {
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
          console.log();
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
.login-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  z-index: 100;
  position: fixed !important;
  top: 110px;
}
section {
  height: 100vh;
}
.form-cont {
  width: 50%;
}
form {
  max-width: 100%;
  margin: 30px auto;
  margin-top: 70px !important;
  text-align: left;
  border-radius: 10px;
  background-color: white;
  box-shadow: -10px 13px 20px 9px rgba(220, 220, 220, 0.94);
  -webkit-box-shadow: -10px 13px 20px 9px rgba(220, 220, 220, 0.94);
  -moz-box-shadow: -10px 13px 20px 9px rgba(220, 220, 220, 0.94);
}
label {
  color: rgb(0, 0, 0);
  display: inline-block;
  margin: 10px 0 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 7px 6px;
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ddd;
  color: rgb(0, 0, 0);
  background-color: rgba(233, 221, 221, 0.25);
}
.button-body {
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
  width: 100%;

  justify-content: center;
  align-items: center !important;
  display: flex;
  height: 100vh;
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
@media all and (max-width: 991px) {
  .form-cont {
    width: 60%;
  }
  form {
    margin-top: 70px !important;
  }
  input {
    display: block;
    padding: 5px 6px;
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ddd;
    color: rgb(0, 0, 0);
    background-color: rgba(233, 221, 221, 0.25);
  }
  .button-body {
    background: rgba(139, 102, 96, 0.924);
    border: 0;
    padding: 5px 20px;
    margin-top: 15px;
    color: rgb(255, 255, 255);
    border-radius: 10px;
    cursor: pointer;
    margin-bottom: 10px !important;
  }
  label {
    color: rgb(0, 0, 0);
    display: inline-block;
    margin: 5px 0 5px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
}

@media all and (max-width: 768px) {
  .form-cont {
    width: 70%;
  }
}

@media all and (max-width: 576px) {
  .form-cont {
    width: 80%;
  }
  .login-title {
    position: fixed;
    top: 110px;
  }
}
@media all and (max-width: 400px) {
}
</style>
