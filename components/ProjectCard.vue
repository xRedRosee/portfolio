<template>
    <li class="project-card">
        <img class="project-img" :src="Img">
        <figcaption class="project-text">
            <h2 class="project-name"> {{ ProjectName }}</h2>
            <button class="see-more"> See more &rarr;</button>
        </figcaption>
    </li>
    <div class="project-detail">
        <button class="close-btn"> &#10005; </button>
        <h1 class="detail-name"> {{ ProjectName }}</h1>
        <div class="detail-section">
            <figure class="img-container">
                <img :src="Mockup" class="detail-img">
            </figure>
            <article class="detail-text">
                <p class="detail-tools"> {{ ProjectTools }}</p>
                <p class="detail-desc"> {{ ProjectDesc }}</p>
            </article>
        </div>
    </div>
</template>

<script>
export default {
    name: "ProjectCard",
    props: {
        Img: {
            type: String,
            default: '',
            // required: true
        },
        ProjectName: String,
        Mockup: {
            type: String,
            default: '',
        },
        ProjectTools: String,
        ProjectDesc: String,
    }
}
</script>

<style scoped>
.project-card {
    margin: 0;
    padding: 0;
    list-style: none;
    cursor: pointer;
}

.project-img {
    height: 400px
}

.project-text {}

.project-name {
    color: white;
    font-family: var(--normalfont);
    font-size: 20px;
    font-weight: normal;
    margin: 0;
    margin-top: 10px;
}

.see-more {
    color: white;
    font-family: var(--normalfont);
    font-size: 20px;
    margin: 0;
    text-decoration: none;
    cursor: pointer;
    margin-top: 5px;
    background: none;
    border: none;
    outline: none;
}

.see-more:visited {
    color: white;
    font-family: var(--normalfont);
    font-size: 20px;
    margin: 0;
    text-decoration: none;
}

/* --------------------------------- project detail pop up */
.project-detail {
    width: 100%;
    height: 100%;
    background-color: var(--black);
    position: fixed;
    top: 0;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.close-btn {
    color: white;
    font-family: var(--normalfont);
    font-size: 30px;
    font-weight: 100;
    margin: 0;
    text-decoration: none;
    cursor: pointer;
    margin-top: 5px;
    background: none;
    border: none;
    outline: none;
    position: absolute;
    right: 20px;
}

.detail-name {
    font-size: 50px;
    font-weight: 500;
    margin-left: 80px;
    text-align: center;
    color: var(--white);
    font-family: var(--headingfont);
    font-style: italic;
    margin-top: 60px;
}

.detail-section {
    width: 100%;
    display: flex;
    flex-direction: row;
}

.img-container {
    margin: 0;
    padding: 0;
    width: 50%;
}

.detail-img {
    width: 100%;
}

.detail-text {
    width: 50%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.detail-tools {
    color: var(--white);
    font-family: var(--normalfont);
    margin-top: 20px;
    text-align: left;
}

.detail-desc {
    color: var(--white);
    font-family: var(--normalfont);
    text-align: left;
}
</style>