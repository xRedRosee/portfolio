<template>
    <NavBar></NavBar>
    <section class="detail-section-header">
        <div class="detail-section-header-image">
            <img :src="projectDetailIntroImg" class="detail-section-header-img">
        </div>
        <div class="detail-section-header-title">
            <h2 class="bigger-font-size section-header-title"> {{ projectDetailTitle }} </h2>
            <h2 class="bigger-font-size section-header-title decorative-font"> {{ projectDetailTitleType }} </h2>
        </div>
    </section>
    <section class="detail-section-intro" ref="introSection">
        <div class="detail-section-intro-techniques">
            <p class="section-default-text bold"> Techniques: </p>
            <ul class="techniques-list">
                <li v-for="(technique, index) in projectTechniques" :key="technique"
                    class="section-default-text technique-bullet-item">
                    <span class="technique-bullet"></span>
                    <span class="section-default-text" data-select="techniques-text">{{ technique }}</span>
                </li>
            </ul>
        </div>
        <div class="detail-section-intro-links" v-show="gitLink || websiteLink">
            <p class="section-default-text bold"> See more: </p>
            <LinkItem v-show="gitLink" :githubLink="true" :link="gitLink"></LinkItem>
            <LinkItem v-show="websiteLink" :githubLink="false" :link="websiteLink"></LinkItem>
        </div>
    </section>
    <section class="detail-section-about">
        <div class="detail-section-about-title" ref="detailTitle">
            <h2 class="section-header-title"> About </h2>
            <h2 class="section-header-title decorative-font"> this project </h2>
        </div>
        <div class="detail-section-about-text" ref="detailText">
            <p class="section-default-text"> {{ projectDetailText }}</p>
        </div>
    </section>
    <section class="detail-section-gallery">
        <img ref="img1" :src="projectDetailImg1" class="detail-section-gallery-image">
        <img ref="img2" :src="projectDetailImg2" class="detail-section-gallery-image">
        <img ref="img3" v-show="projectDetailImg3" :src="projectDetailImg3" class="detail-section-gallery-image">
    </section>
    <section class="detail-section-scrollup">
        <p class="section-default-text scroll-text"> Scroll </p>
        <button class="scroll-to-top" @click="scrollToTop" @mouseenter="showText" @mouseleave="hideText">
            <i class="fas fa-arrow-up" v-show="!isHovered"></i>
            <img src="../../assets/gradient-butterfly.svg" alt="butterfly" v-show="isHovered" class="butterfly-icon" />
        </button>
        <p class="section-default-text scroll-text"> up </p>
    </section>
    <ContactSection></ContactSection>
    <div class="butterfly-section">
        <img src="../../assets/gradient-butterfly.svg" ref="contactButterflyElement"
            class="contact-section-header-butterfly" alt="butterfly">
    </div>
    <CustomCursor></CustomCursor>
</template>
<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import NavBar from '@/components/NavBar.vue';
import LinkItem from '@/components/LinkItem.vue';
import ContactSection from '@/components/sections/ContactSection.vue';
import CustomCursor from '@/components/CustomCursor.vue';

gsap.registerPlugin(ScrollTrigger);

const route = useRoute();

// Animation refs
const introSection = ref(null);
const detailTitle = ref(null);
const detailText = ref(null);
const img1 = ref(null);
const img2 = ref(null);
const img3 = ref(null);
const isHovered = ref(false);

// Data refs
const pageName = ref("");
const projectDetailTitle = ref("");
const projectDetailTitleType = ref("");
const projectDetailIntroImg = ref("");
const projectTechniques = ref("");
const projectDetailText = ref("");
const gitLink = ref("");
const websiteLink = ref("");
const projectDetailImg1 = ref("");
const projectDetailImg2 = ref("");
const projectDetailImg3 = ref("");

// Media query with GSAP
let mm = gsap.matchMedia(), breakPoint = 1025;

const getData = async (pageName) => {
    // Import the JSON data
    const response = await fetch('/projects.json');

    // Set JSON data in an array
    const JsonFile = await response.json();
    const myArray = JsonFile.projects;

    // Find the correct object in the array
    for (let i = 0; i < myArray.length; i++) {
        if (myArray[i].pagename === pageName) {
            projectDetailTitle.value = myArray[i].projectDetailTitle;
            projectDetailTitleType.value = myArray[i].projectDetailTitleType;
            projectDetailIntroImg.value = myArray[i].projectImage;
            projectDetailImg1.value = myArray[i].projectDetailImg1;
            projectDetailImg2.value = myArray[i].projectDetailImg2;
            projectDetailImg3.value = myArray[i].projectDetailImg3;
            projectTechniques.value = myArray[i].projectTechniques;
            gitLink.value = myArray[i].gitLink;
            websiteLink.value = myArray[i].websiteLink;
            projectDetailText.value = myArray[i].projectDetailText;
            break;
        }
    }
};

