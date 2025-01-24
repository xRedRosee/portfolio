<template>
    <a :href="link" class="link-item-a" target="_blank">
        <p v-show="githubLink" class="section-default-text"> See code </p>
        <p v-show="!githubLink" class="section-default-text"> Visit website </p>
        <img alt="open link icon" class="link-item-image" src="../assets/arrow-link.svg" ref="linkImage">
    </a>
</template>
<script setup>
const props = defineProps({
    githubLink: Boolean,
    link: String
})

</script>
<style scoped>
.link-item-a {
    text-decoration: none;
    color: var(--white);
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 17px;
}

.link-item-a:hover {
    cursor: none;
    /* Zorg ervoor dat de normale cursor verdwijnt */
}

.link-item-image {
    height: 36px;
}
</style>