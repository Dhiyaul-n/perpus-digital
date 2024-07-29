<template>
  <div class="wrapper">
    <div class="cover-form">
      <div class="background"></div>
      <div class="col-lg-6">
        <div class="cover-form">
          <form @submit.prevent="kirimData" class=" form card rounded-4">
            <h2 class="judul-form display-3">Form Pengunjung</h2>
            <div class="mb-1 p-5 pt-0 py-0">
              <input v-model="form.nama" type="text" class="form-control" placeholder="Nama">
            </div>
            <div class="mt-2 mb-1 p-5 pt-0 py-0">
              <select @change="cekKeanggotaan" v-model="form.keanggotaan" class="form-control"
                aria-placeholder="KATEGORI">
                <option value="" disabled>KATEGORI</option>
                <option v-for="(member, i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
              </select>
              <div v-if="form.keanggotaan == '2'" class="mb-0">
                <input type="text" value="KELAS" readonly class="form-control">
                <div class="option">
                  <div class="col-md p-0">
                    <select v-model="form.kelas" class="form-control ">
                      <option value="" disabled>TINGKAT</option>
                      <option class="opsi" value="X">X</option>
                      <option class="opsi" value="XI">XI</option>
                      <option class="opsi" value="XII">XII</option>
                    </select>
                  </div>
                  <div class="col-md p-0">
                    <select v-model="form.jurusan" class="form-control" @change="selectJurusan">
                      <option value="" disabled>JURUSAN</option>
                      <option class="opsi" value="PPLG">PPLG</option>
                      <option class="opsi" value="TJKT">TJKT</option>
                      <option class="opsi" value="TSM">TSM</option>
                      <option class="opsi" value="TOI">TOI</option>
                      <option class="opsi" value="DKV">DKV</option>
                    </select>
                  </div>
                  <div class="col-md p-0">
                    <select v-model="form.tingkat" :disabled="!form.jurusan || form.jurusan == 'TOI'"
                      class="form-control" required>
                      <option value="" disabled>ROMBEL</option>
                      <option class="opsi" value="1">1</option>
                      <option class="opsi" value="2">2</option>
                      <option v-if="!(form.jurusan == 'DKV')" class="opsi" value="3">3</option>
                      <option v-if="!(form.jurusan == 'DKV')" class="opsi" value="4">4</option>
                    </select>
                  </div>
                </div>
              </div>
              <div class="mb-1 pt-1 py-1 ">
                <select @change="cekKeperluan" v-model="keperluan" class="form-control" placeholder="Keperluan"
                  required>
                  <option value="" disabled>KEPERLUAN</option>
                  <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
                  <option>Lainnya</option>
                </select>
              </div>
              <div v-if="keperluan == 'Lainnya'" class="form-group-py1 text-dark" aria-placeholder="KEPERLUAN">
                <div class="dll">
                  <textarea v-model="form.keperluan_lainnya" class="form-control" cols="30" rows="3"
                    placeholder="ketik di sini.."></textarea>
                </div>
              </div>
              <div class="pt-4 py-4">
                <button type="submit" class="kirim btn" value="kirim">kirim</button>
              </div>
            </div>
          </form>
        </div>
        <button type="submit" class="btn-skip">
          <NuxtLink to="/history">
            <svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
              width="24" height="24" fill="none" viewBox="0 0 24 24">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="m9 5 7 7-7 7" />
            </svg>
          </NuxtLink>
        </button>
      </div>
    </div>
  </div>

</template>

<script setup>

const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])

const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan_lainnya: "",
})
const keperluan = ref('')

const kirimData = async () => {
  const { error } = await supabase.from('pengunjung').insert([{
    ...form.value,
    keperluan: keperluan.value == 'Lainnya' ? null : keperluan.value
  }])
  if (error) throw error
  else navigateTo('/history')
  if (error) gagal.value = true
  else terkirim.value = true
}

