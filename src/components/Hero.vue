<template>
  <div class="hero1 w-100" v-if="show">
    <div class="d-flex justify-content-center">
      <input
        v-model="search"
        type="text"
        class="search form-control"
        placeholder="Search for a movie, person or genre"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
      />
      <button
        class="SearchBtn btn btn-danger"
        style="margin-top:7px;"
        @click="handleClik"
        type="button"
        id="button-addon2"
      >Search</button>
    </div>
  </div>

  <div class="hero2" v-else>
    <div class="d-flex justify-content-center">
      <input
        v-model="search"
        type="text"
        class="search form-control"
        placeholder="Search for a movie, person or genre"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
      />
      <button
        class="SearchBtn btn btn-danger"
        @click="handleClik"
        type="button"
        id="button-addon2"
      >Search</button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { defineEmits, ref } from "vue";
let search = ref();
let show = ref();
const emitSearch = defineEmits(['actionCaptured']) // Search içindeki veriyi yakalayıp gönderme kısmı
const handleClik = () => {                         
  emitSearch('actionCaptured', search.value);
  show.value = true;
}
</script>
<style scoped>
.hero1 {
  /* background */
  position: absolute;
  height: 30%;
  top: 10%;
  background: url("../assets/images/background.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  right: 0;
  left: 0;
/* Body ve html olarak Vue.app içerisinde genel tanımlamıştım 
fakat istediğim görüntüye ulaşamayınca yazı fontunda her component içinde kullandım. */
  font-family: inter;
}
.hero2 {
  /* background */
  position: absolute;
  height: 60%;
  top: 10%;
  background: url("../assets/images/background.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  right: 0;
  left: 0;

   font-family: inter;
}


.search {
  /* Search */
  position: absolute;
  height: 65px;
  width: 90%;
  top: 40%;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 3px;
}
.SearchBtn {
  position: absolute;
  width: 85px;
  height: 37px;
  top: 44%;
  right: 6%;
  background: #e22a2a;
  border-radius: 3px;
}
</style>