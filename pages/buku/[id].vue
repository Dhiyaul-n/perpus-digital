<template>
  <div class="container-fluid">
    <div class="background"></div>
    <div class="group">
      <img class="book-img" :src="buku?.cover">
      <div class="text">
        <h1 class="tittle">Judul : {{ buku?.judul }}</h1>
        <p class="pengarang">Pengarang : {{ buku?.penulis }}</p>
        <p class="tahun-terbit">Tahun terbit : {{ buku?.tahun_terbit }}</p>
        <p class="lokasi">Rak : {{ buku?.rak }}</p>
        <p class="kategori">KATEGORI : {{ buku?.kategori_buku?.nama }}</p>
        <p id="desc1" class="desc">Deskripsi : {{ buku?.deskripsi }}</p>
      </div>
    </div>
        <p id="desc2" class="desc">Deskripsi : {{ buku?.deskripsi }}</p>
    <div class="btn">
      <NuxtLink class="kembali btn rounded-1" to="/buku/search">kembali</NuxtLink>
    </div>

  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref()


const getBookById = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori_buku(*)`)
  .eq('id', route.params.id)
  .maybeSingle()
  if(error) throw error
  console.log(data)
  if (data) {
    const { data: url } = supabase.storage.from('cover').getPublicUrl(data.cover)
    if (url) 
    {
      data.cover = url.publicUrl
    }
    buku.value = data
  }
}

onMounted(() => {
  getBookById()
})

</script>

<style scoped>
.container-fluid {
  width: 100%;
  height: 100%;
  padding-top: 15%;
  padding-left: 0;
  padding-right: 0;
  background-blend-mode: soft-light;
}

.background {
  background-image: url('@/assets/img/bg-detail.png');
  position: fixed;
  z-index: -1;
  width: 100%;
  height: 100%;
  padding-left: 0;
  padding-right: 0;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background-size: cover;
}

.group {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.15);
  display: grid;
  position: sticky;
  grid-template-columns: 25% 75%;
}

.book-img {
  height: 100%;
  width: 100%;
  position: relative;
  bottom: 6px;
  padding: 0px;
  border: rgba(255, 255, 255, 0.5) 15px solid;
}

.tittle {
  font-size: 54px;
  color: white;
  font-style: italic;
  padding-left: 10px;
}

.pengarang {
  font-size: 25px;
  padding-left: 15px;
  margin: 0;
  color: white;
  font-style: italic;
}

.tahun-terbit {
  font-size: 25px;
  padding-left: 15px;
  margin: 0;
  color: white;
  font-style: italic;
}

.lokasi {
  font-size: 25px;
  padding-left: 15px;
  margin: 0;
  color: white;
  font-style: italic;
}

.kategori {
  font-size: 25px;
  padding-left: 15px;
  margin: 0;
  color: white;
  font-style: italic;
}

.desc {
  font-size: 30px;
  color: white;
  font-style: italic;
  padding-left: 15px;
  text-shadow: -2px -1px 0 #000, 2px -1px 0 #000, -2px 1px 0 #000, 2px 1px 0 #000;
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
  right: 30px;
  bottom: 3%;
}

/* if text deskripsi */

@media screen and (min-width: 1024px){
  #desc2{
    display: none;
  }
}

/* UKURAN TABLET */

@media screen and (max-width: 720px){

  .container-fluid {
  width: 100%;
  height: 100%;
  padding-top: 15%;
}

.group {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.15);
}

  .book-img {
  height: 100%;
  width: 100%;
  bottom: 6px;
  padding: 0px;
  border: rgba(255, 255, 255, 0.5) 15px solid;
}

.desc {
  padding-left: 15px;
  position: relative;
}

#desc1{
  display: none;
}

#desc2{
  width: 100%;
  font-size: 20px;
}

}

@media screen and (max-width: 430px){

  .container-fluid {
  width: 100%;
  height: 100%;
  padding-top: 25%;
}

  .group {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.15);
    display: grid;
    grid-template-columns: 50% 50%;
  }

  .book-img {
    height: 100%;
    width: 100%;
    padding: 0px;
    border: rgba(255, 255, 255, 0.5) 15px solid;
  }

  .pengarang {
    font-size: 15px;
    padding-left: 5px;
  }

  .tahun-terbit {
    font-size: 15px;
    padding-left: 5px;
  }

  .lokasi {
    font-size: 15px;
    padding-left: 5px;
  }
  .kategori {
    font-size: 15px;
    padding-left: 5px;
  }

  .tittle{
    font-size: 20px;
    padding-left: 5px;
  }

  .desc {
    text-shadow: -.1px -.1px 0 #000, .1px -1px 0 #000;
  }


  #desc1{
  display: none;
}

#desc2{
  width: 100%;
  font-size: 20px;
}

}

</style>