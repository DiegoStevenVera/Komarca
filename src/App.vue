<template>
  <div id="app" class="Container">
    <div class="Categories"> 
      <category v-for="category in categories" :key="category" :name="category.name">
        
      </category>
    </div>
    <div class="Resume">{{this.message}}</div>
  </div>
</template>

<script>
import Category from './components/Category'
import {EventBus} from './eventBus.js'

export default {
  name: 'App',
  components: {
    Category
  },
  data() {
    return {
      message: "Resume",
      categories: [
        { name: "Deportes"},
        { name: "Nacionales"},
        { name: "Internacionales"},
        { name: "Tecnología"},
        { name: "Políticos"},
        { name: "Espectaculos"}
      ]
    }
  },
  mounted() {
    EventBus.$on('estado', msg => {
      this.message = msg
    })
  }
}
</script>

<style>
.Container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  grid-gap: 10px;
  padding: 5px;
  background-color: aqua;
}
.Categories {
  background-color: rgb(0, 216, 144);
}
.Resume {
  grid-column-start: 2;
  grid-column-end: 5;
  background-color: rgb(0, 235, 156);
}
</style>
