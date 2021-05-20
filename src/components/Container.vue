<template>
  <div class="myContainer">
    <Header @Selected="selectedLang" @MenuOpen="menuTrigger" />
    <transition name="fade">
      <Menu v-show="menuStatus" @MenuClose="menuTrigger" />
    </transition>
    <Main :data="data" />
    <Footer />
  </div>
</template>

<script>
import Header from './Header.vue';
import Menu from './Menu.vue';
import Main from './Main.vue';
import Footer from './Footer.vue';
import * as myData from './../myData.js';

export default {
  name: 'Container',
  components: {
    Header,
    Menu,
    Main,
    Footer
  },
  data() {
    return {
      data : String,
      menuStatus : Boolean
    }
  },
  created() {
    this.data = myData.en;
    this.menuStatus = false;
  },
  methods: {
    selectedLang(Lang) {
      console.log(Lang);
      switch (Lang) {
        case 'AR':
          this.data = myData.ar;
          break;
        case 'FR':
          this.data = myData.fr;
          break;
        case 'EN':
          this.data = myData.en;
          break;
        case 'RU':
          this.data = myData.ru;
          break;
      } 
    },
    menuTrigger(status) {
      this.menuStatus = status;
    }
  }
}
</script>

<style scoped>
  .myContainer {
    width: 100%;
    margin: 0 auto;
  }
  .fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>
