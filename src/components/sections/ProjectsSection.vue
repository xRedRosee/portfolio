<template>
    <section class="projects" id="projects" ref="projects">
        <h2 class="section-header-title" ref="sectionTitle"> My work </h2>
        <ul class="projects-section-cards-list">
            <li class="projects-section-cards-list-item" v-for="(project) in projectList" :key="project.id">
                <ProjectCard :project-title="project.projectTitle" :project-image="project.projectImage"
                    :project-techniques="project.projectTechniques" :project-link="project.slug" />
            </li>
        </ul>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import ProjectCard from '../ProjectCard.vue';

gsap.registerPlugin(ScrollTrigger);

const projects = ref(null)
const sectionTitle = ref(null)
const projectList = ref([])

const initProjects = async () => {
    try {
        const response = await fetch('/projects.json');
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        const data = await response.json();

        projectList.value = data.projects;
    } catch (error) {
        console.error('Error fetching project cards:', error);
    }
}

onMounted(() => {
    initProjects()

    // Title animation
    gsap.fromTo(sectionTitle.value, {
        opacity: 0
    }, {
        scrollTrigger: {
            trigger: sectionTitle.value,
            start: "top 60%",
            end: "top 40%",
            toggleActions: "restart pause reverse pause",
            scrub: true,
        },
        opacity: 1,
        duration: 1,
        ease: "power1.out",
    })
})
</script>
<style scoped>
.projects {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    width: 100%;
    padding-top: 60px;
    margin-top: 10vh;
}

.section-header-title {
    margin-left: 10%;
}

.projects-section-cards-list {
    margin-left: 10%;
    width: 80%;
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-top: 3vh;
    margin-bottom: 15vh;
}

.projects-section-cards-list-item {
    list-style: none;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .projects {
        margin-top: 4vh;
    }

    .projects-section-cards-list {
        gap: 42px;
        margin-bottom: 0;
    }

}
</style>