<template>
  <div class="wrapper">
    <div class="background"></div>
    <div class="search input-group input-group-sm p-0"></div>
    <form @submit.prevent="getBooks">
      <input v-model="keyword" type="search" class="form-control" aria-label="Small" placeholder=" search here...">
    </form>
    <div class="book mt-5">
      <div v-for="(book, i) in books" :key="i" class="col-lg-2">
        <div class="card-body">
          <NuxtLink :to="`/buku/${book.id}`">
            <img  :src="book.cover" class="cover-img" alt="cover">
          </NuxtLink>
        </div>
      </div>
    </div>
    <div class="btn">
      <NuxtLink class="kembali btn rounded-1" to="/history">kembali</NuxtLink>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const keyword = ref('')
const books = ref([])

const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select(`*,kategori(*)`)
  .ilike('judul', `%${keyword.value}%`)
  if(data) books.value = data
  data.forEach(book => {
    const {data} = supabase.storage.from('cover').getPublicUrl(book.cover)
    if (data) {
      book.cover = data.publicUrl
    }
  })
}

onMounted(() => {
  getBooks()
})

</script>


<style scoped>


.wrapper {
  width: 100%;
  height: 2000px;
  padding-top: 140px;
  padding-left: 0;
  padding-right: 0;
  background-size: auto;
  background-repeat: no-repeat;
  background-blend-mode: soft-light;
  position: sticky;
}


.background {
  background-image: url('@/assets/img/search-bg.png');
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: -1;
  background-size: cover;
  background-position: center;
}


.form-control {
  margin: 0;
  padding: 0;
  height: 4.6%;
  position: relative;
  font-weight: 500;
  color: black;
  opacity: 0.7;
  position: fixed;
  top: 20%;
  border-radius: 3px;
  margin-top: 0;
  width: 100%;
  padding: 0;
  opacity: 0.8;
}


::placeholder {
  color: black;
  opacity: 1;
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
}


.cover-img{
  width: 100%;
  height: 100%;
  background-size: cover;
}



.card-body {
  color: none;
  background-color: none;
  width: 130px;
  height: 200px;
  padding: 0;
  margin-bottom: 50px;
  margin-top: 50px;
  border: 10px solid rgba(0, 0, 0, 0.8);
}


.book {
  display: grid;
  grid-template-columns: auto auto auto auto auto auto;
  padding-left: 5%;
}

@media screen and (max-width: 768px){
  
  .form-control{
    top: 10%;
    height: 3%;
  }

  .book {
  display: grid;
  grid-template-columns: auto auto auto ;
  padding-left: 80px;
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
    bottom: 5%;
  }

}

@media screen and (max-width: 430px){

  .wrapper{
    padding-top: 70px;
  }

  .book {
  display: grid;
  grid-template-columns: auto auto ;
  padding-left: 8%;
  }

}

</style>