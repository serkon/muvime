<!-- eslint-disable vue/no-multiple-template-root -->
<template>
  <NavVue />
  <HeroVue @actionCaptured="handleAction" />
  <DescriptionVue :push="search" :pushService="pushServiceData"/>
  <MovieList :push="search" @servieData="servieData"/>
  <LegacyVue />
  <FooterVue
    :list1="['Guidelines', 'Discussions', 'Leaderboard', 'Twitter']"
    :list2="[
      'Contribution Bible',
      '3rd Party Applications',
      'Add New Movie',
      'Add New TV Show',
    ]"
    :list3="[
      'About TMDB',
      'Contact Us',
      'Support Forums',
      'API',
      'System Status',
    ]"
  />
</template>

<script lang="ts" setup>
import LegacyVue from "./components/Legacy.vue";
import FooterVue from "./components/Footer.vue";
import NavVue from "./components/Nav.vue";
import HeroVue from "./components/Hero.vue";
import DescriptionVue from "./components/Description.vue";
import MovieList from './components/MovieList1.vue';

import { ref } from "vue";
let search = ref();
let pushServiceData = ref();
const handleAction = (e: any) => {
  search.value = e;
};
const servieData =(e: any)=>{
  pushServiceData.value = e;
}
</script>

<style  >
@import "https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css";
@import "https://fonts.googleapis.com/icon?family=Material+Icons";


</style>
