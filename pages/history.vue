<template>
  <div class="container-fluid ps-5">
    <div class="card bg-pengunjung rounded-3 pt-2 mb-1">
      <div class="card-body ">
        <h2>Pengunjung</h2>
      </div>
    </div>
    <table class="tabel table rounded-pil">
      <thead>
        <tr class="table-dark">
          <th class="text-center">No</th>
          <th class="text-center">Kategori</th>
          <th class="text-center">Nama</th>
          <th class="text-center">Kelas</th>
          <th class="text-center">Tanggal</th>
          <th class="text-center">Waktu</th>
          <th class="text-center">Keperluan</th>
          <th class="text-center">jurusan</th>
          <th class="text-center">Rombel</th>
        </tr>
      </thead>
      <tbody>

        <td class="text-center">{{ }}1</td>


        <td class="text-center">{{ }}siswa</td>


        <td class="text-center">{{ }}Dhiyaul</td>


        <td class="text-center">{{ }} XI</td>


        <td class="text-center">{{ }}25/03/2024</td>


        <td class="text-center">{{ }}10.30</td>


        <td class="text-center">{{ }}Membaca di tempat</td>


        <td class="text-center">{{ }}PPLG</td>


        <td class="text-center">{{ }}3</td>


      </tbody>
    </table>
    <div class="button">
      <NuxtLink class="kembali btn rounded-1" to="/home">kembali</NuxtLink>
      <NuxtLink class="caribuku btn rounded-1" to="/search">Cari buku</NuxtLink>
    </div>
  </div>
</template>

<style scoped>
.container-fluid {
  background-image: url('@/assets/img/bg-home-cari-buku.jpg');
  width: 100%;
  height: 100vh;
  padding-top: 140px;
  background-size: 1400px;
}

.card {
  padding: 0;
  height: 70px;
  width: 200px;
  opacity: .6;
}

.card.bg-pengunjung {
  background-image: url('@/assets/img/bg-home-kunjungan.jpeg');
  background-position: center center;
  background-size: cover;
  filter: grayscale(100%);
}

.card-body h2 {
  text-align: center;
  font-size: 24px;
  color: white;
  opacity: 1;
}

.tabel {
  width: 1250px;
}

.table-dark th {
  border: 2px solid black;
}

td {
  border: 1.9px solid black;
}

td {
  background-color: #ffffff8a;
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
  height: 30px;
  padding-top: 0px;
  text-align: center;
  position: relative;
  left: 2.2px;
}

.caribuku {
  background-color: #D9D9D9;
  width: 120px;
  height: 30px;
  padding-top: 0px;
  text-align: center;
  position: relative;
  left: 71.1%;
}
</style>