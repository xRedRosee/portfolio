<template>
    <NavBar></NavBar>
    <main class="contact-page">
        <h1 class="page-heading"> Get in touch with me </h1>
        <p class="page-heading-smalltext">Want to have a talk with me about a new challenge? <br>
            Feel free to contact me on my email or social media! </p>

        <section class="contact-info">
            <div class="email-side">
                <h2 class="contact-info-h2"> Email </h2>
                <a href="mailto:irisrn2004@hotmail.com" class="email-adress"> irisrn2004@hotmail.com </a>
            </div>
            <div class="socialmedia-side">
                <h2 class="contact-info-h2"> Social Media </h2>
                <SocialMedia Img="assets/social/github.svg" SocialMediaName="xRedRosee"
                    SocialMediaLink="https://github.com/xRedRosee">
                </SocialMedia>
                <SocialMedia Img="assets/social/linkedin.svg" SocialMediaName="Iris Roemermann"
                    SocialMediaLink="https://www.linkedin.com/in/iris-roemermann"></SocialMedia>
                <SocialMedia Img="assets/social/insta.svg" SocialMediaName="fotografie_byiris"
                    SocialMediaLink="https://www.instagram.com/fotografie_byiris"></SocialMedia>
            </div>
        </section>
    </main>
</template>

<script>
import NavBar from '/././components/NavBar.vue';
import SocialMedia from '~/components/SocialMedia.vue';


export default {

}
</script>

<style>
.contact-page {
    margin-top: 60px;
}

.page-heading-smalltext {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
}

.contact-info {
    display: flex;
    flex-direction: row;
    width: 80%;
    margin-top: 60px;
}

.email-side {
    display: flex;
    flex-direction: column;
    width: 50%;
}

.socialmedia-side {
    display: flex;
    flex-direction: column;
    width: 50%;
}

.contact-info-h2 {
    font-family: var(--headingfont);
    color: var(--white);
    font-weight: 500;
    font-size: 28px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
    text-decoration: none;
}

.email-adress {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
    text-decoration: none;
}

.email-adress:visited {
    font-family: var(--normalfont);
    color: var(--white);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
    text-decoration: none;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .contact-page {
        margin-top: 0;
    }
}
</style>