<template>
    <div class="experience">
        <div class="title">
            <VueFeather type="briefcase" stroke="darkorange" size="35" />
            <h3 v-text="data.experience_title" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
        <div class="item" v-for="(item, index) in data.experience" :key="index">
            <img :src="require('./../../assets/' + item.logo)" alt="Logo">
            <div>
                <h4 v-text="item.desc" />
                <h5 v-text="item.mission" />
                <i v-text="item.date" />
            </div>
        </div>
    </div>
</template>

<script>
    import VueFeather from 'vue-feather';

    export default {
        name: 'Experience',
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

    .experience {
        padding: 0 20px;
        width: 60%;
    }

    .title {
        display: flex;
        align-items: center;
        margin-bottom: 30px;
    }

    h3 {
        margin-left: 15px;
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

    i {
        font-size: 14px;
        color: #887b7b;
    }

    img {
        width: 50px;
        height: 50px;
        margin-right: 15px;
        object-fit: contain;
    }

    .item {
        display: flex;
        margin-bottom: 25px;
    }

    @media(max-width: 767px) {
        .experience {
            padding: 0;
            width: 100%;
        }
    }

</style>
