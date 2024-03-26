<template>
  <div class="wrapper">
    <div class="background"></div>
    <div class="search input-group input-group-sm p-0">
    </div>
    <input type="text" class="form-control" aria-label="Small" placeholder=" search here...">
    <div class="book mt-5">
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/death-note-book.jpg" alt="">
      </NuxtLink>
    </div>
    <div class="book mt-5">
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
      </NuxtLink>
      <NuxtLink to="detail">
        <img class="book-img" src="@/assets/img/bleach-book.jpg" alt="">
        <div class="text-img">Bleach vol.60 : Everything but the rain</div>
      </NuxtLink>
    </div>
    <div class="btn">
      <NuxtLink class="kembali btn rounded-1" to="/history">kembali</NuxtLink>
    </div>
  </div>
</template>
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
}

.form-control {
  margin-top: 0;
  width: 100%;
  padding: 0;
}

input {
  margin: 0;
  padding: 0;
  position: relative;
  font-weight: 500;
  color: black;
  opacity: 0.7;
  position: fixed;
  top: 21%;
  border-radius: 3px;
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

.book {
  padding-left: 50px;
}

.book-img {
  width: 130px;
  height: 200px;
  border: 10px solid rgba(0, 0, 0, 0.7);
}

.text-img {
  background-color: #ffffff95;
  color: black;
  width: 130px;
  height: 200px;
  opacity: 0;
  position: relative;
  bottom: 50%;
  font-style: italic;
  font-size: 20px;
  font-weight: 900;
  text-align: center;
  text-decoration: none;
}

.text-img:hover {
  opacity: 1;
  transition: 1s ease;
}

.book {
  display: grid;
  grid-template-columns: auto auto auto auto auto auto;
}
</style>