<script setup>
import "@/assets/TitleHeader.css"
import '@fortawesome/fontawesome-free/css/all.css'
import pdf from "@/assets/Prospekt.pdf"

const prospect = () => {
    let password = window.prompt("Passord for å laste ned prospektet", "");

    if (password !== "Bjørn") {
        alert("Feil passord");
        return;
    }

    window.open(pdf, "_blank");
}

</script>

<template>
    <div class="title-header">
        <h1>
            Et innovativt boligkonsept med<br/>tjenester
            fra Personlig Omsorg AS
        </h1>
        <h2>
            EN TRYGG TILVÆRELSE MED
            FRIHET OG VALGMULIGHETER
        </h2>
        <a href="#about" class="clickable scroll-btn">
            <a href="#about" class="clickable">
                <i class="fas fa-chevron-down clickable"></i>
            </a>
        </a>
        <button class="prospect-btn clickable" @click="prospect">
            Last ned prospekt <i class="fas fa-lock"></i>
        </button>
    </div>
</template>