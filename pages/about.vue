<template>
    <NavBar></NavBar>
    <main class="about-page">
        <h1 class="page-heading"> About me </h1>
        <Introduction></Introduction>
        <h1 class="page-heading"> My skills </h1>
        <div class="skills-table">
            <img src="../assets/html-logo.svg" class="skills-img">
            <img src="../assets/css-logo.svg" class="skills-img">
            <img src="../assets/js-logo.svg" class="skills-img">
            <img src="../assets/vue-logo.svg" class="skills-img">
            <img src="../assets/nuxt-logo.svg" class="skills-img">
            <img src="../assets/photoshop-logo.svg" class="skills-img">
            <img src="../assets/illustrator-logo.svg" class="skills-img">
            <img src="../assets/indesign-logo.svg" class="skills-img">
            <img src="../assets/premierepro-logo.svg" class="skills-img">
            <img src="../assets/figma-logo.svg" class="skills-img">
        </div>
    </main>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import Introduction from '~/components/Introduction.vue';

export default {

}
</script>

<style>
.page-heading {
    font-family: var(--headingfont);
    color: var(--white);
    font-size: 50px;
    font-weight: 500;
    margin-left: 80px;
    font-style: italic;
}

/* -------------------------------------------- skills table */
.skills-table {}

.skills-img {}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .about-page {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .page-heading {
        font-size: 50px;
        font-weight: 500;
        margin-left: 0;
        width: 80%;
    }
}
</style>