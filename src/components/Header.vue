<template>
  <header>
    <div class="languages">
      <img :class="isActive === 'AR' ? 'active' : ''" title="Arabic" 
            src="./../assets/langs/tunisia.png" alt="Flag" @click="selectLang('AR')">
      <img :class="isActive === 'FR' ? 'active' : ''" title="French" 
            src="./../assets/langs/france.png" alt="Flag" @click="selectLang('FR')">
      <img :class="isActive === 'EN' ? 'active' : ''" title="English" 
            src="./../assets/langs/england.png" alt="Flag" @click="selectLang('EN')">
      <img :class="isActive === 'RU' ? 'active' : ''" title="Russian" 
            src="./../assets/langs/russia.png" alt="Flag" @click="selectLang('RU')">
    </div>
    <div class="menu">
      <button @click.prevent="menuOpening">
        <VueFeather type="align-right" stroke="white" size="35" />
      </button>
    </div>
  </header>
</template>

<script>
import VueFeather from 'vue-feather';

export default {
  name: 'Header',
  components: {
    VueFeather
  },
  data() {
    return {
      isActive : String,
      menuOpen: Boolean
    }
  },
  created() {
    this.isActive = 'EN';
    this.menuOpen = true;
  },
  methods: {
    selectLang(Lang) {
      this.isActive = Lang;
      this.$emit('Selected', Lang);
    },
    menuOpening() {
      this.$emit('MenuOpen', this.menuOpen)
    }
  }
}
</script>


<style scoped>
header {
    padding: 15px 5%;
    background: #1f203a;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 20px 15px -10px rgb(0 0 0 / 40%);
}

.languages {
  display: flex;
}

.languages img {
  width: 30px;
  height: 30px;
  margin: 4px;
  cursor: pointer;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  border-radius: 50%;
  border: 3px solid transparent;
}

.languages img.active {
  border: 3px solid #080
}

button {
  background: transparent;
  border: none;
  cursor: pointer;
}

</style>
