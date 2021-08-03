<template>
  <p>
    站點名稱搜尋: <input type="text" >
  </p>
  {{searchInText}}
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    searchInText:{
      type: String,
    }
  }
}
</script>

<style scoped>
</style>
