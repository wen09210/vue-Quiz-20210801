<template>
<nav v-if="pagerEnd > 0">
  <ul class="pagination">
    <li @click.prevent="setPage(currentPage - 1)" class="page-item">
      <a class="page-link" href>Previous</a>
    </li>

    <li v-for="i in pagerEnd" :class="{ active: i + pagerAddAmount === currentPage }" :key="i"
      @click.prevent="setPage(i + pagerAddAmount)" class="page-item">
      <a class="page-link" href>{{ i + pagerAddAmount }}</a>
    </li>

    <li @click.prevent="setPage(currentPage + 1)" class="page-item">
      <a class="page-link" href>Next</a>
    </li>
  </ul>
</nav>
</template>

<script>
export default {
  name: 'Pager',
  props: {
    currentPage: Number,
    countOfPage: Number,
    filtedUbikeStops: Object,
  },
   data() {
   return {
     PAGINATION_MAX: 10,
   }},
   computed: {
    totalPageCount() {
    // 計算總頁數
    return Math.ceil(this.filtedUbikeStops.length / this.countOfPage);
    },
    pagerEnd() {
    // 頁碼尾端
    return this.totalPageCount <= this.PAGINATION_MAX ? this.totalPageCount : this.PAGINATION_MAX; }, pagerAddAmount() { // 頁碼位移
      const tmp=this.totalPageCount <=this.PAGINATION_MAX ? 0 : this.currentPage + 4 - this.pagerEnd; return tmp <=0 ? 0 :
      this.totalPageCount - (this.PAGINATION_MAX + tmp) < 0 ? this.totalPageCount - this.PAGINATION_MAX : tmp; }
   },
   methods:{
        setPage(page) {
        // 設定目前頁數
        if (page < 1 || page> this.totalPageCount) {
          return;
          }
          this.$emit("setPage", page);
          },
   },

}
</script>

<style scoped>
</style>
