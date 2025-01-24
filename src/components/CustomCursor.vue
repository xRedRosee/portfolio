<template>
    <div id="custom-cursor"></div>
</template>

<script setup>
import { onMounted, onUnmounted } from 'vue';
import gsap from 'gsap';

onMounted(() => {
    const cursor = document.querySelector("#custom-cursor");
    const interactiveElements = document.querySelectorAll("a, button, .link-item-a, .project-card, .projects-section-cards-list-item");

    const moveCursor = (event) => {
        gsap.to(cursor, {
            x: event.clientX,
            y: event.clientY,
            duration: 0.1,
            ease: "power2.out",
        });
    };

    // Change cursor bigger & yellow
    const scaleUp = () => {
        gsap.to(cursor, { scale: 4, backgroundColor: "rgba(255, 229, 0, 0.5)", duration: 0.2, ease: "power2.out" });
    };

    // Change back
    const scaleDown = () => {
        gsap.to(cursor, { scale: 1, backgroundColor: "rgba(255, 255, 255, 0.5)", duration: 0.2, ease: "power2.out" });
    };

    interactiveElements.forEach((el) => {
        el.addEventListener("mouseenter", scaleUp);
        el.addEventListener("mouseleave", scaleDown);
    });

    window.addEventListener("mousemove", moveCursor);

    // Clear cursor
    onUnmounted(() => {
        window.removeEventListener("mousemove", moveCursor);
    });
});
</script>

<style scoped>
#custom-cursor {
    width: 2vh;
    aspect-ratio: 1;
    position: fixed;
    top: 0;
    left: 0;
    background-color: rgba(255, 255, 255, 0.5);
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    transform: translate(-50%, -50%);
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    #custom-cursor {
        display: none;
    }
}
</style>