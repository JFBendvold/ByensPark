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
    <div class="textSection" id="about" ref="textSection">
        <div class="sections">
            <div class="img-container" ref="imageSection">
                <img src="../assets/img/fasade.jpg" alt="Byens Park">
            </div>
            <div class="text-container">
                <h1>
                    OM BOLIGKONSEPTET
                </h1>
                <p>
                    Personlig Omsorg sitt boligkonsept er en boligform der vi legger alt til rette for at byens seniorer
skal ha muligheter til å bestemme selv hvordan hverdagen skal være. Både i form av hvilke
aktiviteter man ønsker å prioritere, og hvilke fritidsinteresser man ønsker å bruke tid på.
                </p>
                <p>
                    Altså; en helsefremmende livsstilsbolig.
                </p>
                <p>
                    Vi tilbyr valgmulighetene er slik tilværelse kan by på. Lettstelte, lyse selveierleiligheter med
livsløpsstandard og muligheten til å kunne være aktiv og sosial i lett tilgjengelige felleslokaler.
                </p>
                <p>
                <strong>Alt skal være innomhus slik at du ikke trenger å kle på deg yttertøy for å være sosial og aktiv.</strong>
                </p>
                <p>
                    Det vil være profesjonell oppfølging og vedlikehold av hus og hage, samt ansatte som kan bistå
med stell av leiligheten eller organisere aktiviteter og felles turer.
                </p>
                <p>
                    Personlig Omsorg sitt boligkonsept er en boligform for aktive seniorer, som hver dag vil ønskes
velkommen av vår husvert. Kaffe, noe å bite i og dagens avis tilbys i fellesarealet. Om ønskelig,
vil man få ytterligere oppfølging fra dyktige medarbeidere i Personlig Omsorg AS.
                </p>
            </div>
        </div>
    </div>
</template>