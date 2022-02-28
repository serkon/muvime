<template>
  <div class="movie w-95 " style="margin-top:5rem;">
    <div v-if="push === undefined">
      <div class="popularHeader">
        What's Popular
      </div>
      <div class="d-flex justify-content-end">
        <button
          type="button"
          class="btn"
          style="font-weight: 600; font-size: 18px; color: rgba(9, 9, 9, 0.4); border: 1px solid rgba(0, 0, 0, 0.4);"
        >More</button>
      </div>
    </div>
    <div class="row row-cols-6 d-flex" style="margin-top:20px;">
      <div v-for="(i, index) in imglist" :key="index">
        <div class="card mx-2" style=" margin-top:50px;  border: white;">
          <img
            :src="'https://image.tmdb.org/t/p/w500' + i.poster_path"
            class="card-img-top"
            style="border-radius: 7px;"
          />
          <div class="card-body">
            <p class="card-text" style="display: flex-end; color: #545454; font-weight: 600;font-size: 20px;line-height: 120%;">{{ i.title }}</p>
            <p class="card-text" style="font-weight: bold; font-size: 12px; line-height: 150%; display: flex; align-items: flex-end;
            color: #828282;">{{ i.original_title }}</p>
            <div class="d-flex flex-row">
              <p class="card-text" style="font-weight: normal; font-size: 12px; line-height: 15px; color: #828282;">{{ i.release_date }}</p>
              <button
                type="button"
                class="btn btn-dark rounded-5"
                style="margin-left:9px; height:22px;"
              >
                <p style="height:13px; font-size:8px; text-align: center;">{{ i.popularity }}</p>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {
  onMounted,
  onUpdated,
  ref,
  defineProps,
} from "vue";
import axios from "axios";
let imglist = ref();
let serviceData = ref();
// Props ile searchin içindeki gönderilen veri çekildi
const props = defineProps<{
  push: any;
}>();
const emit = defineEmits(['servieData']) 
const handleClik = () => {
  emit('servieData', serviceData.value);
}

onMounted(async () => {
  // popüler veri listesi ilk çalıştığında ekrana yansıtılan
  await axios
    .get(
      "https://api.themoviedb.org/3/trending/all/day?api_key=e6da8f6ab1d5059c5a68581dd5a973c0"
    )
    .then(
      (response) => (
        (imglist.value = response.data.results),
        // servisten gelen verilerin bozuk olması durumunda burdan değişiklik yaparak diğer verileri görebilirsiniz.
        (imglist.value = imglist.value.slice(0, 6))
      )
    );
});
onUpdated(async () => {
  // popüler veri listesi her tetiklendiğinde içindekini çalıştırır.
  if (props.push === undefined) {
    await axios
      .get(
        "https://api.themoviedb.org/3/trending/all/day?api_key=e6da8f6ab1d5059c5a68581dd5a973c0"
      )
      .then(
        (response) => (
          (imglist.value = response.data.results),
          // servisten gelen verilerin bozuk olması durumunda burdan değişiklik yaparak diğer verileri görebilirsiniz.
          (imglist.value = imglist.value.slice(0, 6))
        )
      );
  }
  //search sonucunda gelen veri listesi
  else {
    await axios
      .get(
        "https://api.themoviedb.org/3/search/movie?api_key=e6da8f6ab1d5059c5a68581dd5a973c0&query=" +
        props.push
      )
      .then(
        (response) => (
          (imglist.value = response.data.results),
          (serviceData.value = imglist.value.slice(0, 6)),
          (imglist.value = imglist.value.slice(6, 12))
        )
      );
  }
  handleClik();
});
</script>
<style scoped>
.movie {
  position: absolute;
  height: 100%;
  top: 115%;
  right: 5%;
  left: 5%;

  font-family: inter;
  font-style: normal;
}
.popularHeader {
  /* What's Popular */
  position: absolute;
  font-weight: 800;
  font-size: 40px;
  line-height: 48px;
  display: flex;
  align-items: center;
  letter-spacing: -0.03em;
  color: #555555;
  
}
</style>