<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>#</th>
        <th>場站名稱</th>
        <th>場站區域</th>
        <th>
          <div @click="setSort('sbi')">
            目前可用車輛
            <i v-if="currentSort === 'sbi'" :class="{ 'fa-sort-asc': !isSortDesc, 'fa-sort-desc': isSortDesc }"
              class="fa" aria-hidden="true"></i>
            <i v-else class="fa fa-sort" aria-hidden="true"></i>
          </div>
        </th>
        <th>
          <div @click="setSort('tot')">
            總停車格
            <i v-if="currentSort === 'tot'" :class="{ 'fa-sort-asc': !isSortDesc, 'fa-sort-desc': isSortDesc }"
              class="fa" aria-hidden="true"></i>
            <i v-else class="fa fa-sort" aria-hidden="true"></i>
          </div>
        </th>
        <th>資料更新時間</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="s in tableData" :key="s.sno">
        <td>{{ s.sno }}</td>
        <td>{{ s.sna }}</td>
        <td>{{ s.sarea }}</td>
        <td>{{ s.sbi }}</td>
        <td>{{ s.tot }}</td>
        <td>{{ timeFormat(s.mday) }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'TableSheet',
  props: {
    tableData: Object,
    currentSort: String,
    isSortDesc: Boolean,
  },
   data() {
   return {
   }},
   methods:{
      timeFormat(val) {
      // 時間格式
      const pattern = /(\d{4})(\d{2})(\d{2})(\d{2})(\d{2})(\d{2})/;
      return val.replace(pattern, "$1/$2/$3 $4:$5:$6");
      },
      setSort(val) {
        this.$emit("setSortIn", val);
      },
   },

}
</script>

<style scoped>
</style>
