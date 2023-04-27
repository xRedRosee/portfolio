<template>
    <section class="introduction">
        <article class="intro-textside">
            <p class="intro-text">
                My name is Iris Roemerman. I'm a 18 year old student living in a small town called Kessel in Limburg, the
                Netherlands. I graduated from havo in 2021 and I'm currently studying ICT & Media Design at Fontys
                University in Eindhoven. I'm a very ambitious person that likes to learn new things. In my free time I like
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
}

.intro-textside {
    width: 50%;
}

.intro-text {
    color: var(--white);
    font-family: var(--normalfont);
}

.intro-imageside {
    margin: 0;
    padding: 0;
    width: 50%;
}

.intro-img {
    height: 300px;
}
</style>