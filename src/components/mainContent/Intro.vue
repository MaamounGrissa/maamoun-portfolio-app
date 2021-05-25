<template>
    <div id="intro" class="intro">
        <div>
            <img src="./../../assets/Profile.jpg" alt="Profile Photo">
        </div>
        <div>
            <h1 v-text="data.name" :class="data.lang === 'ar' ? 'rtl' : '' " />
            <h2 v-text="data.job" :class="data.lang === 'ar' ? 'rtl' : '' " />
            <p v-text="data.intro" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Intro',
        props: ['data']
    }
</script>


<style scoped>
    .rtl {
        direction: rtl;
    }

    .intro {
        padding: 3% 5%;
        display: flex;
        align-items: center;
    }

    .intro>div {
        width: 50%;
        padding: 40px;
    }

    h1 {
        font-size: 2.5rem;
        margin-bottom: 5px;
        color: #1f203a;
    }

    h2 {
        font-size: 2rem;
        font-weight: 400;
        margin-top: 10px;
        color: #1f203a;
    }

    p {
        color: #333;
        font-size: 1.1rem;
        line-height: 1.6;
        height: 260px;
    }

    img {
        display: block;
        width: 80%;
        height: auto;
        margin: 0 auto;
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        border-radius: 50%;
        filter: grayscale(100%);
        transition: all 0.4s ease-in-out;
    }

    img:hover {
        filter: none
    }

    @media(max-width: 767px) {
        .intro {
            flex-direction: column;
        }

        .intro>div {
            width: 100%;
            padding: 10px;
        }

        .intro>div:first-of-type {
            order: 2;
        }

        h1 {
            text-align: center;
        }

        h2 {
            text-align: center;
        }

        p {
            font-size: 1.1rem;
            line-height: 1.6;
            text-align: center;
            height: auto;
        }
    }

</style>