const checkSlug = () => {
    pageName.value = route.params.project;
    getData(pageName.value);
};

const contactButterflyElement = ref(null);


const scrollToTop = () => {
    document.querySelector(".butterfly-section").style.display = "flex";

    window.scrollTo({
        top: 0,
        behavior: 'smooth',
    });

    // Move butterfly from right bottom to top left
    gsap.fromTo(contactButterflyElement.value, {
        opacity: 1,
        x: '100vw',
        y: '100vh',
        scale: 1,
    }, {
        opacity: 1,
        x: '-10vw',
        y: -200,
        duration: 3,
        ease: "power1.out",
        onComplete: () => {
            document.querySelector(".butterfly-section").style.display = "none";
        }
    });

    // Butterfly animation
    gsap.fromTo(
        contactButterflyElement.value,
        {
            scaleX: 0.4,
            rotate: -30
        },
        {
            scaleX: 1,
            ease: "power2.out",
            duration: 0.3,
            yoyo: true,
            repeat: -1,
        }
    )
};

const showText = () => {
    gsap.fromTo('.scroll-text', {
        y: 10,
    },
        {
            opacity: 1,
            y: 0,
            duration: 0.3,
            ease: 'power1.out'
        });

    isHovered.value = true;
};

const hideText = () => {
    gsap.to('.scroll-text', {
        opacity: 0,
        y: 10,
        duration: 0.3,
        ease: 'power1.in'
    });

    isHovered.value = false;
};

