<script>
export default {
    name: "NavBar",
    setup() {
        const route = useRoute()
    },
}
</script>

<template>
    <nav>
        <ul>
            <li>
                <NuxtLink to="/"> Home</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/about">About</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/projects">Projects</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/contact">Contact</NuxtLink>
            </li>
        </ul>
    </nav>
</template>

<style lang="css"></style>