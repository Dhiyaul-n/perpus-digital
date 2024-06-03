<template>
  <div class="container-fluid ps-5">
    <div class="background"></div>
    <div class="card bg-pengunjung rounded-3">
        <p class="jumlah-pengunjung">{{ visitors.length }} PENGUNJUNG</p>
    </div>
    <div class="table-responsive">
      <table class="tabel table rounded-pil">
        <thead>
          <tr class="table-top">
            <th class="top-text-center">No</th>
            <th class="top-text-center">Kategori</th>
            <th class="top-text-center">Nama</th>
            <th class="top-text-center">Kelas</th>
            <th class="top-text-center">Tanggal</th>
            <th class="top-text-center">Waktu</th>
            <th class="top-text-center">Keperluan</th>
          </tr>
        </thead>
        <tbody>

          <tr v-for="(visitor, i) in visitors" :key="i">


          <td class="text-center">{{ i+1 }}</td>


          <td class="text-center">{{visitor.keanggotaan.nama}}</td>


          <td class="text-center">{{visitor.nama}}</td>


          <td class="text-center">{{ visitor.kelas }} {{ visitor.jurusan }} {{visitor.tingkat}} </td>


          <td class="text-center">{{visitor.tanggal}}</td>


          <td class="text-center">{{visitor.waktu.split(".")[0]}}</td>


          <td class="text-center">{{visitor.keperluan?.nama || visitor.keperluan_lainnya}}</td>

          
        </tr>
      </tbody>
    </table>
  </div>
    <div class="button">
      <div class="back">      
        <NuxtLink class="kembali btn rounded-1" to="/">kembali</NuxtLink>
      </div>
      <div class="cari">
        <NuxtLink class="caribuku btn rounded-1" to="/buku/search">Cari buku</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>

const supabase = useSupabaseClient()
const visitors = ref ([])

const getPengunjung = async() => {
  const {data, error} = await supabase.from('pengunjung').select().order('tanggal', { ascending: false }).order('waktu', {ascending: false})
  .select(`*, keanggotaan(*), keperluan(*)`)
  if(data) visitors.value = data
}

onMounted (() => {
  getPengunjung()
})

</script>


<style scoped>


.background {
  background-image: url('@/assets/img/bg-home-cari-buku.jpg');
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: -1;
  background-size: cover;
  background-position: center;
}


.container-fluid {
  width: 100%;
  height: 100%;
  padding-top: 140px;
  background-size: cover;
  background-position: center;
}

.bg-pengunjung{
  margin-top: 10px;
  margin-bottom: 10px;
}

.jumlah-pengunjung{
  position: relative;
  font-size: 40px;
  font-weight: 500;
  top: 25%;
  color: black;
  font-family: "Alata";
  opacity: 1;  
  text-align: center;
  font-size: 24px;
  opacity: 1;
}

.card {
  padding: 0;
  height: 70px;
  width: 200px;
  opacity: .6;
}

.table-top{
  background-color: #4d4d4dcf;
  color: rgb(255, 255, 255);
  font-weight: lighter;
}

.table-responsive{
  padding-bottom: 5%;
}

.top-text-center{
  font-weight: 300;
  font-family: "Alata";
  text-align: center;
  border: 2px solid black;
}

.tabel {
  width: 95%;
}


td {
  border: 1.9px solid black;
}

td {
  background-color: #ffffffac;
}


td {
  font-family: 'Josefin Sans', sans-serif;
}

.button {
  display: grid;
  grid-template-columns: auto auto;
}

.kembali {
  background-color: #D9D9D9;
  width: 120px;
  height: 27px;
  padding-top: 0px;
  text-align: center;
  font-weight: 500;
  color: black;
  position: fixed;
  left: 30px;
  bottom: 3%;
  font-family: "Alata";
}

.caribuku {
  background-color: #D9D9D9;
  width: 120px;
  height: 27px;
  padding-top: 0px;
  text-align: center;
  font-weight: 500;
  color: black;
  position: fixed;
  right: 30px;
  bottom: 3%;
  font-family: "Alata";
}

@media screen and (max-width: 768px) {
  .tabel {
  width: 95%;
}
}

@media screen and (max-width: 430px){

  .background {
  background-image: url('@/assets/img/bg-mobile.png');
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: -1;
  background-size: cover;
  background-position: center;
}

.jumlah-pengunjung{
  position: relative;
  font-size: 20px;
  font-weight: 500;
  top: 25%;
  color: black;
  font-family: "Alata";
  opacity: 1;  
  text-align: center;
  font-size: 24px;
  opacity: 1;
}

.card {
  padding: 0;
  font-size: 20px;
  height: 30px;
  width: 100px;
  opacity: .6;
}

.jumlah-pengunjung{
  font-size: 10px;
}

.table-responsive{
  padding-bottom: 50px;
}


}

</style>
