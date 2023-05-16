<template>
    <NavBar></NavBar>
    <main class="about-page">
        <h1 class="page-heading"> About me </h1>
        <Introduction></Introduction>
        <h1 class="page-heading"> My skills </h1>
        <section class="skills">
            <div class="skills-table">
                <div class="frontend-skills">
                    <img src="../assets/html.png" class="skills-img" alt="HTML 5 logo">
                    <img src="../assets/css.png" class="skills-img" alt="CSS logo">
                    <img src="../assets/js.png" class="skills-img" alt="JavaScript logo">
                    <img src="../assets/vue.png" class="skills-img" alt="Vue logo">
                    <img src="../assets/nuxt.png" class="skills-img" alt="Nuxt logo">
                </div>
                <div class="design-skills">
                    <img src="../assets/photoshop.png" class="skills-img" alt="Adobe Photoshop logo">
                    <img src="../assets/illustrator.png" class="skills-img" alt="Adobe Illustrator logo">
                    <img src="../assets/indesign.png" class="skills-img" alt="Adobe InDesign logo">
                    <img src="../assets/premierepro.png" class="skills-img" alt="Adobe Premiere Pro logo">
                    <img src="../assets/figma.png" class="skills-img" alt="Figma logo">
                </div>
            </div>
        </section>
    </main>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import Introduction from '~/components/Introduction.vue';
import AOS from 'aos'
import 'aos/dist/aos.css'

export default {
    methods: {
    }
}
</script>

<style>
@import url("https://unpkg.com/aos@2.3.1/dist/aos.css");

.about-page {
    margin-top: 60px;
}

.page-heading {
    font-family: var(--headingfont);
    color: var(--white);
    font-size: 50px;
    font-weight: 500;
    margin-left: 80px;
    font-style: italic;
    animation: 0.5s ease-out slideInTitle;
}

@keyframes slideInTitle {
    0% {
        opacity: 0;
        transform: translateX(-50%);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
    }
}

@-webkit-keyframes slideInTitle {
    0% {
        transform: translateX(-50%);
    }

    100% {
        transform: translateX(0);
    }
}

/* -------------------------------------------- skills table */
.skills {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-bottom: 60px;
    animation: 0.5s ease-out opacitychange;
}

@keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

@-webkit-keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

.skills-table {
    width: 90%;
    background-color: #292727;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 60px;
    gap: 40px;
}

.frontend-skills {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 100%;
}

.design-skills {
    margin-bottom: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 100%;
}

.skills-img {
    width: 12%;
    height: auto;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .about-page {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 0;
    }

    .page-heading {
        font-size: 50px;
        font-weight: 500;
        margin-left: 0;
        width: 80%;
    }

    /* -------------------------------------------- skills table */
    .skills-table {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        margin-bottom: 60px;
        gap: 20px;
    }

    .frontend-skills {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        width: 100%;
        align-items: center;
        gap: 20px;
        margin-top: 20px;
        margin-bottom: 20px;
    }

    .design-skills {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        width: 100%;
        gap: 20px;
        align-items: center;
        margin-top: 20px;
        margin-bottom: 20px;
    }

    .skills-img {
        width: 60%;
        height: auto;
    }
}
</style>