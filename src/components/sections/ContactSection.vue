<template>
    <section class="contact" id="contact">
        <div class="contact-section-header">
            <div class="contact-section-header-title" ref="contactTitle">
                <h2 class="section-header-title"> Get in <p class="decorative-font">
                        touch
                    </p>
                </h2>
                <h2 class="section-header-title"> with <p class="decorative-font">
                        me
                    </p>
                </h2>
            </div>
            <img src="../../assets/gradient-butterfly.svg" ref="contactButterflyElement"
                class="contact-section-header-butterfly" alt="butterfly">
        </div>
        <div class="contact-section-information">
            <div class="contact-section-information-container">
                <h3 class=" section-default-text bold"> Email </h3>
                <a href="mailto:irisrn2004@gmail.com" target="_blank" class="section-default-text contact-text">
                    irisrn2004@gmail.com
                </a>
            </div>
            <div class="contact-section-information-container">
                <h3 class="section-default-text bold"> Social Media </h3>
                <SocialMedia social-media-image="/github.svg" social-media-name="xRedRosee"
                    social-media-link="https://github.com/xRedRosee">
                </SocialMedia>
                <SocialMedia social-media-image="/linkedin.svg" social-media-name="Iris Roemermann"
                    social-media-link="https://www.linkedin.com/in/iris-roemermann"></SocialMedia>
                <SocialMedia social-media-image="/insta.svg" social-media-name="fotografie_byiris"
                    social-media-link="https://www.instagram.com/fotografie_byiris"></SocialMedia>
            </div>
        </div>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import SocialMedia from '../SocialMedia.vue';

gsap.registerPlugin(ScrollTrigger);

const contactButterflyElement = ref(null);
const contactTitle = ref(null);

// Media query with GSAP
let mm = gsap.matchMedia(), breakPoint = 1025;

onMounted(() => {
    // Header title animation
    gsap.fromTo(contactTitle.value, {
        opacity: 0,
        y: -200,
    }, {
        scrollTrigger: {
            trigger: contactTitle.value,
            start: "top 40%",
            end: "top 20%",
            toggleActions: "restart pause reverse pause",
            scrub: 2,
        },
        opacity: 1,
        y: 0,
        duration: 1,
        ease: "power1.out",
    })

    mm.add({
        isDesktop: `(min-width: ${breakPoint}px) and (prefers-reduced-motion: no-preference)`,
        isMobile: `(max-width: ${breakPoint - 1}px) and (prefers-reduced-motion: no-preference)`
    }, (context) => {
        let { isDesktop, isMobile } = context.conditions;

        // Desktop
        if (isDesktop) {
            //Butterfly flying in animation
            gsap.fromTo(contactButterflyElement.value, {
                opacity: 0,
                y: 200,
                x: 100
            }, {
                scrollTrigger: {
                    trigger: contactButterflyElement.value,
                    start: "top 90%",
                    end: "top 50%",
                    toggleActions: "restart pause reverse pause",
                    scrub: 2,
                },
                opacity: 1,
                y: 0,
                x: 0,
                duration: 1,
                ease: "power1.out",
            })
        }

        // Butterfly animation
        gsap.fromTo(
            contactButterflyElement.value,
            {
                scaleX: 1,
                rotate: -15
            },
            {
                scaleX: 0.4,
                ease: "power2.out",
                duration: 1,
                yoyo: true,
                repeat: -1,
            }
        )
    })
})
</script>
<style scoped>
.contact {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-evenly;
    width: 100%;
    padding-top: 60px;
    margin-top: 10vh;
    height: 100vh;
}

.contact-section-header {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-left: 10%;
    width: 80%;
}

.contact-section-header-title {
    display: flex;
    flex-direction: column;
}

.section-header-title {
    font-family: var(--font-normal);
    font-weight: var(--font-normal-extralight);
    font-style: italic;
    display: flex;
    flex-direction: row;
    align-items: baseline;

}

.decorative-font {
    font-family: var(--font-decorative);
    font-weight: var(--font-decorative-regular);
    margin-left: 22px;
}

.contact-section-header-butterfly {
    height: 200px;
    filter: drop-shadow(0px 15px 5px rgba(0, 0, 0, 0.2));
}

.contact-section-information {
    margin-left: 10%;
    width: 80%;
    display: flex;
    flex-direction: row;
}

.contact-section-information-container {
    width: 50%;
    display: flex;
    gap: 16px;
    flex-direction: column;
}

.contact-text {
    text-decoration: none;
    color: var(--text-color-light);
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .contact-section-header {
        flex-direction: column-reverse;
    }

    .contact-section-header-butterfly {
        height: 20vh;
        filter: drop-shadow(0px 15px 5px rgba(0, 0, 0, 0.2));
    }

    .contact-section-information {
        flex-direction: column;
        gap: 32px;
    }

    .contact-section-information-container {
        width: 100%;
    }

    .decorative-font {
        margin-left: 16px;
    }
}

@media screen and (max-width: 768px) {
    .contact {
        margin-top: 0;
    }

    .decorative-font {
        margin-left: 13px;
    }
}
</style>