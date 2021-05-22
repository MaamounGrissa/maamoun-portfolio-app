<template>
    <div class="portfolio">
        <div class="title">
            <VueFeather type="codesandbox" stroke="darkorange" size="35" />
            <h3 v-text="data.portfolio_title" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
        <div class="skills-group" v-for="(group, index) in data.skills" :key="index">
            <div v-for="(skill, i) in group.groupSkills" :key="i">
                <img :src="require('./../../assets/' + skill)" alt="Skill">
            </div>
        </div>
    </div>
</template>

<script>
    import VueFeather from 'vue-feather';

    export default {
        name: 'Portfolio',
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

    .portfolio {
        padding: 2% 0;
    }

    .title {
        display: flex;
        align-items: center;
        margin-bottom: 20px;
    }

    h3 {
        margin-left: 15px;
        font-size: 1.8rem;
        color:darkorange
    }

    .skills-group {
        display: flex;
        align-items: center;
        margin-bottom: 15px;
        overflow-x: auto;
    }

    img {
        width: 50px;
        margin-right: 5px;
    }

    @media(max-width: 767px) {
    
    }

</style>
