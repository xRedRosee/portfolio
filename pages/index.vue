<template>
    <NavBar></NavBar>
    <article class="intro-container">
        <div class="intro-textfield">
            <h1 class="page-title"> Hey, <br> I'm Iris Roemermann </h1>
            <p class="page-text"> ICT & Media Design student </p>
        </div>
    </article>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
export default {

}
</script>

<style>
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

.intro-container {
    width: 100%;
    height: 400px;
    position: relative;
}

.intro-textfield {
    position: absolute;
    top: 50%;
}

.page-title {
    font-family: var(--headingfont);
    color: var(--white);
    font-size: 70px;
    font-style: italic;
    margin: 0;
    margin-left: 100px;
    animation: 0.5s ease-out slideInTitle;
}

.page-text {
    font-family: var(--normalfont);
    color: var(--white);
    font-weight: 100;
    font-size: 50px;
    margin-left: 100px;
    margin-top: 15px;
    animation: 0.5s ease-out slideInText;
}

@keyframes slideInTitle {
    0% {
        transform: translateX(-50%);
    }

    100% {
        transform: translateX(0);
    }
}

@keyframes slideInText {
    0% {
        transform: translateX(-100%);
    }

    100% {
        transform: translateX(0);
    }
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .page-title {
        font-size: 48px;
        margin: 0;
        margin-left: 20px;
    }

    .page-text {
        font-size: 20px;
        margin: 0;
        margin-left: 20px;
    }
}
</style>