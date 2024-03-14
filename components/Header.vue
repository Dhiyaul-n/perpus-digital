<template>
  <div class="header row p-0 mb-0 text-white tp fixed-top">
    <div class="col-lg-1 p-0">
      <img class="logo-smk" src="@/assets/img/LOGO-SMK4.png" alt="LOGO SMKN 4">
    </div>

    <div class="col-lg-11">
      <h1 class="text-primary">PERPUS DIGITAL</h1>
      <address class="alamat mb-0">
        SMKN 4 Tasikmalaya <p class="mb-0">JL.Depok, Sukamenak, Purbaratu</p>
      </address>
    </div>
  </div>
</template>



<style scoped>
.header {
  height: 21%;
}

.logo-smk {
  width: 125px;
  height: 135px;
  padding-left: 10px;
}

.text-primary {
  font-size: 60px;
  padding-left: 10px;
  opacity: 0.6;
  color: lighten(rgba(0, 191, 255, 0.5));

}

.alamat {
  padding-left: 10px;
}

.tp {
  background-color: rgba(0, 0, 0, 0.7);
}
</style>