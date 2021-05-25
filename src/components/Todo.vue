<!--
 * @Date: 2021-05-24 15:16:01
 * @LastEditors: Timothy
 * @LastEditTime: 2021-05-25 11:04:03
 * @Description: 
-->

<template>
  <el-container class="todo-list-wrap">
    <el-main>
      <div class="header">
        <el-input
          v-model="input"
          placeholder="请输入内容"
          @keypress.enter="addItem"
        />
        <el-button type="primary" @click="addItem">新增待办事项</el-button>
      </div>
      <div class="body">
        <ul>
          <li v-for="(c, i) of list" :key="c.id">
            <div class="label-todo">
              <el-checkbox v-model="c.complete" />
              <!-- <p class="label-wrap"> -->
                <span @click="c.editing" :class="[c.complete && 'complete']">{{ c.label }}</span>
                <!-- <el-input v-model="c.modifyLabel" v-show="c.editing"></el-input> -->
              <!-- </p> -->
            </div>
            <span>{{ c.time }}</span>
            <i class="el-icon-delete" @click="delItem(i)"></i>
          </li>
        </ul>
      </div>
    </el-main>
  </el-container>
</template>

<script>
import { ref, reactive, watch } from "vue";
//* 增加 待办事项
const useAdd = (todos) => {
  let input = ref("");
  const addItem = () => {
    todos.unshift({
      complete: false,
      label: input.value && input.value.trim(),
      id: Date.now().toString(16).slice(-5),
      time: new Date().toLocaleDateString() + new Date().toLocaleTimeString(),
    });
    input.value = ""; // 清空表单值
  };
  return {
    input,
    addItem,
  };
};
//* 删除 待办事项
const useRemove = (todos) => {
  const delItem = (i) => todos.splice(i, 1);
  return { delItem };
};
//* 编辑 待办事项
//* 持久化存储
class Storage {
  constructor(options={}){
    this.key = options.key || "vue3.x-todolist";
  }
  setItem(value){
    localStorage.setItem(this.key,JSON.stringify(value));
  }
  getItem(){
    return JSON.parse(localStorage.getItem(this.key));
  }
}
const storage = new Storage();
export default {
  name: "Todo",
  setup() {
    let list = reactive(storage.getItem() || []);
    watch(list,(val) => storage.setItem(val))
    return {
      list,
      ...useAdd(list),
      ...useRemove(list),
    };
  },
};
</script>
<style scoped >
.todo-list-wrap {
  justify-content: center;
}
.el-main {
  max-width: 800px;
}
.header {
  display: flex;
}
.header .el-button {
  margin-left: 10px;
}
ul {
  all: unset;
}
li {
  list-style: none;
  text-align: left;
  height: 40px;
  line-height: 40px;
  display: flex;
  align-items: center;
}
li i {
  cursor: pointer;
  color: red;
  margin-left: 10px;
}
.el-checkbox {
  margin-right: 20px !important;
}
.el-checkbox__label {
  font-size: 18px;
  font-weight: normal;
}
.label-todo {
  margin-right: auto;
}
.complete{
  text-decoration-line: line-through;
}
</style>