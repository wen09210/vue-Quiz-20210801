<template>
  <p>
    站點名稱搜尋: <input type="text"  @keydown.enter="change">
  </p>
  <button >gogo</button>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {},
   data() {
   return {
     msg2:'1233'
   }},
   methods:{
     change(){
      this.$emit('changeText', this.msg2);
     }
   },

}
</script>

<style scoped>
</style>
