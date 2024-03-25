<template>
  <div class="header row p-0 mb-0 text-white tp fixed-top">
    <div class="col-lg-1 p-0">
      <img class="logo-smk" src="@/assets/img/LOGO-SMK4.png" alt="LOGO SMKN 4">
    </div>

    <div class="col-lg-11">
      <h1 class="tittle">PERPUS DIGITAL</h1>
      <address class="alamat mb-0">
        SMKN 4 Tasikmalaya <p class="mb-0">JL.Depok, Sukamenak, Purbaratu</p>
      </address>
    </div>
  </div>
</template>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Michroma&display=swap');

.header {
  height: 21%;
}

.logo-smk {
  width: 125px;
  height: 135px;
  padding-left: 10px;
}

.tittle text-primary {
  font-size: 60px;
  font-style: italic;
  padding-left: 10px;
  opacity: 0.6;
}

h1 {
  font-family: "Michroma";
  font-size: 70px;
  margin: 0;
  lighting-color: #249cff;
  opacity: 0.6;
  color: #249cff;
}

.alamat {
  padding-left: 10px;
}

.tp {
  background-color: rgba(0, 0, 0, 0.7);
}
</style>