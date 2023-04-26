<template>
    <NavBar></NavBar>
    <article class="intro-text">
        <h1 class="page-title"> Hey, <br> I'm Iris Roemermann </h1>
        <p class="page-text"> ICT & Media Design student </p>
    </article>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
export default {

}
</script>

<style lang="css">
@import url("https://use.typekit.net/xup3qvy.css");

:root {
    --headingfont: "lust-sans", sans-serif;
    --normalfont: "owners", sans-serif;
    --white: white;
    --black: black;
}

body {
    background-color: var(--black);
    margin: 0;
    padding: 0;
}

.intro-text {}

.page-title {
    font-family: var(--headingfont);
    color: var(--white);
    font-size: 60px;
    font-style: italic;
}

.page-text {
    font-family: var(--normalfont);
    color: var(--white);
    font-weight: 100;
}
</style>