<script setup>
import "@/assets/ContactForm.css"
import { ref, onMounted } from "vue";

const contactForm = ref(null);
const form = ref(null);
const submitStatus = ref(null);

//Onscroll
window.addEventListener("scroll", () => {
    //imageSection.value.style.transform = `translateY(${window.scrollY / 2}px)`;

    //When entering the section, set the opacity to 1 from 0
    if (window.scrollY > contactForm.value.offsetTop - 500) {
        contactForm.value.style.opacity = 1;
    } else {
        contactForm.value.style.opacity = 0;
    }
});

//On mounted
onMounted(() => {
    //Form submit
    form.value.addEventListener("submit", (e) => {
        e.preventDefault();

        //Send form
        fetch("https://formspree.io/f/xeqbqlkd", {
            method: "POST",
            body: new FormData(form.value),
            headers: {
                Accept: "application/json",
            },
        })
            .then((res) => {
                if (res.ok) {
                    submitStatus.value.style.opacity = 1;
                    form.value.style.opacity = 0;
                    form.value.style.pointerEvents = "none";
                    form.value.style.userSelect = "none";
                    form.value.style.height = "0px";
                }
            })
            .catch((error) => {
                console.log(error);
            });
    });
});

</script>

<template>
    <div class="contact-form" ref="contactForm">
        <h2>
            Er du en utbygger som ønsker å bli med på laget?
        </h2>
        <form action="https://formspree.io/f/xeqbqlkd" method="POST" ref="form">
            <input type="text" name="name" placeholder="Navn" class="input" />
            <input type="email" name="email" placeholder="E-post" class="input" />
            <input type="text" name="phone" placeholder="Telefon" class="input" />
            <textarea name="message" placeholder="Melding" class="input"></textarea>
            <button type="submit" class="clickable">Send melding</button>
        </form>
        <p class="submit-status" ref="submitStatus">
            Meldingen er sendt! Vi tar kontakt med deg så fort som mulig.
        </p>
    </div>
</template>