<template>
    <NavBar></NavBar>
    <main class="contact-page">
        <h1 class="page-heading"> Get in touch with me </h1>
        <p class="page-heading-smalltext">Want to have a talk with me about a new challenge? <br>
            Feel free to contact me on my email or social media! </p>
    </main>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
export default {

}
</script>

<style>
.contact-page {
    margin-top: 60px;
}

.page-heading-smalltext {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .contact-page {
        margin-top: 0;
    }
}
</style>