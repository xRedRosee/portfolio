<template>
    <NavBar></NavBar>
    <h1 class="page-heading"> Projects </h1>
    <section class="projects">
        <ul class="projects-container">
            <ProjectCard v-for="p in projectList" :key="p.id" :ProjectName="p.name" :Img="p.img" :ProjectTools="p.tools"
                :ProjectDesc="p.description" :Mockup="p.imgmockup" :slug="p.slug"></ProjectCard>
        </ul>
    </section>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import ProjectCard from '/././components/ProjectCard.vue';
const JsonFile = await import('~/src/projects.json');

export default {
    data() {
        return {
            projectList: []
        }
    },
    methods: {
        async getData() {
            this.projectList = JsonFile.Projects;
        }
    },
    mounted() {
        this.getData()
    }
}

</script>

<style>
.stop-scrolling {
    height: 100%;
    overflow: hidden;
}

.projects {
    width: 100%;
    display: flex;
    justify-content: center;
}

.projects-container {
    width: 90%;
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 25px;
    flex-wrap: wrap;
}
</style>