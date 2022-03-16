<template>
  <!-- <section class="contact-background" id="contact" >
        <div class="container hr">
      <hr class="bg-white" >
    </div>
    <div class="container justify-content-center">
      <form action="https://formspree.io/f/xwkylkad"
      method="post"
      target="_blank" class="contactMe">
        <h2 class="text-center display-6 fw-bold mb-3 subtitlee ">
          <u>Contact Me</u>
        </h2>
        <div id="emailHelp" class="pb-2 mb-2 form-text text-center">
         <p>Let's get in touch. <br />I will never share your information with
          anyone.</p> 
        </div>

        <label class="text-black">Name:</label>
        <input name="name" type="text" class="text-white"  required />

        <label class="text-black">Email:</label>
        <input name="email" type="email" class="text-white"  required />

        <label  class="text-black">Subject:</label>
        <input name="subject" type="text" class="text-white"  />

        <label class="text-black">Message:</label>

        <input name="message" type="text" class="text-white"  />

        <div class="submit mb-3">
          <button type="submit" class="rounded-pill mb-3  btn button-body">
            <h5 id="sub" class="text-white mb-0">Submit</h5>
          </button>
        </div>

      </form>
    </div>

    <div class="container text-white">
      <div class="row text-center ">
        <div class="col-lg-4 col-sm-4 coL-md-3 ">
          <i class="bi bi-envelope contact-icons"></i><p>mphayiw@gmail.com</p>
        </div>
        <div class="col col-lg-4 col-sm-4 coL-md-3 mx-">
          <i class="bi bi-telephone contact-icons"></i><p>(+27)79 928 2407</p>
        </div>
        <div class="col col-lg-4 col-sm-4 coL-md-6">
          <i class="bi bi-geo-alt contact-icons"></i><p>Firgrove Rural <br> Cape Town, South Africa</p>
        </div>
      </div>
    </div>


  </section> -->
  <section>
    <div class="iframe">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3308.4776984642644!2d18.46159681607453!3d-33.98026178062569!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1dcc42d18d81d131%3A0xb8c5dd6edc01c0b!2sCavendish%20Square!5e0!3m2!1sen!2sza!4v1647438047822!5m2!1sen!2sza"
        width="100%"
        height="300"
        style="border: 0"
        allowfullscreen=""
        loading="lazy"
      ></iframe>
    </div>
  </section>

  <section class="contact-background" id="contact">
    <div class="login-title">
      <div class="container text-center">
        <p class="text-white p-2">Contact</p>
      </div>
    </div>
    <div class="cont">
      <div class="formm container justify-content-center">
        <div class=" row ">
          <div class="col-md-6 col-sm-12 col- col-lg-6 col-12">
            <div class=" ">
              <h5>Operating hours</h5>
              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quod praesentium voluptate, expedita blanditiis saepe alias! Earum soluta consequuntur molestias, obcaecati dolor voluptatibus doloremque est corrupti quasi, alias quidem eveniet reprehenderit!</p>

           
                <h5>Contact details</h5>
                  <p>
               Lorem ipsum dolor sit, amet consectetur adipisicing elit. Officiis omnis at, rerum corporis provident sit accusantium dolores sequi quo accusamus error incidunt nostrum animi, autem, ab ullam doloremque? Expedita, ex!
              </p>
              <h5>Banking details</h5>
              <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Iste cupiditate dicta ullam veritatis consequuntur perferendis a mollitia, incidunt veniam, accusantium sequi rerum praesentium libero quaerat eius magni amet aliquid non!</p>
            </div>
          </div>
        
        <div class="form-cont col-md-6 col-sm-12 col- col-lg-6 col-12">
          <form @submit.prevent="register" class="contactMe container">
             <div class="text-center"><h5 class=" p-2">Contact us</h5></div>
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

            <label class="text-black">Subject:</label>
            <input
              class="form-input neu-border-inset"
              type="text"
              v-model="user_contactNumber"
            />

            <label class="text-black">Message:</label>
            <input
              class="form-input message-input neu-border-inset"
              type="text"
              v-model="user_password"
            />

            <div class="submit mb-3">
              <button type="Submit" class="mb-3 btn button-body">
                <h5 id="sub" class="text-black mb-0">Submit</h5>
              </button>
            </div>
          </form>
        </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  // data() {
  //   return {
  //     name: "",
  //     email: "",
  //     subject: "",
  //     message: "",
  //   };
  // },
  //   methods: {
  //     handleSubmit() {
  // fetch('https://kagisomphayiportfolio.herokuapp.com/contact', {
  //   method: 'POST',
  //   body: JSON.stringify({
  //     name: this.name,
  //     email: this.email,
  //     subject: this.subject,
  //     message: this.message,
  //   }),
  //   headers: {
  //     'Content-type': 'application/json; charset=UTF-8',
  //   },
  // })
  //   .then((response) => response.json())
  //   .then((json) => console.log(json));
  //     },
  //   },
};
</script>

<style scoped>
.login-title {
  height: 40px;
  width: 100%;
  background-color: rgba(139, 102, 96, 0.924);
  z-index: 100;
  position: fixed;
  top: 110px;
}

h5{
   color: rgba(10, 81, 139, 0.979);
}
.iframe {
  margin-top: 150px;
}
form {
  max-width: 100%;
  margin: 30px auto;
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
  background: rgba(139, 102, 96, 0.924);
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: rgb(255, 255, 255);
  border-radius: 10px;
  cursor: pointer;
  margin-bottom: 50px !important;
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
  height: 100vh;
  padding-top:70px;
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
