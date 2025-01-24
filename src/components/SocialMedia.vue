<template>
    <div class="social-media-block">
        <a :href="socialMediaLink" class="social-media-link" target="_blank">
            <img :src="socialMediaImage" class="social-media-icon">
            <p class="section-default-text contact-text"> {{ socialMediaName }} </p>
        </a>
    </div>
</template>
<script setup>
const props = defineProps({
    socialMediaLink: String,
    socialMediaImage: String,
    socialMediaName: String
})
</script>
<style scoped>
.social-media-block {
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;
}

.social-media-link {
    text-decoration: none;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
}

.social-media-icon {
    height: 40px;
}

.contact-text {
    text-decoration: none;
    color: var(--text-color-light);
    margin-left: 20px;
}
</style>