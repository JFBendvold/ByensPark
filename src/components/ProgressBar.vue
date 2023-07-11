<script setup>
import "@/assets/ProgressBar.css"
import { ref } from "vue";

const fill = ref(null);

//Onscroll
window.addEventListener("scroll", () => {
    let winScroll = document.body.scrollTop || document.documentElement.scrollTop;
    let height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    let scrolled = (winScroll / height) * 100;
    fill.value.style.width = scrolled + "%";
});

</script>

<template>
    <div class="progress-container">
        <div class="progress-bar-fill" ref="fill"></div>
    </div>
</template>