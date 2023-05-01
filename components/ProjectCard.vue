<template>
    <li class="project-card">
        <img class="project-img" :src="Img">
        <figcaption class="project-text">
            <h2 class="project-name"> {{ ProjectName }}</h2>
            <a href="" class="see-more"></a>
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
    height: 300px;
    width: 300px;
    background-color: red;
}

.project-img {}

.project-text {}

.project-name {}

.see-more {}
</style>