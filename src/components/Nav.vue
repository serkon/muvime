<template>
    <div class="navBar w-100 d-flex flex-row">
        <div>
            <img style="margin-left:80%; " src="../assets/images/logo.png" />
        </div>
        <div style="margin-left:10rem; font-size:18px">
            <button type="button" class="btn btn-light mx-3">
                <b>Filmler</b>
            </button>
            <button type="button" class="btn btn-light mx-3">
                <b>Diziler</b>
            </button>
            <button type="button" class="btn btn-light mx-3">
                <b>Kişiler</b>
            </button>
            <button
                type="button"
                class="btn btn-light mx-5"
                style="background: rgba(0, 0, 0, 0.1);border-radius: 3px;">
                <b>Daha Fazla+</b>
            </button>
        </div>
        <div class="profile d-flex flex-row">
            <button
                type="button"
                class="btn btn-light mx-3"
                style="border: 1px solid #A6A6A6;
box-sizing: border-box; border-radius: 3px; height:35px;
color: #A6A6A6;"
            >EN</button>
            <div>
                <h6 style="font-weight: bold; font-size: 14px;">Serkan Konakçı</h6>
                <p style="font-weight: 300; font-size: 10px;">FrontEnd Developer</p>
            </div>
            <img
                class="mx-2"
                style="width: 32px; height: 32px;"
                alt="profilPhoto"
                src="../assets/images/serkanbey.png"
            />
        </div>
    </div>
</template>
<script lang="ts" >
import { defineComponent } from 'vue';
export default defineComponent({
    name: "App"
});
</script>
<style stoped>
.navBar {
    /* Nav Css Bilgileri */
    position: absolute;
    height: 10%;
    top: 2%;
    right: 0%;
    left: 0%;
    /* İstenildiği üzere font-family interdir. İncele kısmından inceleyebilirsiniz. */
    font-family: inter;
    font-style: normal;
    text-align: center;
}
.profile {
    position: absolute;
    right: 5%;
}
</style>