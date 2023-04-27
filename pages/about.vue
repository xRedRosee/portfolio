<template>
    <NavBar></NavBar>
    <main class="about-page">
        <h1 class="page-heading"> About me </h1>
        <Introduction></Introduction>
        <h1 class="page-heading"> My skills </h1>
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