<script setup>
import "@/assets/textSection.css"
import { ref } from "vue";

const textSection = ref(null);
const imageSection = ref(null);

const showMore = ref(false);

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
            <div class="img-container" ref="imageSection">
                <a href="https://personligomsorg.no/" class="clickable" target="_blank">
                    <img src="../assets/img/PO-logo.png" alt="Personlig Omsorg logo" class="logo clickable" />
                </a>
            </div>
            <div class="text-container">
                <h1>Personlig Omsorg AS er tjenesteleverandør</h1>
                <p>
                    Vi har siden 2007 levert tjenestene våre til personer i hele Østfold. Vi har sett og lært hva seniorbefolkningen ønsker av tjenester og hvordan de skal utføres for at hverdagen skal bli så bra som mulig.
Stadig oftere mottar vi henvendelser om vi har tilrettelagte boliger eller omsorgsboliger. Vi ønsker å møte
denne etterspørselen, slik vi har gjort ved å videreutvikle tjenestene våre gjennom mange år.De siste
årene har vi lagt ned store ressurser på å utvikle tjenester og tilbud vi mener seniorbefolkningen kan nyte
godt av.
                </p>
                <p>
                    Grunnlaget for dette prospektet, er våre erfaringer knyttet opp mot funksjonelle boformer
for seniorer. Vi har sett på det «beste» fra ulike boformer i Norden.
                </p>
                <p>
                    Personlig Omsorg har startet opp flere prosjekter knyttet til vår virksomhet, som har blitt solgt videre som
solide, selvstendige bedrifter (eks. Ren Bolig, Optimal Assistanse (nå: Ecura)).
                </p>
                <p v-show="showMore">
                    Vi har solid faglig erfaring, da våre ansatte har lang fartstid i den private og offentlige helsetjenesten som
sykepleiere, vernepleiere, hjelpepleiere og hjemmehjelper.
                </p>
                <p v-show="showMore">
                    <strong>I dag finnes det ikke et tilsvarende botilbud i Østfold. Vi ønsker med dette å dekke et behov som er
sterkt etterspurt.</strong>
                </p>
                <div class="showMore" @click="showMore = !showMore" v-show="!showMore">
                    <p v-if="showMore">Vis mindre</p>
                    <p v-else>Vis mer</p>
                </div>
            </div>
        </div>
    </div>
</template>