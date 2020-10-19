<template>
  <div>
      这个是子节点{{showMessage}}
      <br/>
      {{propD}}
  </div>
</template>

<script lang="ts">
// 注意点：1.下面的代码必须在每个页面都中引入
import { Component, Vue, Prop } from 'vue-property-decorator';

  @Component
  // 注意点：2.每个页面都有组件名称：App/自定义
export default class Child2 extends Vue {
  @Prop(String) propB!: string;

  @Prop(Object) propD?: any;

    public showMessage?: string|number = 10;

    created() {
      console.log(this.propD.abc2);
    }
}
</script>

<style scoped>

</style>
