<template>
  <!-- Footer -->
  <section>
    <footer
      class="page-footer font-small teal pt-2"
      style="z-index: 10;"
    >
      <div class="container text-center text-md-left">

        <!-- Copyright -->
        <div class="footer-copyright text-center mb-0 py-1 text-white h5">
          ©2021 Copyright: Laundry Villa
        </div>
        <!-- Copyright -->
      </div>
    </footer>
  </section>
</template>

<script scoped>
export default {};
</script>

<style>
.hrFooter {
  margin: 0px;
  background-color: black !important;
}
#footerr:hover {
  color: white;
}
#footerr {
  color: rgb(155, 44, 155);
}
.icons:hover {
  -ms-transform: scale(1.5); /* IE 9 */
  -webkit-transform: scale(1.5); /* Safari 3-8 */
  transform: scale(1.5);
  color: rgb(155, 44, 155) !important;
}

footer{
    position:fixed;
    bottom: 0;
    background-color:  rgb(39, 89, 180);
    width: 100%;
}
</style>