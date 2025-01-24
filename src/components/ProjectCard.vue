<template>
    <a class="project-card" :href="projectLink" data-component="project-card">
        <div class="project-card-image-container" ref="projectImageContainer">
            <img alt="project image" class="project-card-image" :src="projectImage" ref="projectImageElement">
        </div>
        <article class="project-card-text-container">
            <div class="project-card-header">
                <h2 class="project-card-title" ref="projectTitleElement"> {{ projectTitle }} </h2>
                <a :href="projectLink" class="project-card-link">
                    <img alt="open link icon" class="project-card-link-image" src="../assets/arrow-link.svg"
                        ref="linkImage">
                </a>
            </div>
            <div class="project-card-techniques">
                <p class="section-default-text" data-select="techniques-text"> Techniques: </p>
                <ul class="techniques-list">
                    <li v-for="(technique, index) in projectTechniques" :key="technique" class="technique-item">
                        <span class="section-default-text" data-select="techniques-text">{{ technique }}</span>
                        <span v-if="index < projectTechniques.length - 1"
                            class="project-card-techniques-divider"></span>
                    </li>
                </ul>
            </div>
        </article>
    </a>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';

const props = defineProps({
    projectLink: String,
    projectTitle: String,
    projectImage: String,
    projectTechniques: Array,
})

gsap.registerPlugin(ScrollTrigger);

const projectImageElement = ref(null);
const projectTitleElement = ref(null);
const techniquesDivider = ref(null);
const linkImage = ref(null);
const projectImageContainer = ref(null);

// Media query with GSAP
let mm = gsap.matchMedia(), breakPoint = 1025;

onMounted(() => {
    const techniquesTexts = document.querySelectorAll("[data-select='techniques-text']");

    // MatchMedia for different screen sizes
    mm.add({
        isDesktop: `(min-width: ${breakPoint}px) and (prefers-reduced-motion: no-preference)`,
        isMobile: `(max-width: ${breakPoint - 1}px) and (prefers-reduced-motion: no-preference)`
    }, (context) => {
        let { isDesktop, isMobile } = context.conditions;

        // Desktop
        if (isDesktop) {
            // Project image animatiom
            gsap.fromTo(
                projectImageElement.value,
                { opacity: 0.5, width: '20vw' },
                {
                    opacity: 1,
                    duration: 1,
                    width: '30vw',
                    scrollTrigger: {
                        trigger: projectImageElement.value,
                        start: "top 80%",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 0.5,
                    },
                }
            );

            // Project title animation
            gsap.fromTo(
                projectTitleElement.value,
                { opacity: 0.5, fontSize: '50px', },
                {
                    opacity: 1,
                    duration: 1,
                    fontSize: '80px',
                    scrollTrigger: {
                        trigger: projectTitleElement.value,
                        start: "top 80%",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 0.5,
                    },
                }
            );
        }

        // Mobile
        if (isMobile) {
            // Project image animatiom
            gsap.fromTo(
                projectImageElement.value,
                { opacity: 0.5, width: '40vw' },
                {
                    opacity: 1,
                    duration: 1,
                    width: '60vw',
                    scrollTrigger: {
                        trigger: projectImageElement.value,
                        start: "top 80%",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 0.5,
                    },
                }
            );

            // Project title animation
            gsap.fromTo(
                projectTitleElement.value,
                { opacity: 0.5, fontSize: '6vmin', },
                {
                    opacity: 1,
                    duration: 1,
                    fontSize: '10vmin',
                    scrollTrigger: {
                        trigger: projectTitleElement.value,
                        start: "top 80%",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 0.5,
                    },
                }
            );
        }
    })

    // Link image animation
    gsap.fromTo(
        linkImage.value,
        { opacity: 0.5, },
        {
            opacity: 1,
            duration: 1,
            scrollTrigger: {
                trigger: linkImage.value,
                start: "top 80%",
                end: "top 40%",
                toggleActions: "play none none reverse",
                scrub: true,
            },
        }
    );

    // Techniques text animation
    techniquesTexts.forEach((techniqueText) => {
        gsap.fromTo(
            techniqueText,
            { opacity: 0.5, },
            {
                opacity: 1,
                duration: 1,
                scrollTrigger: {
                    trigger: techniqueText,
                    start: "top 80%",
                    end: "top 40%",
                    toggleActions: "play none none reverse",
                    scrub: true,
                },
            }
        );
    })

    // Technique divider animatiom
    gsap.fromTo(
        techniquesDivider.value,
        { opacity: 0.5, },
        {
            opacity: 1,
            duration: 1,
            scrollTrigger: {
                trigger: techniquesDivider.value,
                start: "top 80%",
                end: "top 40%",
                toggleActions: "play none none reverse",
                scrub: true,
            },
        }
    );
});
</script>
<style scoped>
.project-card {
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 50vh;
    gap: 20px;
    text-decoration: none;
}

.project-card-image-container {
    width: auto;
}

.project-card-image {
    width: 30vw;
    border-radius: 8px;
}

.project-card-text-container {
    width: 60%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
}

.project-card-header {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding-right: 10px;
}

.project-card-title {
    font-size: 80px;
    font-family: var(--font-normal);
    font-weight: var(--font-normal-bold);
    color: var(--text-color-light);
}

.project-card-link-image {
    height: 60px;
}

.project-card-techniques {
    display: flex;
    flex-direction: row;
    gap: 17px;
    align-items: center;
}

.techniques-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    align-items: center;
    gap: 10px;
}

.technique-item {
    display: flex;
    align-items: center;
    gap: 10px;
}

.project-card-techniques-divider {
    background-color: var(--color-orange);
    width: 18px;
    aspect-ratio: 1;
    border-radius: 50%;
    display: inline-block;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .project-card {
        height: auto;
        flex-direction: column;
        gap: 8px;
        border-bottom: 1px solid rgba(255, 255, 255, 0.359);
    }

    .project-card-text-container {
        width: 100%;
    }

    .project-card-link-image {
        width: 9vmin;
    }

    .project-card-techniques-divider {
        width: 2vw;
    }
}
</style>