<template>
  <div class="menu">
      <div class="nav-container">
          <button @click.prevent="menuTrigger">X</button>
          <nav>
              <ul>
                  <li><a href="#intro">Intro</a></li>
                  <li><a href="#education">Education</a></li>
                  <li><a href="#experiences">Experiences</a></li>
                  <li><a href="#skills">Skills</a></li>
                  <li><a href="#portfolio">Portfolio</a></li>
                  <li><a href="#contact">Contact Me</a></li>
              </ul>
          </nav>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
      return {
          menuClose: false
      }
  },
  methods: {
      menuTrigger() {
          this.$emit('MenuClose', this.menuClose)
      }
  }
  
}
</script>


<style scoped>
.menu {
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.5);
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
}

.nav-container {
    width: 30%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    position: relative;
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

button {
    position: absolute;
    right: 10px;
    top: 10px;
    cursor: pointer;
    color: white;
    font-size: 28px;
    font-weight: bold;
    background-color: transparent;
    border: none;
    transition: all 0.1s ease-in-out;
    opacity: 0.8;
}

button:hover {
    opacity: 1;
    font-size: 30px;
}

nav {
    color: white;
    padding: 60px 15%;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    padding: 8px 0;
    font-size: 22px;
}

li>a {
    color: white;
    text-decoration: none;
}

@media(max-width: 767px) {
    .nav-container {
        width: 60%;
    }
}
</style>
