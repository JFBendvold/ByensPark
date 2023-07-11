<script setup>
import "@/assets/textSection.css"
import { ref } from "vue";

const textSection = ref(null);
const imageSection = ref(null);

//Onscroll
window.addEventListener("scroll", () => {
    //imageSection.value.style.transform = `translateY(${window.scrollY / 2}px)`;

    //When entering the section, set the opacity to 1 from 0
    if (window.scrollY > textSection.value.offsetTop - 500) {
        textSection.value.style.opacity = 1;
    } else {
        textSection.value.style.opacity = 0;
    }
});

</script>

<template>
    <div class="textSection" id="personligomsorg" ref="textSection">
        <div class="sections">
            <div class="text-container">
                <h1>Arkitekten</h1>
                <p>
                    Meter Arkitektur AS, ved Magnus Olsen, har laget et utkast til bygningene, inn- og utvendig.
                </p>
                <p>
                    Meter Arkitektur AS er et solid lokalt firma etablert i 2001 med tilholdssted i Gamlebyen i Fredrikstad.
                </p>
                <p>
                    Siden oppstart har de tegnet alt fra eneboliger og hytter til større boligområder og industribygg. 
                    Dermed har de erfaring med å samarbeide 
                    med privatpersoner og store eiendomsutviklere.
                </p>
                <p>
                    Gjennom disse prosjektene har Meter Arkitektur AS opparbeidet seg bred
                    erfaring med passivhus, og innehar kompetanse til å prosjektere aktivhus
                    eller «økohus» hvor lavt energibruk i byggefasen også har stort fokus.
                </p>
            </div>
            <div class="img-container" ref="imageSection">
                <a href="https://www.meter-as.no/" class="clickable" target="_blank">
                    <img src="../assets/img/meter-logo.png" alt="Personlig Omsorg logo" class="logo clickable" />
                </a>
            </div>
        </div>
    </div>
</template>