const cekKeanggotaan = e => {
  if (e.target.value != '2') {
    form.value.kelas = ''
    form.value.jurusan = ''
    form.value.tingkat = ''
  }
}
const cekKeperluan = e => {
  if (e.target.value != 'Lainnya') {
    form.value.keperluan_lainnya = ''
  }
}

const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if (data) members.value = data
}


const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if (data) objectives.value = data
}

const selectJurusan = () => {
  if (form.value.jurusan == 'TOI') {
    form.value.tingkat = ''
  }
}

onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})


</script>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,100..700;1,100..700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Andada+Pro:ital,wght@0,400..840;1,400..840&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Alata&display=swap');


.wrapper {
  width: 100%;
  height: 100%;
  padding-top: 14%;
  padding-left: 0;
  padding-right: 0;
  background-size: cover;
  background-repeat: no-repeat;
  background-blend-mode: soft-light;
}


.background {
  background-image: url('@/assets/img/home.jpg');
  position: fixed;
  width: 100%;
  height: 100%;
  padding-left: 0;
  padding-right: 0;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-size: cover;
  background-position: center;
}


.tittle {
  font-family: "Michroma";
}


h2 {
  font-family: "Josefin+Sans";
  font-weight: 100;
  font-style: normal;
}


.text-white {
  font-weight: 400;
}

cover-form {
  width: 100%;
}

.form {
  padding: 3px;
  border-radius: 20px;
}


.card {
  background-color: rgba(0, 0, 0, 0.45);
  box-shadow: 1px 1px 5px #000000;
  width: 95%;
  text-align: center;
  margin-left: 2.5%;
  margin-right: 0;
  position: absolute;
  font-family: "Andada+pro";
  font-weight: bolder;
}

.judul-form {
  color: white;
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
  border-radius: 3px;
  border: 1px black;
  font-size: 15px;
  font-weight: 400;
  font-family: "Alata";
  color: black;
  width: 120px;
  height: 30px;
  padding: 0px;
  text-align: center;
  position: relative;
  right: 45%;
}

.btn-skip {
  background-color: #ffffff;
  border-radius: 50%;
  font-size: 15px;
  font-weight: 400;
  font-family: "Alata";
  color: black;
  width: 60px;
  height: 60px;
  text-align: center;
  position: absolute;
  bottom: 5%;
  right: 5%;
  box-shadow:
    inset -.5px -.5px .5px 0px rgba(0, 0, 0, 0.23),
    inset .5px .5px .5px 0px rgba(255, 255, 255, 0.6);
}


@media screen and (max-width: 768px) {

  .wrapper {
    width: 100%;
    height: 100%;
    padding-top: 20%;
  }

  .kirim {
    right: 0%;
    width: 150px;
    height: 40px;
    font-size: 20px;
  }

}

@media screen and (max-width: 430px) {
  .wrapper {
    width: 100%;
    height: 100%;
    padding-top: 40%;
  }

  .background {
    background-image: url('@/assets/img/home-mobile.png');
  }

  .background::before {
    background-color: rgba(0, 0, 0, 0.5);
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
  }

  .card {
    background-color: rgba(255, 255, 255, 0.1);
    box-shadow: 1px 1px 7px #000000;
    width: 80%;
    position: relative;
    left: 7.5%;
    font-size: 20px;
    text-align: center;
    font-family: "Andada+pro";
    font-weight: bolder;
  }

  .judul-form {
    color: #ddc08c;
    text-shadow: 1px 1px 5px rgb(0, 0, 0);
    -webkit-text-stroke-width: .2px;
    -webkit-text-stroke-color: rgb(0, 0, 0);
    font-size: 35px;
    padding: 10%;
    font-family: 'Times New Roman', Times, serif;
    font-weight: 250;
    font-style: italic;
  }

  .form-control {
    padding: 2px;
    padding-bottom: 0;
    padding-left: 5px;
    font-size: 7px;
  }

  .kirim {
    background-color: rgb(255, 255, 255);
    color: #000000;
    right: 0%;
    width: 60px;
    height: 15px;
    font-size: 8px;
  }



}
</style>
