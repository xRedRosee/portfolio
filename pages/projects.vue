<template>
    <NavBar></NavBar>
    <h1 class="page-heading"> Projects </h1>
    <section class="projects">
        <ul class="project-container">
            <ProjectCard v-for="p in projectList" :key="p.id" :Name="p.name" :Img="p.img"></ProjectCard>
        </ul>
    </section>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import ProjectCard from '/././components/ProjectCard.vue';
const JsonFile = await import('~/public/projects.json');

export default {
    data() {
        return {
            projectList: []
        }
    },
    methods: {
        async getData() {
            this.projectList = JsonFile.Projects;
            console.log(this.projectList)
        }
    },
    mounted() {
        this.getData()
    }
}

// let projects = []

// function displayProjects() {
//     fetch('projects.json')
//         .then(res => res.json())
//         .then(data => projects.push(data.Projects))
//     console.log(projects)
// }

// displayProjects()

</script>

<style>
.projects {}

.projects-contrainer {
    margin: 0;
    padding: 0;
    list-style: none;
}
</style>