<template>
  <div class="container-fluid">
    <div class="row py-4">
      <div class="col-lg-6">
        <div class="form card rounded-4">
          <h2 class=" text-white display-3">Form Pengunjung</h2>
          <div class="mb-1 p-5 pt-0 py-0">
            <input type="text" class="form-control rounded-2" placeholder="Nama">
          </div>
          <div class="mt-2 mb-1 p-5 pt-0 py-0">
            <select class="form-control form-select rounded-2">
              <option value="">KATEGORI</option>
              <option value="umum">Umum</option>
              <option value="staff">Staff</option>
              <option value="siswa">Siswa</option>
              <option value="guru">Guru</option>
            </select>
          </div>
          <div class="mb-3 p-5 pt-0 py-0">
            <div class="row">
              <div class="mb-0">
                <select class="form-control form-select rounded-2">
                  <option value="">KELAS</option>
                </select>
              </div>
              <div class="option">
                <div class="col-md p-0">
                  <select class="form-control form-select rounded-2 ">
                    <option class="opsi" value="X">X</option>
                    <option class="opsi" value="XI">XI</option>
                    <option class="opsi" value="XII">XII</option>
                  </select>
                </div>
                <div class="col-md p-0">
                  <select class="form-control form-select rounded-2 ">
                    <option class="opsi" value="PPLG">PPLG</option>
                    <option class="opsi" value="TJKT">TJKT</option>
                    <option class="opsi" value="TSM">TSM</option>
                    <option class="opsi" value="TOI">TOI</option>
                    <option class="opsi" value="DKV">DKV</option>
                  </select>
                </div>
                <div class="col-md p-0">
                  <select class="form-control form-select rounded-2 ">
                    <option class="opsi" value="1">1</option>
                    <option class="opsi" value="2">2</option>
                    <option class="opsi" value="3">3</option>
                    <option class="opsi" value="4">4</option>
                  </select>
                </div>
              </div>
              <div class="mb-1">
                <select class="form-control form-select rounded-2 mt-1">
                  <option value="">KEPERLUAN</option>
                </select>
              </div>
              <div class="mb-1 pt-1 py-1">
                <select class="form-control form-select rounded-2">
                  <option class="opsi" value="baca">Membaca di tempat</option>
                  <option class="opsi" value="pinjam">Meminjam</option>
                  <option class="opsi" value="mengembalikan">Mengembalikan buku</option>
                  <option class="opsi" value="lainnya">Lainnya</option>
                </select>
              </div>
              <div class="pt-4 py-4">
                <NuxtLink type="submit" class="kirim btn rounded-1" to="/history">kirim</NuxtLink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container-fluid {
  background-image: url('@/assets/img/bg-home-kunjungan.jpeg');
  width: 100%;
  height: 100vh;
  background-size: cover;
  padding-top: 140px;
}

.tittle {
  font-family: "Michroma";
}

.text-white {
  font-weight: 400;
}


.form-control {
  padding: 3px;
}

.card {
  background-color: rgba(0, 0, 0, 0.5);
  /* height: auto; */
  box-shadow: 1px 1px 10px #424242;
  width: 80rem;
  text-align: center;
  margin-left: 20px;
  margin-right: 20px;
}

.opsi {
  background-color: #ffffff;
  opacity: 0.5;
}

.option {
  height: 100%;
  display: grid;
  grid-template-columns: auto auto auto;
}

.col-md p-0 {
  height: 35px;
}

.kirim {
  background-color: #D9D9D9;
  width: 120px;
  height: 30px;
  padding-top: 0px;
  text-align: center;
}
</style>