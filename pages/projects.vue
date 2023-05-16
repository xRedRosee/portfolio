<template>
    <NavBar></NavBar>
    <h1 class="page-heading"> Projects </h1>
    <section class="projects">
        <ul class="projects-container">
            <ProjectCard v-for="p in projectList" :key="p.id" :ProjectName="p.name" :Img="p.img" :ProjectTools="p.tools"
                :ProjectDesc="p.description" :Mockup="p.imgmockup" :page="p.page"></ProjectCard>
        </ul>
    </section>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import ProjectCard from '/././components/ProjectCard.vue';

export default {
    data() {
        return {
            projectList: []
        }
    },
    methods: {
        async getData() {
            const JsonFile = await import('~/src/projects.json');

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
    animation: 0.5s ease-out opacitychange;
    margin-bottom: 50px;
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
</style>