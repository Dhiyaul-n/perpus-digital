<template>
  <div class="container-fluid">
    <div class="group">
      <img class="book-img" src="@/assets/img/bleach-book.jpg">

      <div class="text">
        <h1 class="tittle">BLEACH VOL.60 : Everything but the rain</h1>
        <p class="pengarang">Pengarang : Tsugumi ohba</p>
        <p class="tahun-terbit">Tahun terbit : 7 oktober 2008</p>
        <p class="lokasi">RAK : 1</p>
        <p class="kategori">Kategori buku : Komik</p>
        <p class="desc">Deskripsi : Deskripsi :
          Death Note 13: How to Read is an official encyclopedia-style guide to the Death Note manga series. It
          including character bios, storyline summaries, interviews with creators Tsugumi Ohba and Takeshi Obata,
          production notes, and commentaries</p>
      </div>
    </div>

    <div class="btn">
      <NuxtLink class="kembali btn rounded-1" to="/search">kembali</NuxtLink>
    </div>

  </div>
</template>

<style scoped>
.container-fluid {
  background-image: url('@/assets/img/bg-detail.png');
  width: 100%;
  height: 100%;
  padding-top: 140px;
  padding-left: 0;
  padding-right: 0;
  background-size: 1400px;
  background-blend-mode: soft-light;
}

.group {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.15);
  display: grid;
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
</style>