<template>
    <section class="about" id="about" ref="about">
        <h2 class="section-header-title" data-select="header-title"> Hey, </h2>
        <h2 class="section-header-title" data-select="header-title">I'm Iris Roemermann! </h2>
        <div class="about-section-container">
            <article class="about-section-article">
                <div>
                    <p class="section-default-text" data-select="section-text">
                        A 20 year old student living in Limburg, the Netherlands that's
                        currently studying <span class="highlighted">ICT & Media Design</span>
                        at Fontys University of Applied Sciences.</p>
                </div>
                <div>
                    <p class="section-default-text" data-select="section-text">
                        During my studies I developed a big <span class="highlighted">passion</span></p>
                    <p class="section-default-text" data-select="section-text">
                        for everything interaction design related: </p>
                    <p class="section-default-text" data-select="section-text">
                        from working with <span class="highlighted">Adobe</span> to front end </p>
                    <p class="section-default-text" data-select="section-text">
                        developing with <span class="highlighted">Vue</span>!</p>
                </div>

                <div>
                    <p class="section-default-text" data-select="section-text">
                        My current skills include <span class="highlighted">Figma</span>, <span
                            class="highlighted">JavaScript</span>, </p>
                    <p class="section-default-text" data-select="section-text">
                        <span class="highlighted">TypeScript</span>,<span class="highlighted"> Vue</span> and <span
                            class="highlighted">Adobe</span> programs
                        such as
                    </p>
                    <p class="section-default-text" data-select="section-text">
                        <span class="highlighted">InDesign</span> and <span class="highlighted">Illustrator</span>.
                    </p>
                    <p class="section-default-text" data-select="section-text"> I also have experience in mobile
                        development, including working with <span class="highlighted">Flutter</span> and
                        <span class="highlighted">Swift.</span>
                    </p>
                </div>
            </article>
            <div class="about-section-arrow">
                <span class="arrow-line"></span>
                <div class="arrow-pointer-container">
                    <span class="arrow-pointer-line left"></span>
                    <span class="arrow-pointer-line right"></span>
                </div>
            </div>
            <div class="about-section-image-container">
                <img class="about-section-image" alt="image of me" src="../../assets/image-me.png"
                    data-select="section-image">
            </div>
        </div>
        <div class="skills-section-container">
            <SkillBubble skill-image='/logo-vue.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-js.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-ts.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-figma.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-id.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-ai.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-ps.png' data-select="skill-item" />
            <SkillBubble skill-image='/logo-pr.png' data-select="skill-item" />
        </div>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import SkillBubble from '../SkillBubble.vue';

gsap.registerPlugin(ScrollTrigger);

const about = ref(null)

// Media query with GSAP
let mm = gsap.matchMedia(), breakPoint = 1025;

onMounted(() => {
    const sectionHeaderTexts = about.value.querySelectorAll("[data-select='header-title']")
    const sectionDefaultTexts = about.value.querySelectorAll("[data-select='section-text']")
    const skillItems = about.value.querySelectorAll("[data-select='skill-item']")
    const sectionImage = about.value.querySelector("[data-select='section-image']")

    // Title animation
    sectionHeaderTexts.forEach((text) => {
        gsap.fromTo(text, {
            opacity: 0
        }, {
            scrollTrigger: {
                trigger: text,
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

    // Section text animation
    sectionDefaultTexts.forEach((text) => {
        gsap.fromTo(text, {
            opacity: 0.3
        },
            {
                scrollTrigger: {
                    trigger: text,
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

    // Arrow animation
    gsap.fromTo('.arrow-line',
        {
            height: '0%'
        },
        {
            scrollTrigger: {
                trigger: '.arrow-line',
                start: "top 98%",
                end: "bottom 0%",
                toggleActions: "restart pause reverse pause",
                scrub: true,
            },
            height: '100%',
        })

    // MatchMedia for different screen sizes
    mm.add({
        isDesktop: `(min-width: ${breakPoint}px) and (prefers-reduced-motion: no-preference)`,
        isMobile: `(max-width: ${breakPoint - 1}px) and (prefers-reduced-motion: no-preference)`
    }, (context) => {
        let { isDesktop, isMobile } = context.conditions;

        // Desktop
        if (isDesktop) {
            gsap.fromTo(sectionImage, {
                opacity: 0,
                height: '0px'
            }, {
                scrollTrigger: {
                    trigger: sectionImage,
                    start: "top 80%",
                    end: "top 50%",
                    toggleActions: "restart none reverse none",
                    scrub: 1,
                },
                opacity: 1,
                height: '450px',
            });
        }

        // Mobile
        if (isMobile) {
            gsap.fromTo(sectionImage, {
                opacity: 0,
                width: '0px'
            }, {
                scrollTrigger: {
                    trigger: sectionImage,
                    start: "top 80%",
                    end: "top 50%",
                    toggleActions: "restart none reverse none",
                    scrub: 1,
                },
                opacity: 1,
                width: '70vw',
            });
        }
    })

    // Skill items animation
    skillItems.forEach((skillItem) => {
        gsap.fromTo(skillItem, {
            xPercent: -1050,
        }, {
            scrollTrigger: {
                trigger: skillItem,
                start: "top 70%",
                end: "top 50%",
                toggleActions: "restart pause reverse pause",
                scrub: 2,
            },
            rotate: 360,
            xPercent: 0,
            duration: 1,
            ease: "power1.out",
        })
    })
})
</script>
<style scoped>
.about {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    width: 100%;
    padding-top: 60px;
}

.section-header-title {
    margin-left: 10%;
}

.about-section-container {
    display: flex;
    margin-left: 10%;
    width: 80%;
    justify-content: space-between;
    height: 60vh;
}

.about-section-article {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    width: 45%;

}

.highlighted {
    color: var(--color-yellow)
}

.about-section-arrow {
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: center;
    width: 10%;

}

.arrow-line {
    display: block;
    height: 90%;
    width: 4px;
    background: #FF6600;
    background: -moz-linear-gradient(top, #FF6600 0%, #ffe500 100%);
    background: -webkit-linear-gradient(top, #FF6600 0%, #ffe500 100%);
    background: linear-gradient(to bottom, #FF6600 0%, #ffe500 100%);
    border-radius: 20px;
}

.arrow-pointer-container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-end;
    gap: 9px;
    margin-top: -15px;
}

.arrow-pointer-line {
    display: block;
    height: 22px;
    width: 4px;
    background-color: var(--color-yellow);
    border-radius: 20px;
}

.left {
    transform: rotate(-45deg);
}

.right {
    transform: rotate(45deg);
}

.about-section-image-container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 45%;
}

.about-section-image {
    height: 500px,
}

.skills-section-container {
    margin-top: 15vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 22px;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .about-section-container {
        flex-direction: column-reverse;
        align-items: center;
        height: auto;
    }

    .about-section-article {
        width: 90%;
        gap: 22px;
        margin-top: 5vh;
    }

    .about-section-arrow {
        display: none;
    }

    .about-section-image-container {
        width: 100%;
        margin-top: 5vh;
        /* Calculation for the image height based on vw */
        height: calc(70vw * 272 / 245);
    }

    .skills-section-container {
        gap: 6px;
        margin-top: 5vh;
        flex-wrap: wrap;
    }
}
</style>