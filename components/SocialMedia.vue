<template>
    <figure class="social-media-block">
        <a :href=SocialMediaLink class="social-media-link" target="_blank">
            <img :src="Img" class="social-media-icon">
            <figcaption class="social-media-name"> {{ SocialMediaName
            }}
            </figcaption>
        </a>
    </figure>
</template>

<script>
export default {
    name: 'SocialMedia',
    props: {
        Img: {
            type: String,
            default: '',
            required: true
        },
        SocialMediaName: String,
        SocialMediaLink: String
    }
}
</script>

<style scoped>
.social-media-block {
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;
    margin-top: 20px;
    margin-left: 80px;
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

.social-media-name {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-left: 20px;
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