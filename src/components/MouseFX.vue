<script setup>
import "@/assets/mouseFX.css"
import { ref, onMounted } from 'vue'

const mouseFX = ref(null)
const mouseFXTrail = ref(null)

// Make the mouse follow the cursor
const mouseFollow = (e) => {
    checkClickable(e)
    mouseFX.value.style.left = e.pageX + 'px'
    mouseFX.value.style.top = e.pageY + 'px'

    mouseFXTrail.value.style.left = e.pageX + 'px'
    mouseFXTrail.value.style.top = e.pageY + 'px'
}

onMounted(() => {
    document.addEventListener('mousemove', mouseFollow)
})

//Check if the object the mouse is hovering over contains the class 'clickable'
const checkClickable = (e) => {
    if (e.target.classList.contains('clickable')) {
        mouseFX.value.classList.add('main-clickable')
        mouseFXTrail.value.classList.add('trail-clickable')
    } else {
        mouseFX.value.classList.remove('main-clickable')
        mouseFXTrail.value.classList.remove('trail-clickable')
    }

    if (e.target.classList.contains('input')) {
        mouseFX.value.classList.add('main-input')
        mouseFXTrail.value.classList.add('trail-input')
    } else {
        mouseFX.value.classList.remove('main-input')
        mouseFXTrail.value.classList.remove('trail-input')
    }
}

</script>

<template>
    <div class="mouseFX-dot" ref="mouseFX"></div>
    <div class="mouseFX-trail" ref="mouseFXTrail"></div>
</template>