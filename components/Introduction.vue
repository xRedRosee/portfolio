<template>
    <section class="introduction">
        <article class="intro-textside">
            <p class="intro-text">
                My name is Iris Roemermann. I'm a 19 year old student living in Limburg, the
                Netherlands.<br> I graduated from havo in 2021 and I'm currently studying ICT & Media Design at Fontys
                University in Eindhoven. I'm now in semester 4 and following the specialization smart mobile.
                <br> I describe myself as a very ambitious person that likes to learn new things and isn't afraid
                for a challenge!
                <br> In my free time I like to play games, go shopping or do photography.
            </p>
        </article>
        <figure class="intro-imageside">
            <img class="intro-img" src="../assets/imageik.jpg" alt="image of myself">
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
    animation: 0.5s ease-out opacitychange;
}

@keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

@-webkit-keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

.intro-imageside {
    margin: 0;
    padding: 0;
    width: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    animation: 0.5s ease-out opacitychange;
}

@keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

@-webkit-keyframes opacitychange {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

.intro-img {
    height: 380px;
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .introduction {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-bottom: 60px;
        align-items: flex-start;
    }

    .intro-textside {
        width: 100%;
        display: flex;
        justify-content: center;
    }

    .intro-text {
        font-size: 18px;
        width: 80%;
        margin-left: 0;
    }

    .intro-imageside {
        width: 100%;
    }

    .intro-img {
        width: 85%;
        height: auto;
        margin-top: 30px;
    }
}
</style>