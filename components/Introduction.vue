<template>
    <section class="introduction">
        <article class="intro-textside">
            <p class="intro-text">
                My name is Iris Roemerman. I'm a 18 year old student living in a small town called Kessel in Limburg, the
                Netherlands.<br> I graduated from havo in 2021 and I'm currently studying ICT & Media Design at Fontys
                University in Eindhoven. <br> I'm a very ambitious person that likes to learn new things and isn't afraid
                for a challenge! <br> In my free
                time I like
                to play games, go shopping or do photography.
            </p>
        </article>
        <figure class="intro-imageside">
            <img class="intro-img" src="../assets/imageik.jpg">
        </figure>
    </section>
</template>

<script>
export default {
    name: "Introduction",
}
</script>

<style scoped>
.introduction {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 60px;
}

.intro-textside {
    width: 50%;
}

.intro-text {
    color: var(--white);
    font-family: var(--normalfont);
    font-size: 21px;
    margin: 0;
    margin-top: 20px;
    margin-left: 80px;
    width: 60%;
}

.intro-imageside {
    margin: 0;
    padding: 0;
    width: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.intro-img {
    height: 380px;
}
</style>