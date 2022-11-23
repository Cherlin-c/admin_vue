<template>
  <el-tree :data="data" :props="defaultProps" @node-click="nodeClick" node-key="catId"
           ref="menuTree">
      <span class="custom-tree-node" slot-scope="{ node, data }">
        <span>{{ node.label }}</span>
      </span>
  </el-tree>
</template>

<script>
export default {
  name: "category",
  //import 引入的组件需要注入到对象中才能使用
  components: {},
  props: {},
  data() {
    //这里存放数据
    return {
      data: [],
      defaultProps: {
        children: "children",
        label: "name",
      },
    };
  },
  //计算属性 类似于 data 概念
  computed: {},
  //监控 data 中的数据变化
  watch: {},
  //方法集合
  methods: {
    // 获取数据列表
    getDataList() {
      this.dataListLoading = true
      this.$http({
        url: this.$http.adornUrl("/product/category/tree"),
        method: 'get'
      }).then(({data}) => {
        if (data && data.code === 0) {
          this.data = data.data
        } else {
          this.$message.error('获取树形分类列表失败');
        }
      })
    },
    nodeClick(data,node,component){
      //向父组件发送事件
      this.$emit("tree-node-click",data,node,component);

    }
  },
  //生命周期 - 创建完成（可以访问当前 this 实例）
  created() {
    this.getDataList();
  },
  //生命周期 - 挂载完成（可以访问 DOM 元素）
  mounted() {
  },
  beforeCreate() {
  }, //生命周期 - 创建之前
  beforeMount() {
  }, //生命周期 - 挂载之前
  beforeUpdate() {
  }, //生命周期 - 更新之前
  updated() {
  }, //生命周期 - 更新之后
  beforeDestroy() {
  }, //生命周期 - 销毁之前
  destroyed() {
  }, //生命周期 - 销毁完成
  activated() {
  }, //如果页面有 keep-alive 缓存功能，这个函数会触发
};
</script>

<style scoped>

</style>
