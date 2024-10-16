<script setup>
import { ref } from 'vue'
import "@/assets/stairsPresentation.css"
import '@fortawesome/fontawesome-free/css/all.css'

// Show select words modal
const showModal = ref(false)

// Steps data
const steps = ref([
    {
        number: 1,
        title: "Attraktive og aktive lokalsamfunn",
        wordList: [
            "Fellesarealer",
            "Trimrom",
            "P-plass",
            "Vaktmester",
            "Slippe vedlikehold",
            "Gjestehybel",
            "Bod",
            "Etablert boligområde",
            "Kollektivtransport",
            "Butikker",
            "Apotek",
            "Kafé",
        ]
    },
    {
        number: 2,
        title: "Helsefremmende og forebyggende aktivitet",
        wordList: [
            "Hage/uteplass",
            "Tilsyn av leilighet",
            "Frisør",
            "Fotpleie",
            "Aktiviteter",
            "Trimrom",
            "Fysioterapi",
            "Rehabilitering",
            "Fellesaktiviteter",
            "Sosialt samvær",
            "Felles interesser",
            "Husvert",
        ]
    },
    {
        number: 3,
        title: "Tidlig innsats",
        wordList: [
            "Sosialt samvær",
            "Felles interesser",
            "Husvert",
            "Felleskap",
            "Samtaler",
            "Forebygge ensomhet/isolasjon",
            "Hjemmehjelp",
            "Universal utforming",
            "Velferdsteknologi",
            "Aktiviteter",
            "Fellesaktiviteter",
            "Individuell oppfølging",
        ]
    },
    {
        number: 4,
        title: "Meningsfull og inkluderende hverdag",
        wordList: [
            "Føle seg til nytte",
            "Universal utforming",
            "Forebygge ensomhet/isolasjon",
            "Velferdsteknologi",
            "Husvert",
            "Gjestehybel",
            "Sosialt samvær",
            "Aktiviteter",
            "Fellesområder",
            "Grupper",
            "Aktiv",
            "Sosial",
        ]
    },
    {
        number: 5,
        title: "Tilpasset bolig - Kommunalt disponerte boliger",
        wordList: [
            "Individuell oppfølging",
            "Sosialt samvær",
            "Slippe vedlikehold",
            "Forebygge ensomhet/isolasjon",
            "Velferdsteknologi",
            "Husvert",
            "Universal utforming",
        ]
    },
    {
        number: 6,
        title: "Leve godt i eget hjem",
        wordList: [
            "Pleie- og omsorgstjenester",
            "Bo hjemme lenger",
            "Gjestehybel",
            "Velferdsteknologi",
            "Individuell oppfølging",
            "Hjemmehjelp",
            "Vaktmester",
            "Følgetjeneste",
            "Forebygge ensomhet/isolasjon",
            "Stort tjeneste- og aktivitetstilbud",
            "Sosial",
            "Universal utforming",
        ]
    },
    {
        number: 7,
        title: "Helsehjelp til hjemmeboende - Hjemmesykepleie fra kommunen",
        wordList: [
            "Innkjøp",
            "Individuell oppfølging",
            "Pleie- og omsorgstjenester",
            "Bo hjemme lenger",
            "Velferdsteknologi",
            "Fysioterapi",
            "Trimrom",
            "Rehabilitering",
        ]
    },
    {
        number: 8,
        title: "Boliger med fellesfunksjoner",
        wordList: [
            "Fysioterapi",
            "Frisør",
            "Fotpleie",
            "Trimrom",
            "Felleskap",
            "Sosialt samvær",
            "Gjestehybel",
            "Velferdsteknologi",
            "Innkjøp",
            "Hage/uteplass",
            "Fast personale",
            "Husvert",
            "Individuell oppfølging",
            "Fellesområder",
        ]
    },
    {
        number: 9,
        title: "Tidsavgrenset opphold - Tidligere hjem fra rehabilitering og sykehus",
        wordList: [
            "Individuell oppfølging",
            "Fysioterapi",
            "Trimrom",
            "Rehabilitering",
            "Tilsynstjeneste",
            "Følgetjeneste",
            "Fellesaktiviteter",
            "Husvert",
            "Samhold",
            "Sosial",
            "Hjemmehjelp",
        ]
    },
    {
        number: 10,
        title: "Boliger med mulighet for døgntjenester",
        wordList: [
            "Helse- og omsorgstjenester",
            "Hjemmehjelp",
            "Individuell oppfølging",
            "Fellesarealer",
            "Velferdsteknologi",
            "Universal utforming",
            "Sosialt samvær",
            "Tilsynstjeneste",
            "Felleskap",
            "Husvert",
        ]
    },
    {
        number: 11,
        title: "Institusjon, døgnpleie/-tilsyn",
        wordList: []
    },
    {
        number: 12,
        title: "Forsterket bolig/institusjon",
        wordList: []
    }
])
const reversedSteps = ref([...steps.value].reverse())

