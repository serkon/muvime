<template>
    <div class="legacy w-100 d-flex flex-row">
        <div class="muvi d-flex flex-row">
            <div>
                <img src="../assets/images/logo.png" />
            </div>
            <div class="mx-5">
                <span>© 2021 Tübitak. All rights reserved.</span>
            </div>
        </div>
        <div class="terms">
            <span class="mx-3">Terms of Use</span>
            <span class="mx-3">API Terms of Use</span>
            <span class>Privacy Policy</span>
        </div>
    </div>
</template>
<script lang="ts" >
import { defineComponent } from 'vue';
export default defineComponent({
    name: "App"
});
</script>
<style scoped>
.legacy {
    position: absolute;
    height: 7%;
    top: 255%;
    font-family: inter;
    font-style: normal;
}
.muvi {
    position: absolute;
    left: 5%;
    top:25%;
    font-weight: 800;
    font-size: 18px;
    line-height: 22px;
    color: #545454;
}
.terms {
    position: absolute;
    right: 5%;
    top:25%;
    font-size: 16px;
    line-height: 150%;
    color: #000000;
}
</style>