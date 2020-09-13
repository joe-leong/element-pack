<template>
  <div id="app">
    <my-table
      :table-header="table.header"
      :data="table.data"
      :size="`mini`"
    ></my-table>
  </div>
</template>

<script>
import { Table } from "@/components/MyTable";
export default {
  name: "App",
  components: {
    MyTable: Table,
  },
  data() {
    return {
      table: {
        header: [
          {
            prop: "date",
            label: "日期",
          },
          {
            prop: "name",
            label: "姓名",
          },
          {
            prop: "province",
            label: "省份",
          },
          {
            label: "操作",
            btns: [
              {
                name: "抛出",
                cb: "test",
              },
            ],
          },
        ],
        data: [
          {
            date: "2016-05-02",
            name: "王小虎",
            province: "上海",
            city: "普陀区",
            address: "上海市普陀区金沙江路 1518 弄",
            zip: 200333,
          },
        ],
      },
    };
  },
  methods: {
    test(scope) {
      console.log(scope);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
