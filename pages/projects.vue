<template>
    <NavBar></NavBar>
    <h1 class="page-title"> Projects </h1>
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

.page-title {
    font-family: var(--headingfont);
    color: var(--white);
}
</style>