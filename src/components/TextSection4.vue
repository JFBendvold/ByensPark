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
                    Meter Arkitektur AS er lokalisert i Fredrikstad, men jobber med prosjekterover hele landet. Kontoret jobber med eiendomsutviklere som har både store og små oppgaver.
                </p>
                <p>
                    Meter Arkitektur AS ble opprettet 2004, og har derfor en bred portefølje med prosjekter. Tyngden av denne ligger på kontor- og logistikkbygg, som innebærer å løse kompliserte og detaljerte samfunnsfunksjoner.
                </p>
                <p>
                    Kontoret har prosjektert blant annet BAMAs hovedkvarter i Oslo, lakseoppdrettsanlegg på land i Fredrikstad og fremtidens
                    energistasjon for YX/7-eleven. I tillegg har vi skoleanlegg, barnehager,
                    boligprosjekter og hytter på listen over utførte prosjekter.
                </p>
                <p>
                    Vi legger stor vekt
                    på tverrfaglig samarbeid i arbeidsprosessen, noe vi mener sikrer det beste
                    resultat for kunder og brukere.
                </p>
                <p>
                    Byens Park er tenkt som et trygt og samlende sted for en voksen målgruppe.
Bygningen er formet rundt et fellesareal som skal brukes av beboerne,
hvor det oppfordres til felles aktiviteter. Alle leiligheter har egen balkong eller
uteplass. Alle beboere har tilgang til frisør, treningsrom, fysioterapi og
fellesstue – alt under samme tak.
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