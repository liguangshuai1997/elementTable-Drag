<template>
  <div class="home">
    <h1>Element ui表格组件+sortablejs实现行拖拽排序</h1>
    <el-table
      size="small"
      :default-sort="{ prop: 'sortNum', order: 'ascending' }"
      :data="tableData"
      border
      align="left"
    >
      <el-table-column
        show-overflow-tooltip
        v-for="(item, index) in col"
        :key="`col_${index}`"
        :prop="col[index].prop"
        :label="item.label"
      >
        <template slot-scope="scope">
          <p>{{ scope.row[item.prop] }}</p>
          <p v-if="item.label === '操作'">
            <el-button size="mini" type="success">上架</el-button>
          </p>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import Sortable from "sortablejs";
export default {
  components: {
    Sortable
  },
  data() {
    return {
      col: [
        {
          label: "位置",
          prop: "location"
        },
        {
          label: "广告信息",
          prop: "content"
        },
        {
          label: "跳转url",
          prop: "url"
        },
        {
          label: "联系人",
          prop: "contacts"
        },
        {
          label: "开始时间",
          prop: "startDate"
        },
        {
          label: "结束时间",
          prop: "endDate"
        },
        {
          label: "经办人",
          prop: "operator"
        },
        {
          label: "操作",
          prop: "isClick"
        }
      ],
      tableData: [
        {
          location: "A5",
          content: "这个鞋子好啊",
          url: "http://xiezi.com",
          contacts: "温州皮革城",
          startDate: "2019-08-28",
          endDate: "2019-08-31",
          operator: "小李"
        },
        {
          location: "A1",
          content: "落魄前端炒粉",
          url: "http://888.com",
          contacts: "陈老板",
          startDate: "2019-08-28",
          endDate: "2019-08-31",
          operator: "小李"
        },
        {
          location: "A0",
          content: "某宝啥都有",
          url: "http://taobao.com",
          contacts: "马总",
          startDate: "2019-08-28",
          endDate: "2019-12-01",
          operator: "大锤"
        },
        {
          location: "A4",
          content: "时尚潮流服饰",
          url: "http://good.com",
          contacts: "廖老板",
          startDate: "2018-09-28",
          endDate: "2019-01-10",
          operator: "狗蛋"
        },
        {
          location: "A3",
          content: "人到中年秃不由己",
          url: "http://666666.com",
          contacts: "土豪",
          startDate: "2019-03-28",
          endDate: "2019-06-18",
          operator: "翠花"
        },
        {
          location: "A2",
          content: "落魄前端炒粉",
          url: "http://dddd.com",
          contacts: "李老板",
          startDate: "2019-02-13",
          endDate: "2019-05-31",
          operator: "小黄"
        }
      ]
    };
  },
  mounted() {
    this.rowDrop();
  },
  methods: {
    rowDrop() {
      const tbody = document.querySelector(".el-table__body-wrapper tbody");
      Sortable.create(tbody);
    }
  }
};
</script>

<style lang="scss" scoped>
.home {
  width: 1200px;
  margin: 0 auto;
}
</style>
