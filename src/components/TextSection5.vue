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
                    Hvorfor sammerbeide med oss for dette prosjektet?
                </h1>
                <p>
                    Vi har bred erfaring innen bruk velferdsteknologi og tilrettelegging av aktiviteter og oppfølgning rettet mot seniorer
                </p>
                <p>
                    30+ dedikerte ansatte som har bred erfaring rettet mot seniorer
                </p>
                <p>
                    Helsefaglig kompetanse, frisør, fotpleie, fysioterapeut og vaktmester
                </p>
                <p>
                    Gjennomtenkte tjenestetilbud
                </p>
                <p>
                    Økonomisk og faglig gjennomføringsevne
                </p>
                <p>
                    Stort kundegrunnlag og interesseliste for prosjektet
                </p>
            </div>
        </div>
    </div>
</template>