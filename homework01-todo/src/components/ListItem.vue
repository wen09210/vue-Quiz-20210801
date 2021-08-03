<template>
  <li v-for="i in insideList" :key="i.id">
    <label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
  </li>
</template>

<script>
  export default {
    name: 'ListItem',
    props: {
      insideList: {
        type: Boolean,
      }
    }
  }
</script>