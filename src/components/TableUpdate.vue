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
          <el-button
            @click.native.prevent="addRow(scope.$index, tableData)"
            type="text"
            size="small"
          >
            添加
          </el-button>
        </template>
      </el-table-column>
    </el-table>
    <!-- 修改弹窗 -->
    <el-dialog title="修改" :visible.sync="changeVisible" width="60%">
      <span>学期</span>
      <el-input v-model="tableData[indexData].date"></el-input>
      <span>姓名</span>
      <el-input v-model="tableData[indexData].name"></el-input>
      <span>学号</span>
      <el-input v-model="tableData[indexData].number"></el-input>
      <span>数学</span>
      <el-input v-model="tableData[indexData].math"></el-input>
      <span>语文</span>
      <el-input v-model="tableData[indexData].language"></el-input>
      <span>英语</span>
      <el-input v-model="tableData[indexData].English"></el-input>
      <span slot="footer" class="dialog-footer">
        <el-button @click="changeVisible = false">取 消</el-button>
        <el-button type="primary" @click="changeData()">确 定</el-button>
      </span>
    </el-dialog>
    <!-- 添加弹窗 -->
    <el-dialog title="添加" :visible.sync="addVisible" width="60%">
      <span>学期</span>
      <el-input v-model="dateAdd"></el-input>
      <span>姓名</span>
      <el-input v-model="nameAdd"></el-input>
      <span>学号</span>
      <el-input v-model="numberAdd"></el-input>
      <span>数学</span>
      <el-input v-model="mathAdd"></el-input>
      <span>语文</span>
      <el-input v-model="languageAdd"></el-input>
      <span>英语</span>
      <el-input v-model="EnglishAdd"></el-input>
      <span slot="footer" class="dialog-footer">
        <el-button @click="addVisible = false">取 消</el-button>
        <el-button type="primary" @click="addData()">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
import axios from "axios";

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
    // 添加数据
    addRow(index, rows) {
      this.addVisible = !this.addVisible;
      this.indexData = index;
    },
    addData() {
      this.addVisible = false;
      let data = {
        number: this.numberAdd,
        name: this.nameAdd,
        language: this.languageAdd,
        math: this.mathAdd,
        English: this.EnglishAdd,
        date: this.dateAdd,
      };
      axios
        .post("http://121.36.10.13:50000/api/insert_score", data, {
          timeout: 5000,
        })
        .then((result) => {
          result = JSON.parse(JSON.stringify(result));
          this.tableData = result.data.data;
          console.log(result.data);
        })
        .cathch((error) => {
          console.log(error);
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
          let data = {
            number: this.tableData[index].number,
            date: this.tableData[index].date,
          };
          axios
            .post("http://121.36.10.13:50000/api/delete_score", data, {
              timeout: 5000,
            })
            .then((result) => {
              result = JSON.parse(JSON.stringify(result));
              this.tableData = result.data.data;
              console.log(result.data);
            })
            .cathch((error) => {
              console.log(error);
            });
        })
    },
    // 修改事件
    changeRow(index, rows) {
      this.changeVisible = !this.changeVisible;
      this.indexData = index;
      console.log(index);
    },
    changeData() {
      this.changeVisible = false;
      let data = {
        number: this.tableData[this.indexData].number,
        name: this.tableData[this.indexData].name,
        language: this.tableData[this.indexData].language,
        math: this.tableData[this.indexData].math,
        English: this.tableData[this.indexData].English,
        date: this.tableData[this.indexData].date,
      };
      console.log(data);
      axios
        .post("http://121.36.10.13:50000/api/updata_score", data, {
          timeout: 5000,
        })
        .then((result) => {
          result = JSON.parse(JSON.stringify(result));
          this.tableData = result.data.data;
          console.log(result.data);
        })
        .cathch((error) => {
          console.log(error);
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
    console.log("asd");
  },
  data() {
    return {
      indexData: 0,
      changeVisible: false,
      addVisible: false,
      search: "",
      tableData: [],
      dateAdd:"",
      nameAdd:"",
      languageAdd: 0,
      mathAdd: 0,
      EnglishAdd:0,
      numberAdd:"",
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