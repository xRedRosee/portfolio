<template>
    <div class="skill-bubble">
        <img alt="skillset icon" class="skill-bubble-image" :src="skillImage">
    </div>
</template>
<script setup>
const props = defineProps({
    skillImage: String
})
</script>
<style scoped>
.skill-bubble {
    width: 20vw;
    aspect-ratio: 1;
    border-radius: 50%;
    background: #121212;
    background: -moz-linear-gradient(-45deg, #121212 15%, #636363 100%);
    background: -webkit-linear-gradient(-45deg, #121212 15%, #636363 100%);
    background: linear-gradient(135deg, #121212 15%, #636363 100%);
    -webkit-box-shadow: inset 0px 0px 31px 1px rgba(255, 255, 255, 0.6);
    box-shadow: inset 0px 0px 31px 1px rgba(255, 255, 255, 0.6);
    display: flex;
    align-items: center;
    justify-content: center;
}

.skill-bubble-image {
    height: 80px;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 1024px) {
    .skill-bubble {
        flex: 0 1 calc(25% - 16px);
    }

    .skill-bubble-image {
        /* height: 40px; */
        height: 45%;
    }
}
</style>