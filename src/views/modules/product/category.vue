<template>
  <el-tree
    :data="data"
    :props="defaultProps"
    @node-click="handleNodeClick"
  ></el-tree>
</template>

<script>
export default {
  //import 引入的组件需要注入到对象中才能使用
  components: {},
  props: {},
  data() {
    return {
      data: [],
      defaultProps: {
        children: "children",
        label: "name",
      },
    };
  },
  methods: {
    handleNodeClick(data) {
      console.log(data);
    },
      // 获取数据列表
      getDataList () {
        this.dataListLoading = true
        this.$http({
          url: this.$http.adornUrl('/product/category/tree'),
          method: 'get'
        }).then(({data}) => {
          if (data && data.code === 0) {
            this.data = data.data
          } else {
            this.$message.error('获取树形分类列表失败');
          }
        })
      },
  },
  //计算属性 类似于 data 概念
  computed: {},
  //监控 data 中的数据变化
  watch: {},
  //生命周期 - 创建完成（可以访问当前 this 实例）
  created () {
    this.getDataList()
  }
}
</script>
<style lang='scss' scoped>
//@import url(); 引入公共 css 类
</style>