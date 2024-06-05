<template>
  <div class="wrapper">
    <div class="background"></div>
      <div class="search input-group input-group-sm p-0">
        <form @submit.prevent="getBooks">
          <input v-model="keyword" type="search" class="search form-control" aria-label="Small" placeholder=" search here...">
        </form>
      </div>
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
      <select v-model="category" class="kategori form form-select form-control" @change="getBooks">
        <option :value="null" disabled>Kategori</option>
        <option v-for="(kategori, i) in kategories" :key="i" :value="kategori.id">{{ kategori.nama }}</option>
        </select>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const kategories = ref([])
const keyword = ref('')
const category = ref(null)
const books = ref ([])


const getBooks = async () => {
  let query = supabase.from('buku').select(`*,kategori(*)`)
  if (keyword.value) query = query.ilike('judul', keyword.value)
  if (category.value) query = query.eq('kategori', category.value)
  const { data, error } = await query
  if (error) throw error
  if(data) {
    books.value = data
    data.forEach(book => {
      const {data} = supabase.storage.from('cover').getPublicUrl(book.cover)
      if (data) {
        book.cover = data.publicUrl
      }
    })
  } 
}

const getKategori = async () => {
  const { data, error} = await supabase
  .from('kategori_buku')
  .select('*')
  if (data) kategories.value = data
}

const bookFiltered = computed (() => {
  return books.value.filter((b) => {
    return (
      b.judul?.toLowerCase().includes(keyword.value?.toLowerCase()) ||
      b.kategori?.nama.toLowerCase().includes(keyword.value?.toLowerCase())
    ) 
  })
})


onMounted(() => {
  getBooks()
  getKategori()
})

</script>


<style scoped>




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


.search {
  margin: 0;
  padding: 0;
  height: 30px;
  font-weight: 500;
  color: black;
  opacity: 0.9;
  top: 0;
  bottom: 0;
  border-radius: 4px;
  width: 100%;
  position: sticky;
  margin-top: 10.7%;
  margin-bottom: 15%;
}


.kategori{
  background-color: #ffffff;
  width: 120px;
  height: 30px;
  padding-top: 0px;
  text-align: center;
  font-weight: 500;
  color: black;
  position: fixed;
  right: 5%;
  bottom: 3%;
  }


  form{
  width: 100%;
  }

::placeholder {
  color: black;
  opacity: 1;
}


.kembali {
  background-color: #ffffff;
  width: 120px;
  height: 27px;
  padding-top: 0px;
  text-align: center;
  font-weight: 500;
  color: black;
  position: fixed;
  left: 5%;
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
  
  .search{
    margin-top: 16.5%;
    margin-bottom: 17%;
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

  .search {
  margin: 0;
  padding: 0;
  height: 20px;
  font-weight: 500;
  color: black;
  opacity: 0.9;
  top: 0;
  bottom: 0;
  border-radius: 4px;
  width: 100%;
  position: sticky;
  margin-top: 20%;
  margin-bottom: 15%;
}

}

</style>