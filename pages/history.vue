<template>
  <div class="container-fluid ps-5">
    <div class="background"></div>
    <div class="grid-group">
      <div class="bg-pengunjung">
        <p class="jumlah-pengunjung">Pengunjung: {{ visitors.length }}</p>
      </div>
      <div class="search responsive p-0">
        <form class="formulir" @submit.prevent="getBooks">
          <input v-model="keyword" type="search" class="search form-control" placeholder="🔎cari pengunjung.." @input="getPengunjung">
        </form>
        </div>
      </div>

    <div class=" table-responsive head">
      <table class="tabel table table-head rounded-pil">
        <thead>
          <tr class="table-top">
            <th class="top-text-center" style="width: 3.7%;">No</th>
            <th class="top-text-center" style="width: 7.78%;">Kategori</th>
            <th class="top-text-center" style="width: 23%;">Nama</th>
            <th class="top-text-center" style="width: 13.94%;">Kelas</th>
            <th class="top-text-center" style="width: 14.5%;">Tanggal</th>
            <th class="top-text-center" style="width: 13.7%;">Waktu</th>
            <th class="top-text-center" style="width: 18.45%;">Keperluan</th>
          </tr>
        </thead>
        </table>
        </div>
        <div class="table-responsive body">
          <table class=" table-body">
          <tbody>

            <tr v-for="(visitor, i) in visitors" :key="i">


            <td class="text-center" style="width: 4%;">{{ i+1 }}</td>


            <td class="text-center" style="width: 8%;">{{visitor.keanggotaan.nama}}</td>


            <td class="text-center" style="width: 24.4%;">{{visitor.nama}}</td>


            <td class="text-center" style="width: 14.5%;">{{ visitor.kelas }} {{ visitor.jurusan }} {{visitor.tingkat}} </td>


            <td class="text-center" style="width: 15.3%">{{visitor.tanggal}}</td>


            <td class="text-center" style="width: 10.7%;">{{visitor.waktu.split(".")[0]}}</td>


            <td class="text-center" style="width: 21.38%;">{{visitor.keperluan?.nama || visitor.keperluan_lainnya}}</td>

            
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
const keyword = ref ('')
const visitors = ref ([])


const getPengunjung = async() => {
  const {data, error} = await supabase.from('pengunjung')
  .select().order('tanggal', { ascending: false }).order('waktu', {ascending: false}).select(`*, keanggotaan(*), keperluan(*)`)
  .ilike('nama', `%${keyword.value}%`)
  .order('id', { ascending: false })
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

.grid-group{
  width: 94.7%;
  margin-top: 20px;
  height: 60px;
  display: grid;
  grid-template-columns: 20% 80%;
}


.jumlah-pengunjung{
  background-color: rgba(128, 128, 128, 0.65);
  border-radius: 5px;
  position: relative;
  font-size: 40px;
  font-weight: 500;
  width: 100%;
  color: black;
  font-family: "Alata";
  opacity: 1;  
  text-align: center;
  font-size: 24px;
  opacity: 1;
}

.search  {
  position: relative;
}

.table-responsive{
  width: 100%;
}

.top-text-center{
  background-color: #4d4d4dcf;
  color: rgb(255, 255, 255);
  font-weight: lighter;
}

.tabel-atas{
  padding-bottom: 5%;
  width: 90%;
}

.table-head{
  padding-bottom: 5%;
  width: 95%;
  margin: 0;
  padding: 0;
}

.table-body{
  padding-bottom: 5%;
  max-height: 100px;
  width: 95%;
}


.top-text-center{
  font-weight: 300;
  font-family: "Alata";
  text-align: center;
  border: 2px solid black;
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

.grid-group{
  width: 100%;
  margin-left: 0%;
  position: relative;
  right: 7%;
  margin-top: 20px;
  margin-bottom: 60px;
  display: grid;
  grid-template-rows: 50% 50%;
  display: list-item;
}



.bg-pengunjung{
  height: 100%;
}

.jumlah-pengunjung{
  position: relative;
  font-weight: 500;
  color: black;
  font-family: "Alata";
  opacity: 1;  
  text-align: center;
  font-size: 20px;
  opacity: 1;
}

.search{
  padding: 5;
}

.tabel{
  width: 100%;
  padding-right: 50px;
}

.table-responsive{
  font-size: 10px;
  position: relative;
  padding-bottom: 50px;
  margin: 0;
  padding: 0;
  width: 100%;
  right: 7%;
}



.table-body{
  padding-bottom: 5%;
  width: 100%;
  overflow-x:hidden;
  position: relative;
}

}

</style>
