<template>
  <div class="header row p-0 mb-0 text-white tp fixed-top">
    <div class="col-lg-1 p-0">
      <img class="logo-smk" src="@/assets/img/LOGO-SMK4.png" alt="LOGO SMKN 4">
    </div>

    <div class="col-lg-11">
      <h1 class="tittle">PERPUS DIGITAL</h1>
      <address class="alamat mb-0">SMKN 4 Tasikmalaya <p>JL.Depok, Sukamenak, Purbaratu</p>
      </address>
    </div>
  </div>
</template>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Michroma&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Andada+Pro:ital,wght@0,400..840;1,400..840&family=Josefin+Sans:ital,wght@0,100..700;1,100..700&display=swap');

.header {
  height: 21%;
}

.logo-smk {
  width: 125px;
  height: 135px;
  padding-left: 10px;
}

.tittle {
  font-family: "Michroma";
  font-size: 60px;
  margin: 0;
  lighting-color: #249cff;
  color: #249cff;
  font-style: italic;
  font-weight: 600;
  padding-left: 10px;
  opacity: 1;
  line-height: 1.2em;
  text-shadow:
    0 0 #ffffff,
    0 1.2em #ffffff;
  overflow: hidden;
  transition: .5s;
  cursor: pointer;
}

.tittle:hover {
  color: rgba(255, 255, 255, 0.8);
  text-shadow:
    0 -1.3em #249cff;
}


.alamat {
  padding-left: 10px;
  font-family: "Andada+Pro";
}

.tp {
  background-color: rgba(0, 0, 0, 0.7);
}
</style>