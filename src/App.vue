<template>
  <img
    alt="Vue logo"
    width="50"
    height="50"
    src="./assets/logo.png"
  >
  <h1>Vue 3 slot demo</h1>
  <h5>Children updated: {{ childrenUpdated }}</h5>
  <div>
    <MyDropdown
      v-model="current"
      :options="list"
    />
  </div>
</template>

<script>
import MyDropdown from "./components/MyDropdown/MyDropdown.vue";
export default {
    name: "App",
    components: {
        MyDropdown,
    },
    provide() {
      return {
        addUpdate: () => {
          this.childrenUpdated += 1;
        },
        resetChildrenUpdated: () => {
          this.childrenUpdated = 0;
        }
      }
    },
    data() {
        return {
          childrenUpdated: 0,
          current: "",
          list: [
            {id: 1, title: 'Apple'},
            {id: 2, title: 'Banana'},
            {id: 3, title: 'Orange'},
            {id: 4, title: 'Mango'},
            {id: 5, title: 'Grapes'},
            {id: 6, title: 'Kiwi'},
            {id: 7, title: 'Pear'},
            {id: 8, title: 'Lime'},
            {id: 9, title: 'Peach'},
            {id: 10, title: 'Avocado'},
          ],
        };
    }
};
</script>

<style>
:root {
    --color-theme: rgb(65 184 131);
    --color-border: rgb(133, 133, 133);
    --color-border-hover: rgb(172, 172, 172);
}

* {
    box-sizing: border-box;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
