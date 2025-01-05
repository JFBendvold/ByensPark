<script setup>
import TitleHeader from '@/components/TitleHeader.vue'
//import MouseFX from '@/components/MouseFX.vue'
import TextSection0 from '../components/TextSection0.vue';
import TextSection1 from '../components/TextSection1.vue';
import TextSection2 from '../components/TextSection2.vue';
import TextSection3 from '../components/TextSection3.vue';
import TextSection4 from '../components/TextSection4.vue';
import TextSection5 from '../components/TextSection5.vue';
import ContactForm from '../components/ContactForm.vue';
import PresentationModal from '../components/presentation/PresentationModal.vue';
</script>

<template>
  <main>
    <TitleHeader />
    <TextSection1 />
    <TextSection0 />
    <TextSection3 />
    <TextSection2 />
    <TextSection4 />
    <TextSection5 />
    <ContactForm />
    <PresentationModal />
  </main>
  <!--
  <MouseFX />
  -->
</template>
