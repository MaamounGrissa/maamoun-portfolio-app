<template>
  <div class="main-content">
    <Intro :data="data" />
    <div class="exp">
      <Education :data="data" />
      <Experience :data="data" />
    </div>
  </div>
</template>

<script>
import Intro from './mainContent/Intro.vue';
import Education from './mainContent/Education.vue';
import Experience from './mainContent/Experience.vue';

export default {
  name: 'Main',
  components: {
      Intro,
      Education,
      Experience
  },
  props: ['data'],
  
}
</script>


<style scoped>
  .main-content {
      padding: 0;
  }

  .exp {
    padding: 3% 10%;
    background-color: #1f203a;
    display: flex;
    overflow: hidden;
  } 

  @media(max-width: 767px) {
      .exp {
          padding: 40px 20px;
          flex-direction: column;
      }
  }
</style>
