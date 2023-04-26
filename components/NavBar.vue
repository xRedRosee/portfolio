<script>
export default {
    name: "NavBar",
    setup() {
        const route = useRoute()
    },
}
</script>

<template>
    <nav class="navbar">
        <ul class="nav-list">
            <li class="nav-item">
                <NuxtLink to="/" class="nav-text"> Home</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/about" class="nav-text">About</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/projects" class="nav-text">Projects</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/contact" class="nav-text">Contact</NuxtLink>
            </li>
        </ul>
    </nav>
</template>

<style lang="css">
@import url("https://use.typekit.net/xup3qvy.css");

:root {
    --headingfont: "lust-sans", sans-serif;
    --normalfont: "owners", sans-serif;
    --white: white;
    --black: black;
}

.navbar {}

.nav-list {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    gap: 30px;
    margin-right: 30px;
}

.nav-item {
    margin: 0;
    padding: 0;
}

.nav-text {
    margin: 0;
    padding: 0;
    color: var(--white);
    text-decoration: none;
    font-family: var(--normalfont);
    font-weight: 300;
    font-size: 30px;
    position: relative;
    cursor: pointer;
}

.nav-text:after {
    content: '';
    width: 0px;
    height: 1px;
    position: absolute;
    top: 100%;
    left: 0;
    background: rgb(255, 255, 255);
    transition: 300ms;
}

.nav-text:hover:after {
    width: 100%;
}

.nav-text:not(:hover):after {
    right: 0;
    left: auto;
}
</style>