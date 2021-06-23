<template>
  <div>
    <el-input v-model="search" size="mini" placeholder="输入关键字搜索" />
    <el-table :data="filterData()" style="width: 100%" max-height="750">
      <el-table-column fixed prop="date" label="学期" min-width="100">
      </el-table-column>
      <el-table-column prop="name" label="姓名" min-width="110">
      </el-table-column>
      <el-table-column prop="number" label="学号" min-width="110">
      </el-table-column>
      <el-table-column prop="math" label="数学" min-width="60">
      </el-table-column>
      <el-table-column prop="language" label="语文" min-width="60">
      </el-table-column>
      <el-table-column fixed="right" prop="English" label="英语" min-width="60">
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  methods: {
    // 筛选
    filterData() {
      return this.tableData.filter((data) => {
        return (
          !this.search ||
          data.name.toLowerCase().includes(this.search.toLowerCase()) ||
          data.number.toLowerCase().includes(this.search.toLowerCase()) ||
          data.math.toLowerCase().includes(this.search.toLowerCase()) ||
          data.language.toLowerCase().includes(this.search.toLowerCase()) ||
          data.English.toLowerCase().includes(this.search.toLowerCase()) ||
          data.date.toLowerCase().includes(this.search.toLowerCase())
        );
      });
    },
  },
  created() {
    axios
      .get("http://121.36.10.13:50000/api/student")
      .then((result) => {
        result = JSON.parse(JSON.stringify(result));
        this.tableData = result.data.data;
        console.log(result.data);
      })
      .cathch((error) => {
        console.log(error);
      });
  },
  data() {
    return {
      search: "",
      tableData: "",
    };
  },
};
</script>