<template>
  <div>
      这个是子节点{{showMessage}}{{propA}}
      <br/>
      {{propC}}
  </div>
</template>

<script lang="ts">
// 注意点：1.下面的代码必须在每个页面都中引入
import { Component, Vue, Prop } from 'vue-property-decorator';

  @Component
  // 注意点：2.每个页面都有组件名称：App/自定义
export default class Child1 extends Vue {
     @Prop(String) propA!: string;

     @Prop(Object) propC!: Record<string, any>;

    public showMessage?: string|number = 111;
}
</script>

<style scoped>

</style>