onMounted(() => {
    checkSlug();

    // Header title animation
    gsap.from(".detail-section-header-title", {
        opacity: 0,
        x: '-10%'
    })

    // Header image animation
    gsap.from(".detail-section-header-img", {
        opacity: 0,
        y: '-10%'
    })

    mm.add({
        isDesktop: `(min-width: ${breakPoint}px) and (prefers-reduced-motion: no-preference)`,
        isMobile: `(max-width: ${breakPoint - 1}px) and (prefers-reduced-motion: no-preference)`
    }, (context) => {
        let { isDesktop, isMobile } = context.conditions;

        if (isDesktop) {
            // ------------------------------------------- is desktop

            // Introduction section animation
            gsap.from(
                introSection.value,
                {
                    y: '-50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: introSection.value,
                        start: "top 70%",
                        end: "top 30%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                }
            );

            // Detail title
            gsap.from(
                detailTitle.value,
                {
                    y: '-50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: detailTitle.value,
                        start: "top 70%",
                        end: "top 30%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                    ease: "power1.out",
                }
            );


            // Detail text
            gsap.from(
                detailText.value,
                {
                    y: '-50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: detailText.value,
                        start: "top 70%",
                        end: "top 30%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                    ease: "power1.out",
                }
            );

            // Gallery images animations
            gsap.fromTo(
                img1.value,
                { opacity: 0, y: 50 },
                {
                    opacity: 1,
                    y: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img1.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );

            gsap.fromTo(
                img2.value,
                { opacity: 0, y: 200 },
                {
                    opacity: 1,
                    y: 100,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img2.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );

            gsap.fromTo(
                img3.value,
                { opacity: 0, y: 300 },
                {
                    opacity: 1,
                    y: 200,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img3.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );
        }

        if (isMobile) {
            // ------------------------------------------ is mobile 

            // Introduction section animation
            gsap.from(
                introSection.value,
                {
                    y: '50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: introSection.value,
                        start: "top 70%",
                        end: "top 30%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                }
            );

            // Detail title
            gsap.from(
                detailTitle.value,
                {
                    y: '50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: detailTitle.value,
                        start: "top 70%",
                        end: "top 50%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                    ease: "power1.out",
                }
            );


            // Detail text
            gsap.from(
                detailText.value,
                {
                    y: '50%',
                    opacity: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: detailText.value,
                        start: "top 70%",
                        end: "top 50%",
                        toggleActions: "play none none reverse",
                        scrub: 2,
                    },
                    ease: "power1.out",
                }
            );

            // Gallery images animations
            gsap.fromTo(
                img1.value,
                { opacity: 0, y: 50 },
                {
                    opacity: 1,
                    y: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img1.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );

            gsap.fromTo(
                img2.value,
                { opacity: 0, y: 50 },
                {
                    opacity: 1,
                    y: 10,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img2.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );

            gsap.fromTo(
                img3.value,
                { opacity: 0, y: 50 },
                {
                    opacity: 1,
                    y: 20,
                    duration: 1,
                    scrollTrigger: {
                        trigger: img3.value,
                        start: "top bottom-=100",
                        end: "top 40%",
                        toggleActions: "play none none reverse",
                        scrub: 1,
                    },
                    ease: "power1.out",
                }
            );
        }
    })
});
</script>
<style scoped>
.detail-section-header {
    height: 100vh;
    display: flex;
    align-items: center;
    position: relative;
}

.detail-section-header-image {
    position: absolute;
    z-index: 0;
    right: 0;
}

.detail-section-header-img {
    opacity: 0.5;
}

.detail-section-header-title {
    display: flex;
    flex-direction: column;
    margin-left: 10%;
    position: absolute;
    z-index: 2;
}

.section-header-title {
    font-family: var(--font-normal);
    font-weight: var(--font-normal-regular);
    font-style: italic;
    display: flex;
    flex-direction: row;
    line-height: normal;
    font-size: var(--font-size-header-big);
}

.decorative-font {
    font-family: var(--font-decorative);
    font-weight: var(--font-decorative-regular);
    line-height: normal;
    font-size: var(--font-size-header-big);
}

.bigger-font-size {
    font-size: 118px;
}

.detail-section-intro {
    margin-left: 10%;
    width: 80%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.detail-section-intro-techniques {
    width: 50%;
    display: flex;
    flex-direction: column;
    gap: 17px;
}

.techniques-list {
    display: flex;
    flex-direction: column;
    gap: 17px;
}

.technique-bullet-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 17px;
}

.technique-bullet {
    background-color: var(--color-orange);
    width: 18px;
    aspect-ratio: 1;
    border-radius: 50%;
    display: inline-block;
}

.detail-section-intro-links {
    width: 50%;
    display: flex;
    flex-direction: column;
    gap: 17px;
}

.detail-section-about {
    display: flex;
    flex-direction: row;
    align-items: start;
    margin-left: 10%;
    width: 80%;
    margin-block: 10%;
}

.detail-section-about-title {
    width: 50%;
}

.detail-section-about-text {
    width: 50%;
}

.detail-section-gallery {
    margin-left: 10%;
    width: 80%;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    margin-bottom: 20vh;
}

.detail-section-gallery-image {
    width: 30%;
}

.detail-section-scrollup {
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 20px;
    margin-bottom: 20vh;
    margin-top: 30vh;
}

.scroll-to-top {
    background: linear-gradient(to bottom, var(--color-orange), var(--color-yellow));
    color: var(--color-white);
    border: none;
    width: 50px;
    height: 50px;
    font-size: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.2s ease-in-out;
    border-radius: 50%;
    z-index: 15;
}

.scroll-to-top:hover {
    background: none;
    border: 2px solid var(--color-orange);
    color: var(--color-white);
}

.scroll-text {
    opacity: 0;
    color: var(--color-white);
}

.butterfly-icon {
    width: 22px;
    height: auto;
}

.butterfly-section {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 16;
    display: none;
    flex-direction: row;
    -webkit-backdrop-filter: blur(0.5px);
    backdrop-filter: blur(0.5px);
    background-color: #00000061;
}

.contact-section-header-butterfly {
    height: 200px;
    filter: drop-shadow(0px 15px 5px rgba(0, 0, 0, 0.2));
    opacity: 0;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .detail-section-header {
        overflow-x: hidden;
    }

    .section-header-title {
        font-size: var(--font-size-header-big-sm);
    }

    .decorative-font {
        font-size: var(--font-size-header-big-sm);
    }

    .detail-section-header-image {
        display: flex;
        justify-content: center;
        right: auto;
    }

    .detail-section-header-img {
        height: 100vh;
    }

    .detail-section-intro {
        margin-block: 10vh;
    }

    .detail-section-about {
        flex-direction: column;
        gap: 5vh;
        margin-top: 10vh;
    }

    .detail-section-about-title {
        width: 100%;
    }

    .detail-section-about-text {
        width: 100%;
    }

    .detail-section-gallery {
        flex-direction: column;
        align-items: center;
        gap: 20px;
    }

    .detail-section-gallery-image {
        width: 80%;
    }

    .detail-section-scrollup {
        margin-top: 10vh;
        margin-bottom: 5vh;
    }

    .scroll-text {
        opacity: 1;
    }
}

@media screen and (max-width: 768px) {
    .detail-section-intro {
        flex-direction: column;
        gap: 32px;
        margin-top: 10vh;
    }

    .detail-section-intro-links {
        width: 100%;
    }

    .detail-section-intro-techniques {
        width: 100%;
    }

    .detail-section-gallery {
        margin-bottom: 0;
    }

    .detail-section-gallery-image {
        width: 90%;
    }

    .detail-section-scrollup {
        margin-top: 10vh;
        margin-bottom: 5vh;
    }

    .scroll-text {
        opacity: 1;
    }
}
</style>