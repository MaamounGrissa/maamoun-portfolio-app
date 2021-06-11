<template>
    <div id="portfolio" class="portfolio">
        <div :class="data.lang === 'ar' ? 'title reverse' : 'title' ">
            <VueFeather type="codesandbox" stroke="darkorange" size="35" />
            <h3 v-text="data.portfolio_title" :class="data.lang === 'ar' ? 'rtl' : '' " />
        </div>
        <div class="projects">
            <div class="project" v-for="(project, index) in data.portfolio" :key="index">
                <h4 v-text="project.name" />
                <img :src="require('./../../assets/portfolio/' + project.photo)" alt="Project">
                <div class="actions">
                    <a :class="project.code === '' ? 'url disable' : 'url'" target="_BLANK" :href="project.code === '#' ? '' : project.code">
                        <VueFeather type="github" size="20" />
                        <span v-text="data.code_btn" />
                    </a>
                    <a :class="project.url === '' ? 'url disable' : 'url'" target="_BLANK" :href="project.url">
                        <VueFeather type="link" size="20" />
                        <span v-text="data.url_btn" />
                    </a>
                </div>
                <img :src="require('./../../assets/skills/' + project.skills[0] + '.png')" class="skill s1" alt="Skill">
                <img v-if="project.skills[1]" :src="require('./../../assets/skills/' + project.skills[1] + '.png')" class="skill s2" alt="Skill">
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

    .reverse {
        flex-direction: row-reverse;
    }

    .portfolio {
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

    h4 {
        text-align: left;
        color: #fff;
        font-size: 1.2rem;
        margin-bottom: 15px;
        margin-top: 10px;
        padding-left: 20px;
    }

    .projects {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    .project {
        position: relative;
        width: 30%;
        border: 1px solid white;
        padding: 10px;
        border-radius: 10px;
        margin-bottom: 20px;
        background-color: rgba(255,255,255,0.1);
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
    }

    img {
        width: 100%;
        margin-bottom: 5px;
    }

    .actions {
        display: flex;
        justify-content: space-between;
        width: 100%;
    }

    a.url {
        display: flex;
        align-items: center;
        padding: 5px 5px;
        border: 1px solid #fff;
        border-radius: 10px;
        text-align: center;
        justify-content: center;
        background-color: #1f203a;
        color: white;
        text-decoration: none;
        width: 40%;
        transition: all 0.3s ease-in-out;
    }

    a.url:hover {
        background-color: white;
        color: #1f203a;
    }

    .url>span {
        margin-left: 8px;
    }

    .url.disable {
        background-color: #51526e;
        pointer-events: none;
    }

    .skill {
        width: 50px;
        height: 50px;
        border-radius: 50%;
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        position: absolute;
        top: 5px;
    }

    .skill.s1 {
        right: 10px;
    }

    .skill.s2 {
        right: 75px;
    }

    @media(max-width: 767px) {
        .project {
            width: 100%;
        }

        a.url span{
            margin-left: 5px;
            font-style: 15px;
        }
    }

</style>
