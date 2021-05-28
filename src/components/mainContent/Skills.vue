<template>
    <div id="skills" class="skills">
        <div :class="data.lang === 'ar' ? 'title reverse' : 'title' ">
            <VueFeather type="code" stroke="darkorange" size="35" />
            <h3 v-text="data.skills_title" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
        <div class="skills-group" v-for="(group, index) in data.skills" :key="index">
            <div v-for="(skill, i) in group.groupSkills" :key="i">
                <img :src="require('./../../assets/skills/' + skill)" alt="Skill">
            </div>
        </div>
    </div>
</template>

<script>
    import VueFeather from 'vue-feather';

    export default {
        name: 'Skills',
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

    .skills {
        padding: 2% 0;
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

    .skills-group {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 15px;
        overflow-x: auto;
    }

    .skills-group>div {
        width: 14%;
    }

    img {
        width: 100%;
    }

    @media(max-width: 767px) {
        .skills-group>div {
            width: 16%;
        }
    }

</style>
