<template>
    <NuxtLink :to="page" variant="primary" class="projectlink">
        <li class="project-card">
            <img class="project-img" :src="Img">
            <figcaption class="project-text">
                <h2 class="project-name"> {{ ProjectName }}</h2>
                <button class="see-more"> See more &rarr;</button>
            </figcaption>
        </li>
    </NuxtLink>
</template>

<script>
export default {
    name: "ProjectCard",
    setup() {
        const route = useRoute()
    },
    data() {
        return {
            modalAlreadyOpen: false,
        };
    },
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
        page: String,
    },
    // methods: {
    //     SeeDetail() {
    //         // open modal
    //         this.modalAlreadyOpen = true;
    //         const body = document.querySelector('body');
    //         body.classList.add('stop-scrolling');
    //     },
    //     CloseModal() {
    //         // close modal
    //         this.modalAlreadyOpen = false;
    //         const body = document.querySelector('body');
    //         body.classList.remove('stop-scrolling');
    //     }
    // }
}
</script>

<style>
.stop-scrolling {
    height: 100%;
    overflow: hidden;
}

.projectlink {
    text-decoration: none;
}

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
    padding: 0;
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
    .page-heading {
        font-size: 50px;
        font-weight: 500;
        margin-left: 0;
        width: 90%;
        text-align: center;
    }

    /* --------------------------------- project detail pop up */
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