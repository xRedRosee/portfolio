<template>
    <li class="project-card">
        <img class="project-img" :src="Img">
        <figcaption class="project-text">
            <h2 class="project-name"> {{ ProjectName }}</h2>
            <a href="" class="see-more"> See more &rarr;</a>
        </figcaption>
    </li>
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
}

.see-more {
    color: white;
    font-family: var(--normalfont);
    font-size: 20px;
    margin: 0;
    text-decoration: none;
    cursor: pointer;
}

.see-more:visited {
    color: white;
    font-family: var(--normalfont);
    font-size: 20px;
    margin: 0;
    text-decoration: none;
}
</style>