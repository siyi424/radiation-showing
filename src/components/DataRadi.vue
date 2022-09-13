<template>
  <el-table 
  :data="dataset" 
  :row-class-name="tableRowClassName"
  :header-cell-style="{ background: '#f3f6fd', color: '#555' }" 
  style="width: 100%; height: 100%">
    <el-table-column prop="time" label="时间" width="180" align="center"/>
    <el-table-column prop="value" label="值" width="180" align="center"/>
    <el-table-column prop="isSafed" label="是否超出国家限值" align="center"/>
  </el-table>
</template>

<script>
  export default {
    props: ['dataset'],
    methods: {
      tableRowClassName({row}) {
        if (row.isSafed == "安全") {
          return 'success-row';
        } else {
          return 'warning-row';
        }
      }
    },
  }
</script>

<style>
.el-table .warning-row {
  background: rgba(225, 0, 0, 0.5);
}

.ones {
  background: red;
}


</style>
