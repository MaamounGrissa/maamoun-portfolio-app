<template>
    <div id="education" class="education">
        <div :class="data.lang === 'ar' ? 'title reverse' : 'title' ">
            <VueFeather type="book-open" stroke="darkorange" size="35" />
            <h3 v-text="data.education_title" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
        <div  v-for="(item, index) in data.education" :key="index" :class="data.lang === 'ar' ? 'item reverse' : 'item' " >
            <img :src="require('./../../assets/career/' + item.logo)" alt="Logo">
            <div>
                <h4 v-text="item.certificate" :class="data.lang === 'ar' ? 'rtl' : '' " />
                <h5 v-text="item.institute" :class="data.lang === 'ar' ? 'rtl' : '' " />
                <p v-text="item.date" :class="data.lang === 'ar' ? 'rtl' : '' " />
            </div>
        </div>
    </div>
</template>

<script>
    import VueFeather from 'vue-feather';

    export default {
        name: 'Intro',
        components: {
            VueFeather
        },
        props: ['data']
    }
</script>


<style scoped>
    .rtl {
        direction: rtl;
    }

    .reverse {
        flex-direction: row-reverse;
    }

    .education {
        padding: 0 20px;
        width: 40%;
    }

    .title {
        display: flex;
        align-items: center;
        margin-bottom: 40px;
        margin-top: 10px;
    }

    h3 {
        margin: 0 15px;
        font-size: 1.8rem;
        color:darkorange
    }

    h4 {
        margin: 0 0 8px;
        color: #fff;
    }

    h5 {
        margin: 0 0 5px;
        color: #9c9c9c;
    }

    p {
        font-style: italic;
        font-size: 14px;
        color: #887b7b;
    }


    img {
        width: 50px;
        height: 50px;
        margin: 0 10px;
    }

    .item {
        display: flex;
        margin-bottom: 25px;
    }

    @media(max-width: 767px) {
        .education {
            padding: 0;
            width: 100%;
        }
    }

</style>
