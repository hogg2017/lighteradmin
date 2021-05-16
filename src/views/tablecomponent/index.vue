<template>
  <div class="app-container">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>需求</span>
        <el-button 
        style="float: right; padding: 3px 0" type="text"
          >弹窗按钮</el-button
        >
      </div>
      <div class="text item">
        1.点击弹窗按钮弹出一个模态框,内部是一个表格,有多种组件.点击确定按钮发送数据,进入加载态;点击取消按钮清空数据;
        2.demo目的是为了测试三层封装
      </div>
    </el-card>
  </div>
</template>

<script>
import { getList } from "@/api/table";

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        published: "success",
        draft: "gray",
        deleted: "danger",
      };
      return statusMap[status];
    },
  },
  data() {
    return {
      list: null,
      listLoading: true,
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.listLoading = true;
      getList().then((response) => {
        this.list = response.data.items;
        this.listLoading = false;
      });
    },
  },
};
</script>
