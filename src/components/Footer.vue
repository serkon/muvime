<template>
  <div class="row footer w-100">
    <div class="col-3 mt-5">
      <h5 class="mb-4">{{ thebasicsheader }}</h5>
      <div :key="index" v-for="(val, index) in list3">{{ val }}</div>
    </div>
    <div class="col-3 mt-5">
      <h5 class="mb-4">{{ getinvolvedheader }}</h5>
      <div :key="index" v-for="(val, index) in list2">{{ val }}</div>
    </div>
    <div class="col-3 mt-5">
      <h5 class="mb-4">{{ communityheader }}</h5>
      <div :key="index" v-for="(val, index) in list1">{{ val }}</div>
    </div>
    <div class="col-2 mx-auto mt-5">
      <h5 class="mb-4">{{ socialheader }}</h5>
      <div class="social d-flex flex-row">
        <div class="mx-2">
          <img alt="facebook" src="../assets/icons/facebook.png" />
        </div>
        <div class="mx-2">
          <img alt="instagram" src="../assets/icons/instagram.png" />
        </div>
        <div class="mx-2">
          <img alt="twitter" src="../assets/icons/twitter.png" />
        </div>
        <div>
          <img alt="youtube" src="../assets/icons/youtube.png" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, ref } from "vue";
const communityheader = ref("COMMUNITY");
const props = defineProps<{
  list1: string[];
  list2: string[];
  list3: string[];
}>();

const getinvolvedheader = ref("GET INVOLVED");
const thebasicsheader = ref("THE BASICS");
const socialheader = ref("SOCIAL");
</script>

<style scoped>
.footer {
  /* Footer */
  position: absolute;
  height: 40%;
  left: 0px;
  right: 0;
  top: 215%;
  /* background */
  background: #032541;
  text-align: right;
  color: #ffffff;
  font-family: inter;
  font-size: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 150%;
}
.social {
  position: absolute;
  right: 5%;
}
</style>