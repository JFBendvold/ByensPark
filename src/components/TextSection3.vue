<script setup>
import "@/assets/textSection.css"
import { ref } from "vue";

const textSection = ref(null);
const imageSection = ref(null);

const showMore1 = ref(false);
const showMore2 = ref(false);
const showMore3 = ref(false);

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
            <div class="text-container">
                <h1>
                    VI ØNSKER Å BIDRA TIL EN <br/>TRYGG,
                    SOSIAL OG AKTIV HVERDAG
                </h1>
                <h2>
                    Trygg
                </h2>
                <ul>
                    <li>ved å ha husvert tilgjengelige til faste tidspunkter hver dag
                    </li>
                    <li>ved at alle leilighetene har alarm og porttelefon med kamera
                    </li>
                    <li>ved å ha velferdsteknologiske løsninger i hver boenhet som bl.a. kan varsle betjeningen ved fall
                    </li>
                    <li v-show="showMore1">det vil være hjertestarter plassert i resepsjonsområdet
                    </li>
                    <li v-show="showMore1">ved at Personlig Omsorg AS er lokalisert i bygget
                    </li>
                    <div class="showMoreList" @click="showMore1 = !showMore1" v-show="!showMore1">
                        <p>Vis mer</p>
                    </div>
                </ul>
                <h2>
                    Sosial
                </h2>
                <ul>
                    <li>ved å ha fellesarealer med stue, tv-stue og bibliotekkrok
                    </li>
                    <li>ved å ha kjøkken og spisestue som er tilgjengelige for alle beboere
                    </li>
                    <li>ved å ha fellesarealer med sittegrupper utendørs
                    </li>
                    <li v-show="showMore2">ved å arrangere og legge til rette for sosiale sammenkomster, turer og aktiviteter
                    </li>
                    <li v-show="showMore2">ved å ha personale til stedet i felleslokalene som koker kaffe og tilbyr noe å bite i
                    </li>
                    <div class="showMoreList" @click="showMore2 = !showMore2" v-show="!showMore2">
                        <p>Vis mer</p>
                    </div>
                </ul>
                <h2>
                    Aktiv
                </h2>
                <ul>
                    <li>ved å ha fri tilgang til trimrom og aktivitets-/hobbyrom
                    </li>
                    <li>ved å arrangere og legge til rette for turer og aktiviteter
                    </li>
                    <li>ved å ha uteområder som er tilrettelagt for aktiviteter
                    </li>
                    <li v-show="showMore3">ved å ha tilgang til fysioterapeut faste dager i uka i fellesområdet
                    </li>
                    <div class="showMoreList" @click="showMore3 = !showMore3" v-show="!showMore3">
                        <p>Vis mer</p>
                    </div>
                </ul>
            </div>
            <div class="img-container" ref="imageSection">
                <img src="../assets/img/5.jpg" alt="Byens Park">
            </div>
        </div>
    </div>
</template>