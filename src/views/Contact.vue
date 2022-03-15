<template>
  <section class="contact-background" id="contact" >
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
form {
  max-width: 100%;
  margin: 30px auto;
  text-align: left;
  border-radius: 10px;
}
label {
  color: rgb(0, 0, 0);
  display: inline-block;
  margin: 25px 0 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input{
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
  background-color: rgba(0,0,0,.25);
}
.button-body {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
.submit {
  text-align: center;
}
#sub:hover{
  color: rgb(0, 0, 0) !important;
}
#sub{color: white;}
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
.contact-icons{
font-size: 20px !important;
}
</style>