// Every word in the steps, not duplicates
const allWords = ref([...new Set(steps.value.flatMap(step => step.wordList))])

// Percentage of how much each step matches the user's input
const stepMatches = ref([
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0,
    0.0
])

// Selected words from the user
const selectedWords = ref([])

// Function to calculate the step matches based on the selected words, if the step contains all the selected words it gets a 100% match, if it contains none it gets a 0% match
// If a lower level contains all the selected words, the higher levels should also be marked as relevant.
const calculateStepMatches = () => {
    stepMatches.value = stepMatches.value.map(() => 0.0) // Reset all values to 0

    selectedWords.value.forEach(word => {
        let hit = -1;
        for (let i = 0; i < steps.value.length; i++) {
            //console.log("checking index", i)
            if (hit >= 0) {
                //console.log("hit for index", i)
                let value = (1 - 0.2 * (i - hit)) / selectedWords.value.length
                if (value < 0) {
                    value = 0
                }
                stepMatches.value[i] += value
            } else if (steps.value[i].wordList.includes(word)) {
                hit = i
                stepMatches.value[i] += 1 / selectedWords.value.length
            }
        }
    })

    // The steps above the stepBorder should be marked as irrelevant (0% match)
    stepMatches.value = stepMatches.value.map((value, index) => index >= stepBorder.value ? 0 : value)

    // Only keep the top 3 highest stepMatches, the rest should be 0
    let sortedStepMatches = [...stepMatches.value].sort((a, b) => b - a)
    stepMatches.value = stepMatches.value.map(value => sortedStepMatches.indexOf(value) < 3 ? value : 0)
};

// Add a word to the selected words
const addSelectedWord = (word) => {
    if (!selectedWords.value.includes(word)) {
        selectedWords.value.push(word)
        calculateStepMatches()
    }
}

// Remove a word from the selected words
const removeSelectedWord = (word) => {
    selectedWords.value.splice(selectedWords.value.indexOf(word), 1)
    calculateStepMatches()
}

// Step border, every step after the border should be marked as irrelevant
const stepBorder = ref(10)
</script>

<template>
    <div class="stairsPresentation">
        <div class="selectedWords" v-if="selectedWords.length > 0">
            <div v-for="word in selectedWords" :key="word" class="selectedWord" @click="removeSelectedWord(word)">
                {{ word }}
            </div>
        </div>
        <div class="steps">
            <div v-for="step in reversedSteps" :key="step.number" :class="['step', step.number > stepBorder ? 'irrelevant' : '']" :style="{ backgroundColor: stepMatches[step.number-1] > 0.0 ? 'rgba(150, 255, 200, ' + stepMatches[step.number-1]**2 + ')' : 'rgba(255, 255, 255, 0)' }">
                <div class="stepNumber">{{ step.number }}</div>
                <div class="stepContent">
                    <div class="stepTitle">{{ step.title }}</div>
                    <div class="wordList">
                        <div v-for="(word, index) in step.wordList" :key="word" class="word" @click="addSelectedWord(word)">
                            {{ word }}<span v-if="index < step.wordList.length - 1">,</span>
                        </div>
                    </div>
                    <div class="stepMatch" v-if="selectedWords.length > 0 && stepMatches[step.number-1] > 0.0 && step.number <= stepBorder">
                        <div class="stepMatchBar" :style="{ width: stepMatches[step.number-1] * 100 + '%' }"></div>
                    </div>
                </div>
            </div>
        </div>
        <button class="searchButton" @click="showModal = true">
            <i class="fas fa-search"></i>
        </button>
        <div class="modal" v-if="showModal" @click="showModal = false">
            <div class="modalContent" @click.stop>
                <div class="modalHeader">
                    <button class="closeModalButton" @click="showModal = false">
                        <i class="fas fa-times"></i>
                    </button>
                    <div class="modalTitle">
                        Velg relevante ord
                    </div>
                </div>
                <div class="modalBody">
                    <div class="wordList">
                        <div v-for="word in allWords" :key="word" :class="['word', selectedWords.includes(word) ? 'selected' : '']" @click="selectedWords.includes(word) ? removeSelectedWord(word) : addSelectedWord(word)">
                            {{ word }}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>