<template>
  <div class="container-fluid">
    <div class="row my-">
      <div class="col-lg-6">
        <div class="card rounded-4 p-3  ms-3">
          <h2 class="text-white display-3">Form Pengunjung</h2>
          <div class="mb-3">
            <input type="text" class="form-control rounded-2" placeholder="Nama">
          </div>
          <div class="mb-3">
            <select class="form-control form-control-lg form-select rounded-2">
              <option value="">KATEGORI</option>
              <option value="umum">Umum</option>
              <option value="staff">Staff</option>
              <option value="siswa">Siswa</option>
              <option value="guru">Guru</option>
            </select>
          </div>
          <div class="mb-3">
            <div class="row">
              <div class="mb-0">
                <select class="form-control form-control-lg form-select rounded-2">
                  <option value="">KELAS</option>
                </select>
              </div>
              <div class="option">
                <div class="col-md p-0">
                  <select class="form-control form-control-lg form-select rounded-2 mt-1">
                    <option value="X">X</option>
                    <option value="XI">XI</option>
                    <option value="XII">XII</option>
                  </select>
                </div>
                <div class="col-md p-0">
                  <select class="form-control form-control-lg form-select rounded-2 mt-1">
                    <option value="PPLG">PPLG</option>
                    <option value="TJKT">TJKT</option>
                    <option value="TSM">TSM</option>
                    <option value="TOI">TOI</option>
                    <option value="DKV">DKV</option>
                  </select>
                </div>
                <div class="col-md p-0">
                  <select class="form-control form-control-lg form-select rounded-2 mt-1">
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                  </select>
                </div>
              </div>
              <div class="mb-3">
                <select class="form-control form-control-lg form-select rounded-2 mt-1">
                  <option value="">KEPERLUAN</option>
                </select>
              </div>
              <div class="mb-3">
                <select class="form-control form-control-lg form-select rounded-2">
                  <option value="baca">membaca di tempat</option>
                  <option value="pinjam">meminjam</option>
                  <option value="mengembalikan">mengembalikan buku</option>
                  <option value="">lainnya</option>
                </select>
              </div>
              <button type="submit" class="kirim btn rounded-2">kirim</button>
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

.text-white {
  font-weight: 400;
}

.card {
  background-color: rgba(0, 0, 0, 0.5);
  height: 100%;
  box-shadow: 1px 1px 10px #424242;
  width: 80rem;
  text-align: center;
  margin-left: 20px;
  margin-right: 20px;
}

.option {
  display: grid;
  grid-template-columns: auto auto auto;
}

.kirim {
  background-color: #D9D9D9;
  width: 120px;
  height: 30px;
  padding-top: 0px;
  text-align: center;
  margin-left: 10px;
}
</style>