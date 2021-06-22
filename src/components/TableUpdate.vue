<template>
  <div>
    <!-- 搜索 -->
    <el-input v-model="search" size="mini" placeholder="输入关键字搜索" />
    <!-- 表格 -->
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
      <el-table-column prop="English" label="英语" min-width="60">
      </el-table-column>
      <el-table-column fixed="right" label="操作" width="outo" min-width="100">
        <template slot-scope="scope">
          <el-button
            @click.native.prevent="deleteRow(scope.$index, tableData)"
            type="text"
            size="small"
          >
            移除
          </el-button>
          <el-button
            @click.native.prevent="changeRow(scope.$index, tableData)"
            type="text"
            size="small"
          >
            修改
          </el-button>
        </template>
      </el-table-column>
    </el-table>
    <!-- 修改弹窗 -->
    <el-dialog title="修改" :visible.sync="changeVisible" width="60%">
      <span>学期</span>
      <el-input></el-input>
      <span>姓名</span>
      <el-input></el-input>
      <span>学号</span>
      <el-input></el-input>
      <span>数学</span>
      <el-input></el-input>
      <span>语文</span>
      <el-input></el-input>
      <span>英语</span>
      <el-input></el-input>
      <span slot="footer" class="dialog-footer">
        <el-button @click="changeVisible = false">取 消</el-button>
        <el-button type="primary" @click="changeVisible = false"
          >确 定</el-button
        >
      </span>
    </el-dialog>
  </div>
  
</template>

<script>
export default {
  methods: {
    // 搜索筛选
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
    // 删除事件
    deleteRow(index, rows) {
      this.$confirm("此操作将永久删除该文件, 是否继续?", "提示", {
        confirmButtonText: "确定",
        cancelButtonText: "取消",
        type: "warning",
        center: true,
        roundButton: true,
      })
        .then(() => {
          this.$message({
            type: "success",
            message: "删除成功!",
          });
        })
        .catch(() => {
          this.$message({
            type: "info",
            message: "已取消删除",
          });
        });
    },
    // 修改事件
    changeRow(index, rows) {
      this.changeVisible = !this.changeVisible;
    },
  },
  data() {
    return {
      changeVisible: false,
      search: "",
      tableData: [
        {
          date: "2016上半年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016下半年",
          name: "王小虎",
          number: "24182401045",
          math: "431",
          language: "273",
          English: "3120",
        },
        {
          date: "2016上半年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016上半年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "723",
          English: "120",
        },
        {
          date: "2016",
          name: "王小虎呀呀",
          number: "24182401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016上年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "3",
          English: "120",
        },
        {
          date: "201半年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016半年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016年",
          name: "呀呀呀",
          number: "24182401045",
          math: "3",
          language: "73",
          English: "120",
        },
        {
          date: "2016上半年",
          name: "王小虎呀呀呀",
          number: "241401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016半年",
          name: "王小虎呀呀",
          number: "24181045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016上半年",
          name: "王小虎呀呀呀",
          number: "24101045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2上半年",
          name: "王小虎呀呀呀",
          number: "2401045",
          math: "43",
          language: "73",
          English: "120",
        },
        {
          date: "2016年",
          name: "王小虎呀呀呀",
          number: "24182401045",
          math: "43",
          language: "3",
          English: "120",
        },
      ],
    };
  },
};
</script>

<style scoped>
.addTable {
  position: relative;
  left: 50%;
  transform: translateX(-50%);
}
</style>