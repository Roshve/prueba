<template>
  <header>
    <form class="search" :class="{ active: expand }">
      <div class="icon" @click="expand = true"></div>
      <div class="input">
        <input id="mysearch" type="text" placeholder="Search" />
      </div>
      <span class="clear" @click="expand = false"></span>
    </form>
  </header>
</template>
<script>
export default {
  name: 'Header',

  data() {
    return {
      expand: false,
    }
  },

  methods: {
    toggle() {
      this.expand = true
      return (this.expand = !this.expand)
    },
    filterTitleActivity() {
      const oldQuery = this.$router.query;
      return this.expand
        ? this.$router.push({
            name: 'ProductFilter',
            query: { ...oldQuery, title: this.keywords },
          })
        : null
    },
  },
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');


header {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #297eff;
}

.search {
  position: relative;
  width: 60px;
  height: 60px;
  background: #fff;
  border-radius: 60px;
  transition: 0.5s;
  box-shadow: 0 0 0 5px #2573ef;
  overflow: hidden;
}

.search.active {
  width: 360px;
}

.search .icon {
  position: absolute;
  top: 0;
  left: 0;
  width: 60px;
  height: 60px;
  background: #fff;
  border-radius: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  cursor: pointer;
}

.search .icon::before {
  content: '';
  position: absolute;
  width: 15px;
  height: 15px;
  border: 3px solid #287dfc;
  border-radius: 50%;
  transform: translate(-4px, -4px);
}

.search .icon::after {
  content: '';
  position: absolute;
  width: 3px;
  height: 12px;
  background: #287dfc;
  transform: translate(6px, 6px) rotate(315deg);
}

.search .input {
  position: relative;
  width: 300px;
  height: 60px;
  left: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.search .input input {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  border: none;
  outline: none;
  font-size: 18px;
  padding: 10px 0;
}

.clear {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 15px;
  height: 15px;
  right: 15px;
  background: #ff0;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.clear::before {
  position: absolute;
  content: '';
  width: 1px;
  height: 15px;
  background: #999;
  transform: rotate(45deg);
}

.clear::after {
  position: absolute;
  content: '';
  width: 1px;
  height: 15px;
  background: #999;
  transform: rotate(315deg);
}
</style>