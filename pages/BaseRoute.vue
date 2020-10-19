<template>
  <div>
    页面2
    <child1 ref="child1" propA="子页面1" :propC="{json1:'json1',json2:'json2'}"></child1>
    <child2 propB="子页面2" :propD="baseForm"></child2>
    <br />
    {{countChange}}
  </div>
</template>

<script lang="ts">
import {
  Component, Prop, Vue, Watch,
} from 'vue-property-decorator';
import Child1 from '@/components/child1.vue';
import Child2 from '@/components/child2.vue';

@Component({
  components: {
    Child1,
    Child2,
  },
})
export default class BasePage extends Vue {
  public baseForm: Record<string, any> = {
    abc1: '111',
    abc2: '222',
  }

  public count = 0;

  public watchMsg?: string = ''

  // 生命周期
  created(): void {
    console.log('created');
  }

  beforeCreate(): void {
    console.log('beforecreate');
  }

  beforeMount(): void {
    console.log('beforemounted');
  }

  mounted(): void {
    console.log('mounted');
  }

  beforeDestroy(): void {
    console.log('beforeDestroy');
  }

  // 原 method 方法 直接在这一次写
  test() {

  }

  // vue 计算属性
  get countChange(): number {
    return this.count;
  }

  set countChange(val) {
    this.count = val + 1;
  }

  // watch 监听
  // 注意2. 监听多个就导入多个Watch，命名自定义 clgMsg(newVal: string)
  @Watch('count')
  Count(newVal: number) {
    if (newVal < 10) {
      this.watchMsg = `我是数字${newVal}`;
    } else {
      this.watchMsg = '我会继续增长';
    }
  }

  @Watch('watchMsg')
  clgMsg(newVal: string) {
    console.log(newVal);
  }
}
</script>

<style scoped>

</style>
