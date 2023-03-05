<template>
  <h1>一个人的信息</h1>
  <p>sum：<input type="text" v-model="sum" /></p>
  <p>msg：<input type="text" v-model="msg" /></p>
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <button @click="person.name += '-'">修改姓名</button>
  <button @click="person.age++">把他变老</button>
  <slot name="my"></slot>
</template>

<script>
import { computed, reactive, ref, watch } from "vue";
export default {
  name: "Demo",
  props: ["msg", "place"],
  emits: ["hello"],
  setup(props, context) {
    // console.log("---setup---", props);
    let sum = ref(0);
    let msg = ref("您好啊");
    let person = reactive({
      name: "张三",
      age: 22,
    });
    // watch(
    //   [sum, msg],
    //   (newValue, oldValue) => {
    //     console.log("sum或者msg变化了", newValue, oldValue);
    //   },
    //   { immediate: true }
    // );
    watch([() => person.name, () => person.age], (newValue, oldValue) => {
      console.log("person的name变化了", newValue, oldValue);
    });
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>

