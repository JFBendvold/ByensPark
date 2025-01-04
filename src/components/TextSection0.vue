<script setup>
import "@/assets/textSection.css"
import { ref } from "vue";

const textSection = ref(null);

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
    <div class="textSection" id="about" ref="textSection">
        <div class="sections">
            <div class="full-text-container">
                <h1>
                    VI ØNSKER Å FOREBYGGE ENSOMHET OG UTENFORSKAP
                </h1>
                <p>
                    Dette er et økende problem i hele samfunnet.
                </p>
                <p>
                    Vi har sett og erfart at mange som blir pensjonister
eller må slutte å jobbe av andre grunner, ofte kjenner på ensomhet og følelsen av å ikke være til
nytte.
                </p>
                <p>
                    Med prosjektet vårt ønsker vi å motvirke dette.
                </p>
                <p><strong>
                    Derfor har vi planlagt tjenestetilbud
                    og aktiviteter som skal virke inkluderende, skape samhold og mestring.</strong>
                </p>
            </div>
        </div>
    </div>
</template>