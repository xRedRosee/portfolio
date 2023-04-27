<template>
    <NavBar></NavBar>
    <h1 class="page-heading"> About me </h1>
    <Introduction></Introduction>
    <h1 class="page-heading"> My skills </h1>
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
</style>