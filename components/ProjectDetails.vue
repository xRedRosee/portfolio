<template>
    <div class="project-detail">
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
    name: "ProjectDetails",
    props: {
        ProjectName: String,
        Mockup: String,
        ProjectTools: String,
        ProjectDesc: String
    },
}
</script>
<style>
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

/* .close-btn {
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
} */

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
    display: flex;
    justify-content: center;
    align-items: center;
}

.detail-img {
    width: 90%;
    height: auto;
}

.detail-text {
    width: 50%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
}

.detail-tools {
    color: rgb(152, 152, 152);
    font-family: var(--normalfont);
    margin-top: 20px;
    text-align: left;
    width: 80%;
    font-size: 21px;
    font-weight: normal;
}

.detail-desc {
    color: var(--white);
    font-family: var(--normalfont);
    text-align: left;
    width: 80%;
    font-size: 21px;
    font-weight: normal;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .project-detail {
        overflow: auto;
        align-items: center;
    }

    .detail-section {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 30px;
    }

    .detail-name {
        margin-left: 0;
        margin-top: 70px;
    }

    .img-container {
        width: 100%;
    }

    .detail-img {
        width: 95%;
    }

    .detail-text {
        width: 100%;
    }
}
</style>