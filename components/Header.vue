<template>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <div class="header row p-0 mb-0 text-white tp fixed-top">
      <div class="div-logo">
        <img class="logo-smk" src="@/assets/img/LOGO-SMK4.webp" alt="LOGO SMKN 4">
    </div>

    <div class="div-judul">
      <h1 class="tittle">PERPUS DIGITAL</h1>
      <address class="alamat mb-0">SMKN 4 Tasikmalaya <p>JL.Depok, Sukamenak, Purbaratu</p>
      </address>
    </div>
  </div>
</template>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Michroma&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Andada+Pro:ital,wght@0,400..840;1,400..840&family=Josefin+Sans:ital,wght@0,100..700;1,100..700&display=swap');


.header{
  box-shadow: 1px 1px 10px #ffffff;
  background-color: rgba(0, 0, 0, 0.6);
  transition: 1s;
  display: grid;
  grid-template-columns: 10% 90%;
}


.header:hover{
  box-shadow: 1px 1px 5px #000000;
  background-color: #f8d30400;
  transition: 1s;
}


.div-logo{
  width: 100%;
  height: 100%;
}

.logo-smk {
  width: 130px;
  padding-left: 10px;
}

.div-judul{
  width: 100%;
  height: 100%;
}

.tittle {
  font-family: "Michroma";
  font-size: 65px;
  margin: 0;
  lighting-color: white;
  color: #fffbfb7e;
  font-weight: 500;
  padding-left: 10px;
  opacity: 1;
  line-height: 1.2em;
  text-shadow:
    0 0 #ffffff7c,
    0 1.2em #ffffff68;
  overflow: hidden;
  transition: .7s;
  cursor: pointer;
}

.tittle:hover {
  color: #249cff;
  text-shadow: 0 -1.1em #249cff77;
  transition: .7s;
  opacity: 1;
}


.alamat {
  padding-left: 10px;
  font-family: "Andada";
  font-size: 16px;
}

@media screen and (max-width: 768px) {
  .header {
  display: grid;
  grid-template-columns: 18% 82%;
  }

  .div-logo{
  width: 100%;
  height: 100%;
}

.logo-smk {
  width: 100%;
  padding-left: 10px;
}

  .div-judul{
    height: 40%;
    padding: 0;
  }

  .tittle{
    font-size: 40px;
    padding: 0;
  }
}

@media screen and (max-width: 430px){
  .header {
  box-shadow: 1px 1px 5px #000000;
  background-color: #f8d30400;
  display: grid;
  grid-template-columns: 20% 80%;
  padding: 0;
  }

  .div-logo{
  width: 100%;
  height: 100%;
}

.logo-smk {
  width: 100%;
  padding-left: 10px;
}

  .div-judul{
    height: 40%;
    padding: 0;
  }

  .tittle {
  color: #249cff;
  font-size: 20px;
  text-shadow: 0 -1.1em #249cff77;
  transition: .7s;
  opacity: 1;
  }
  
.alamat{
  font-size: 10px;
}

}

</style>