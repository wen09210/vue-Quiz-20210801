<template>
  <p>
    站點名稱搜尋: <input type="text" @input="$emit('changeText', $event.target.value)" :value="text">
  </p>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    text: String,
  },
   data() {
   return {
   }},
   methods:{
   },

}
</script>

<style scoped>
</style>
