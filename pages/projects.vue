<template>
    <NavBar></NavBar>
    <h1 class="page-heading"> Projects </h1>
    <section class="projects">
        <ul class="project-container">
            <ProjectCard></ProjectCard>
        </ul>
    </section>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import ProjectCard
    from '~/components/ProjectCard.vue';
export default {

}
</script>

<style>
.projects {}

.projects-contrainer {
    margin: 0;
    padding: 0;
    list-style: none;
}
</style>