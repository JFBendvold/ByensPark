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
                <h1>Personlig Omsorg AS</h1>
                <p>
                    Vi er en privat tjenesteyter som ble etablert i 2007. 
                </p>
                <p>
                    Siden den gang har vi tilbudt praktisk bistand som hjemmehjelp, følgetjenester, avlastning,
                    fotpleie, frisør og helse- og omsorgstjenester til mange private hjem i hele Østfold.
                </p>
                <p>
                    Vi har tilbudt tjenester gjennom det offentlige via fritt brukervalg.
                </p>
                <p>
                    Vårt motto og verdigrunnlag er basert på: Respekt - Trygghet - Glede.
                </p>
                <p>
                    Nå ønsker vi å integrere våre tjenester i boliger for voksne 50+. Vi vil også ha våre egne kontorer
                    samt personale tilgjengelige i fellesarealene.
                </p>
                <p>
                    Vi har erfart at mange verdsetter privatlivet sitt, men samtidig ønsker seg en enklere hverdag og
                    en trygg arena med mulighet for sosialt samvær og aktiviteter. 
                </p>
                <p>
                    I prospektet vil vi presentere hvordan tjenestene, til Personlig Omsorg AS, og boligformen
                    vil kunne gi deg friheten til å skape en trygg og fleksibel hverdag med mange valgmuligheter. 
                </p>
            </div>
            <div class="img-container" ref="imageSection">
                <a href="https://personligomsorg.no/" class="clickable" target="_blank">
                    <img src="../assets/img/PO-logo.png" alt="Personlig Omsorg logo" class="logo clickable" />
                </a>
            </div>
        </div>
    </div>
</template>