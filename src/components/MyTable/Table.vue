<template>
  <el-table v-bind="$attrs">
    <template v-for="item in tableHeader">
      <el-table-column
        v-if="item.prop"
        :prop="item.prop"
        :label="item.label"
        :key="`column_${item.label}`"
      ></el-table-column>
      <el-table-column
        v-else-if="item.btns.length"
        :key="`column_${item.label}`"
        :label="item.label"
      >
        <template slot-scope="scope">
          <el-button
            v-for="(btn, index) in item.btns"
            :key="`btn_${btn.name}${index}`"
            @click="btnClick(btn.cb, scope)"
            type="text"
            size="small"
            >{{ btn.name }}</el-button
          >
        </template>
      </el-table-column>
    </template>
  </el-table>
</template>

<script>
export default {
  name: "MyTable",
  inheritAttrs: false,
  props: {
    tableHeader: {
      type: Array,
      default: () => {
        return [];
      },
    },
  },
  methods: {
    btnClick(name, scope) {
      this.$emit("handleClick", { name, scope });
      try {
        this.$parent[name](scope);
      } catch (error) {
        console.error(`${name} is not defined`);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
button{
  padding: 0;
}
</style>
