<script setup>
import { ref } from 'vue'
import "@/assets/presentationModal.css"
import '@fortawesome/fontawesome-free/css/all.css'
import StairsPresentation from './StairsPresentation.vue';

const presenting = ref(false) // Ref for the modal

const present = () => {
    /*
    let password = window.prompt("Passord for presentasjon", "");

    if (password !== "Bjørn") {
        alert("Feil passord");
        return;
    }
    */

    presenting.value = true
}

</script>

<template>
    <div :class="['presentationModal', presenting.valueOf() ? 'show' : '']">
        <div class="modal-content">
            <StairsPresentation v-if="presenting" />
        </div>
        <button class="closeButton" @click="presenting = false">
            <i class="fas fa-times"></i>
        </button>
    </div>
    <button class="presentButton" @click="present">
        <span class="material-symbols-outlined">
            pageview
        </span>
    </button>
</template>