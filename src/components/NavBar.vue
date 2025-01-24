<template>
    <nav class="nav">
        <p class="nav-title"> Iris Roemermann </p>
        <ul class="nav-list">
            <li class="nav-list-item">
                <a class="nav-list-item-text" href="/#home" @click="handleNavClick"> Home </a>
            </li>
            <li class="nav-list-item">
                <a class="nav-list-item-text" href="/#about" @click="handleNavClick"> About </a>
            </li>
            <li class="nav-list-item">
                <a class="nav-list-item-text" href="/#projects" @click="handleNavClick"> Projects </a>
            </li>
            <li class="nav-list-item">
                <a class="nav-list-item-text" href="/#contact" @click="handleNavClick"> Contact </a>
            </li>
        </ul>
        <button class="nav-hamburger" @click="hamburgerMenu">
            <span class="nav-hamburger-line"></span>
            <span class="nav-hamburger-line"></span>
            <span class="nav-hamburger-line"></span>
        </button>
    </nav>
</template>
<script setup>
import { ref } from 'vue';
import gsap from 'gsap';

const hamburgerOpen = ref(false);

const hamburgerMenu = () => {
    const navBar = document.querySelector('.nav');
    const navList = document.querySelector('.nav-list');
    const hamburger = document.querySelector('.nav-hamburger');

    if (hamburgerOpen.value == false) {
        // open the hamburger        
        navBar.classList.toggle("active");
        navList.classList.toggle("active");
        hamburger.classList.toggle("active");
        gsap.fromTo(
            ".nav-list-item",
            { y: 20, opacity: 0 },
            {
                y: 0,
                opacity: 1,
                duration: 0.5,
                stagger: 0.1,
                ease: "power3.out",
            }
        );
        return hamburgerOpen.value = true;

    } else if (hamburgerOpen.value == true) {
        // close hamburger
        navBar.classList.remove("active");
        navList.classList.remove("active");
        hamburger.classList.remove("active");
        return hamburgerOpen.value = false;
    }
}

// Close the hamburger menu after a link click
const handleNavClick = () => {
    hamburgerOpen.value = false;
    const navBar = document.querySelector('.nav');
    const navList = document.querySelector('.nav-list');
    const hamburger = document.querySelector('.nav-hamburger');

    navBar.classList.remove("active");
    navList.classList.remove("active");
    hamburger.classList.remove("active");
}
</script>
<style scoped>
.nav {
    width: 100%;
    display: flex;
    justify-content: space-between;
    position: fixed;
    height: 60px;
    align-items: center;
    z-index: 16;
    -webkit-backdrop-filter: blur(20px);
    backdrop-filter: blur(20px);
    background-color: #00000061;
    top: 0;
}

.nav-title {
    margin-left: 20px;
    font-size: var(--nav-font-size);
    color: var(--text-color-light);
}

.nav-list {
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    gap: 30px;
    margin-right: 20px;
}

.nav-list-item {
    margin: 0;
    padding: 0;
    list-style: none;
    cursor: pointer;
}

.nav-list-item-text {
    font-size: var(--nav-font-size);
    color: var(--text-color-light);
    text-decoration: none;
}

.nav-list-item-text::after {
    color: var(--text-color-light);
}

.nav-hamburger {
    background-color: none;
    outline: none;
    border: none;
    background: none;
    display: none;
}

.nav-hamburger-line {
    width: 30px;
    height: 2px;
    background-color: var(--color-white);
    margin: 6px auto;
    display: block;
    -webkit-transition: all 0.3s ease-in-out;
    transition: all 0.3s ease-in-out;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .nav {
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        align-items: center;
        height: 100%;
        width: 100vw;
        margin: 0;
        padding: 0;
        height: 50px;
        z-index: 16;
        -webkit-backdrop-filter: blur(20px);
        backdrop-filter: blur(20px);
        background-color: #00000061;
    }

    .nav.active {
        position: fixed;
        top: 0;
        background-color: var(--color-black);
        -webkit-backdrop-filter: none;
        backdrop-filter: none;
    }

    .nav-title {
        display: none;
    }

    .nav-list {
        list-style: none;
        margin: 0;
        padding: 0;
        display: none;
        flex-direction: column;
        align-items: flex-end;
        justify-content: space-evenly;
        right: 0;
        width: 100%;
        top: 40px;
        z-index: 10;
        position: fixed;
        background-color: var(--color-black);
    }

    .nav-list.active {
        display: flex;
        height: 100%;
        justify-content: flex-start;
        align-items: flex-start;
    }

    .nav-list-item-text {
        margin-right: 16px;
        font-size: var(--font-size-header-big-sm);
    }

    .nav-hamburger {
        display: block;
    }


    .nav-hamburger.active .nav-hamburger-line:nth-child(2) {
        opacity: 0;
    }

    .nav-hamburger.active .nav-hamburger-line:nth-child(1) {
        transform: translateY(8px) rotate(45deg);
    }

    .nav-hamburger.active .nav-hamburger-line:nth-child(3) {
        transform: translateY(-8px) rotate(-45deg);
    }
}
</style>