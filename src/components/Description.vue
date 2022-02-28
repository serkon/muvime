<template>
  <div>
    <div v-if="push === undefined" class="description w-100 d-flex justify-content-center">
      <button class="descriptionBtn">Get Premium</button>
      <div class="advantageText">The TMDB Advantage</div>
      <h2 class="millionsText">Millions of movies, TV shows and people to discover. Explore now.</h2>
      <div class="MovieDatabaseText">
        <h6>
          The Movie Database (TMDB) is a community built movie and TV database.
          Every piece of data has been added by our amazing community dating
          back to 2008. TMDb's strong international focus and breadth of data is
          largely unmatched and something we're incredibly proud of. Put simply,
          we live and breathe community and that's precisely what makes us
          different.
        </h6>
      </div>
    </div>
    <div v-else class="description2 w-95" style="margin-top:60px;">
      <div class="SearchHeader">Search Result</div>
      <div>
        <p
          class="d-flex justify-content-end"
          style="font-weight: 600; font-size: 18px; line-height: 26px;
color: #6B6B6B;"
        >12 Records</p>
      </div>
      <div class="row row-cols-6 d-flex">
        <div v-for="(i, index) in pushService" :key="index">
          <div class="card mx-2" style=" border: white">
            <img
              :src="'https://image.tmdb.org/t/p/w500' + i.poster_path"
              class="card-img-top"
              style="border-radius: 7px"
            />
            <div class="card-body">
              <p
                class="card-text"
                style="display: flex-end; color: #545454; font-weight: 600;font-size: 20px;line-height: 120%;"
              >{{ i.title }}</p>
              <!-- Gelen servisten tür verisine ulaşılamadığım için bu veriyi yansıttım. -->
              <p
                class="card-text"
                style="font-weight: bold; font-size: 12px; line-height: 150%; display: flex; align-items: flex-end;
            color: #828282;"
              >{{ i.original_title }}</p>

              <div class="d-flex flex-row">
                <p
                  class="card-text"
                  style="font-weight: normal; font-size: 12px; line-height: 15px; color: #828282;"
                >{{ i.release_date }}</p>
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
  </div>
</template>
<script lang="ts" setup>
import { ref, defineProps } from "vue";
const props = defineProps<{
  push: any;
  pushService: any;
}>();
</script>
<style scoped>
.description {
  /* Description */
  position: absolute;
  height: 45%;
  top: 70%;
  right: 0;
  left: 0;
  font-family: inter;
  text-align: center;
}
.description2 {
  /* Description */
  position: absolute;
  height: 65%;
  top: 40%;
  right: 5%;
  left: 5%;

  font-family: inter;
  text-align: center;
}
.descriptionBtn {
  position: absolute;
  padding: 6px 12px;
  width: 137px;
  height: 38px;
  border: none;
  background: #02b2e3;
  border-radius: 3px;
  top: 17%;
  color: #ffffff;
  flex-grow: 0;
  margin: 0px 10px;
}
.advantageText {
  position: absolute;
  top: 35%;
  color: #b8b8b8;
}
.millionsText {
  position: absolute;
  top: 50%;
  color: #424242;
}
.MovieDatabaseText {
  position: absolute;
  top: 70%;
  left: 17%;
  right: 17%;
  color: #545454;
}
.SearchHeader {
  font-weight: 800;
  font-size: 40px;
  line-height: 48px;
  display: flex;
  align-items: center;
  letter-spacing: -0.03em;
  color: #555555;
}
</style>