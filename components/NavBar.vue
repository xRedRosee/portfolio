<script>
export default {
    name: "NavBar",
    setup() {
        const route = useRoute()
    },
    data() {
        return {
            hamburgerMenuPressed: false,
        }
    },
    methods: {
        hamburgerMenu() {
            // select the items from HTML
            const r = document.querySelector(':root');

            if (this.hamburgerMenuPressed == false) {
                // open hamburger
                r.style.setProperty('--navbardisplay', 'flex');
                r.style.setProperty('--opacitylines', 'none');
                r.style.setProperty('--opacityexit', 'block');
                r.style.setProperty('--navbarposition', 'fixed');
                document.querySelector("#exit").innerText = 'X';
                return this.hamburgerMenuPressed = true;
            } else if (this.hamburgerMenuPressed == true) {
                // close hamburger
                r.style.setProperty('--navbardisplay', 'none');
                r.style.setProperty('--opacitylines', 'block');
                r.style.setProperty('--opacityexit', 'none');
                r.style.setProperty('--navbarposition', 'absolute');
                document.querySelector("#exit").innerText = 'X';
                return this.hamburgerMenuPressed = false;
            }
        },
    }
}
</script>

<template>
    <nav class="navbar">
        <ul class="nav-list">
            <li class="nav-item">
                <NuxtLink to="/" class="nav-text"> Home</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/about" class="nav-text">About</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/projects" class="nav-text">Projects</NuxtLink>
            </li>
            <li class="nav-item">
                <NuxtLink to="/contact" class="nav-text">Contact</NuxtLink>
            </li>
        </ul>
        <button class="hamburgermenu" @click="hamburgerMenu">
            <span id="line1"></span>
            <span id="line2"></span>
            <span id="line3"></span>
            <span id="exit"> X </span>
        </button>
    </nav>
</template>

<style lang="css">
@import url("https://use.typekit.net/xup3qvy.css");

:root {
    --headingfont: "lust-sans", sans-serif;
    --normalfont: "owners", sans-serif;
    --white: white;
    --black: black;
    --navbardisplay: none;
    --opacitylines: block;
    --opacityexit: none;
    --navbarposition: static;
}

.navbar {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    height: auto;
}

.nav-list {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    gap: 30px;
    margin-right: 30px;
    margin-top: 10px;
    width: 100%;
}

.nav-item {
    margin: 0;
    padding: 0;
}

.nav-text {
    margin: 0;
    padding: 0;
    color: var(--white);
    text-decoration: none;
    font-family: var(--normalfont);
    font-weight: 300;
    font-size: 30px;
    position: relative;
    cursor: pointer;
}

.nav-text:after {
    content: '';
    width: 0px;
    height: 1px;
    position: absolute;
    top: 100%;
    left: 0;
    background: var(--white);
    transition: 300ms;
}

.nav-text:hover:after {
    width: 100%;
}

.nav-text:not(:hover):after {
    right: 0;
    left: auto;
}

.hamburgermenu {
    background-color: none;
    outline: none;
    border: none;
    background: none;
    display: none;
}

#line1 {
    width: 30px;
    height: 2px;
    background-color: var(--white);
    margin-block: 3px;
    display: var(--opacitylines);
}

#line2 {
    width: 30px;
    height: 2px;
    background-color: var(--white);
    margin-block: 3px;
    display: var(--opacitylines);
}

#line3 {
    width: 30px;
    height: 2px;
    background-color: var(--white);
    margin-block: 3px;
    display: var(--opacitylines);
}

#exit {
    display: var(--opacityexit);
    font-size: 1.5em;
    font-family: arbotek, sans-serif;
    font-weight: 100;
    color: var(--white);
}

/* -------------------------------------------- media queries */
@media screen and (max-width: 768px) {
    .navbar {
        display: flex;
        flex-direction: column-reverse;
        justify-content: center;
        align-items: flex-end;
        height: 100%;
        width: 100%;
        background-color: var(--black);
        margin: 0;
        padding: 0;
        height: 50px;
        position: var(--navbarposition);
    }

    .nav-list {
        list-style: none;
        margin: 0;
        padding: 0;
        display: var(--navbardisplay);
        flex-direction: column;
        align-items: flex-end;
        justify-content: space-evenly;
        position: absolute;
        right: 0;
        width: 50%;
        top: 40px;
    }


    .nav-text {
        margin-right: 16px;
        font-size: 50px;
    }

    .hamburgermenu {
        display: block;
    }

    #line1 {
        display: var(--opacitylines);
        margin-right: 18px;
    }

    #line2 {
        display: var(--opacitylines);
        margin-right: 18px;
    }

    #line3 {
        display: var(--opacitylines);
        margin-right: 18px;
    }

    #exit {
        display: var(--opacityexit);
        font-size: 40px;
        font-weight: 100;
        font-family: var(--normalfont);
        margin-right: 18px;
    }
}

@media (min-width: 769px) and (max-width: 8000px) {
    .nav-list {
        display: flex;
        flex-direction: row;
    }

    .navbar {
        position: static;
    }
}
</style>