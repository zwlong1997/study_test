<template>
  <Demo @hello="showHelloMsg" msg="您好啊" place="琶洲">
    <template v-slot:my>
      <span>展会中心</span>
    </template>
  </Demo>
</template>

<script>
import Demo from "./components/Demo.vue";
export default {
  name: "App",
  components: {
    Demo,
  },
  setup() {
    function showHelloMsg(value) {
      alert(`您好啊，你触发了hello事件，我收到的参数是：${value}!`);
    }
    return {
      showHelloMsg,
    };
  },
};
</script>

