<template>
    <div class="Category" @click="click()">
        {{ name }}
    </div>
</template>

<script>
import {EventBus} from './../eventBus.js'

export default {
  name: 'Category',
  props: ['name'],
  methods: {
      click: function() {
        EventBus.$emit('estado',this.name)
      }
  }
};
</script>

<style scoped>
    .Category {
        padding: 20px;
    }
</style>
