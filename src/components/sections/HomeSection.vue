<template>
    <section class="home" id="home" ref="home">
        <div ref="ballElement" class="home-ball-container">
            <img src="../../assets/gradient-butterfly.svg" ref="butterflyElement" class="home-ball-butterfly"
                alt="butterfly">
        </div>
        <header class="home-header-container">
            <section class="header-intro-section">
                <div class="header-first-container">
                    <h1 class="header-text" data-select="header-title"> Turning <span
                            class="decorative-font hover-effect">
                            ideas </span>
                    </h1>
                </div>
                <div class="header-second-container">
                    <h1 class="header-text" data-select="header-title"> into <span class="decorative-font hover-effect">
                            interactive solutions </span>
                    </h1>
                </div>
                <p class="header-bottom-text" data-select="header-text-small"> A media designer with <br>
                    a passion for front end development</p>
            </section>
            <div class="bottom-scroll-section">
                <p class="bottom-scroll-text" data-select='scroll-text'> Curious? Scroll to see more! </p>
                <img src="../../assets/scroll-icon.svg" alt="scroll icon" class="bottom-scroll-icon" ref="scrollIcon">
            </div>
        </header>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import SplitType from 'split-type';

const ballElement = ref(null)
const scrollIcon = ref(null)
const butterflyElement = ref(null)
const home = ref(null)

onMounted(() => {
    // Elements
    const headerTitleElement = home.value.querySelectorAll("[data-select='header-title']")
    const headerSmallTextElement = home.value.querySelectorAll("[data-select='header-text-small']")
    const scrollTextElement = home.value.querySelector("[data-select='scroll-text']")

    const scrollText = new SplitType(scrollTextElement, { types: 'words' });
    const scrollWords = scrollText.words;

    const titleText = new SplitType(headerTitleElement, { types: 'chars' });
    const titleTextChars = titleText.chars;

    const introText = new SplitType(headerSmallTextElement, { types: 'words' })
    const introTextWords = introText.words;

    // Timeline for the home section animations
    const tl = gsap.timeline({ repeat: -1 });

    // Butterfly flying in animation
    tl.from(butterflyElement.value, {
        y: 400,
        duration: 4,
    })

    // Header animation
    tl.from(
        titleTextChars,
        {
            opacity: 0,
            duration: 0.3,
            stagger: 0.1,
        },
    );

    // Intro text animation
    tl.from(introTextWords, {
        opacity: 0,
        duration: 0.5,
        stagger: 0.1,
        ease: "power4.inOut",

    })

    // Scroll text animation
    tl.from(scrollWords, {
        opacity: 0,
        duration: 0.5,
        stagger: 0.3,
        ease: "power4.inOut",
    });

    // Scroll icon animation
    tl.fromTo(
        scrollIcon.value,
        { opacity: 0 },
        {
            opacity: 1,
            y: "-10",
            ease: "power2.inOut",
            yoyo: true,
            repeat: -1
        }
    )

    // Ball animation
    gsap.fromTo(
        ballElement.value,
        { background: "linear-gradient(135deg, #121212 15%, #636363 100%)" },
        {
            background: "linear-gradient(-225deg, #121212 15%, #636363 100%)",
            ease: "power2.out",
            duration: 10,
            repeat: -1,
        }
    )

    // Butterfly animation
    gsap.fromTo(
        butterflyElement.value,
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
</script>
<style scoped>
.home {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100vh;
    position: relative;
}

.home-ball-container {
    width: 500px;
    height: 500px;
    border-radius: 50%;
    position: absolute;
    background: #121212;
    background: -moz-linear-gradient(-45deg, #121212 15%, #636363 100%);
    background: -webkit-linear-gradient(-45deg, #121212 15%, #636363 100%);
    background: linear-gradient(135deg, #121212 15%, #636363 100%);
    -webkit-box-shadow: inset 0px 0px 31px 1px rgba(255, 255, 255, 0.6);
    box-shadow: inset 0px 0px 31px 1px rgba(255, 255, 255, 0.6);
}

.home-ball-butterfly {
    height: 180px;
    position: absolute;
    right: 8%;
    top: 3%;
    filter: drop-shadow(0px 15px 5px rgba(0, 0, 0, 0.2));
}

.home-header-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    width: 100%;
    height: 100vh;
    position: absolute;
    z-index: 2;
}

.header-intro-section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    width: 100%;
    height: 90vh;
    z-index: 2;
}

.header-first-container {
    margin-left: 20%;
}

.header-second-container {
    margin-left: 30%;
}

.header-text {
    font-family: var(--font-normal);
    font-weight: var(--font-normal-extralight);
    font-style: italic;
    display: flex;
    flex-direction: row;
    color: var(--text-color-light);
    font-size: var(--font-size-header-big);
    align-items: baseline;
}

.decorative-font {
    font-family: var(--font-decorative);
    font-weight: var(--font-decorative-regular);
    margin: 0;
    margin-left: 12px;
}

.header-bottom-text {
    font-family: var(--font-normal);
    font-weight: var(--font-normal-extralight);
    color: var(--text-color-light);
    font-size: var(--font-size-default);
    margin-left: 60%;
}

.bottom-scroll-section {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    height: 10vh;
}

.bottom-scroll-text {
    font-family: var(--font-normal);
    font-weight: var(--font-normal-extralight);
    color: var(--text-color-light);
    font-size: var(--font-size-default-small);
}

.bottom-scroll-icon {
    height: 30px;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .home {
        height: 100vh;
        height: calc(var(--vh, 1vh) * 100);
    }

    .home-ball-container {
        width: 90vmin;
        height: 90vmin;
    }

    .home-ball-butterfly {
        height: 35vmin;
        top: 1%;
    }

    .header-intro-section {
        align-items: center;
    }

    .header-first-container {
        margin-left: 0;
    }

    .header-second-container {
        margin-left: 0;
    }

    .header-text {
        font-size: var(--font-size-header-big-sm);
        word-break: break-word;
    }

    .header-bottom-text {
        font-size: var(--font-size-default-sm);
        margin-left: 0;
    }

    .bottom-scroll-text {
        font-size: var(--font-size-default-small-sm);
    }
}
</style>