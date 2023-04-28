<template>
    <figure class="social-media-block">
        <img :src=SocialImage class="social-media-icon">
        <figcaption class="social-media-name"><a :href=SocialMediaLink class="social-media-name"> {{ SocialMediaName
        }}
            </a></figcaption>
    </figure>
</template>

<script>
export default {
    name: 'SocialMedia',
    props: {
        SocialImage: {
            type: String,
            required: true
        },
        SocialMediaName: String,
        SocialMediaLink: String
    }
}
</script>

<style scoped>
.social-media-block {}

.social-media-icon {}

.social-media-name {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
    text-decoration: none;
}

.social-media-name:visited {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
    text-decoration: none;
}
</style>