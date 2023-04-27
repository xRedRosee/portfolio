<template>
    <NavBar></NavBar>
    <main class="about-page">
        <h1 class="page-heading"> About me </h1>
        <Introduction></Introduction>
        <h1 class="page-heading"> My skills </h1>
        <section class="skills">
            <div class="skills-table">
                <div class="frontend-skills">
                    <img src="../assets/html.png" class="skills-img">
                    <img src="../assets/css.png" class="skills-img">
                    <img src="../assets/js.png" class="skills-img">
                    <img src="../assets/vue.png" class="skills-img">
                    <img src="../assets/nuxt.png" class="skills-img">
                </div>
                <div class="design-skills">
                    <img src="../assets/photoshop.png" class="skills-img">
                    <img src="../assets/illustrator.png" class="skills-img">
                    <img src="../assets/indesign.png" class="skills-img">
                    <img src="../assets/premierepro.png" class="skills-img">
                    <img src="../assets/figma.png" class="skills-img">
                </div>
            </div>
        </section>
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
.skills {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-bottom: 60px;
}

.skills-table {
    width: 90%;
    background-color: #292727;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 60px;
    gap: 20px;
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
    }

    .page-heading {
        font-size: 50px;
        font-weight: 500;
        margin-left: 0;
        width: 80%;
    }
}
</style>