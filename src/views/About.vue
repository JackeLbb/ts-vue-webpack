<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>
<script lang="ts">
/**
 * @name about (组件名称)
 * @module 组件存放位置
 * @desc 组件描述
 * @author Jacke
 * @date
 * @param {Object} [title]    - 参数说明
 * @param {String} [columns] - 参数说明
 * @example 调用示例
 *   <about></about>
 */

import { Component, Vue, Prop, Watch, Emit } from 'vue-property-decorator';

@Component({
  components: {}
})
export default class Home extends Vue {
  @Prop({
    type: String,
    required: true
  })
  childProp: string | number = '';

  tasks: Array<number | string> = [];

  task: string | number = '';

  addTask() {
    this.tasks.push(this.task);
    this.task = '';
  }

  @Watch('task')
  onTaskChange(oldValue: string | number, newValue: string | number) {
    console.log(`oldValue ${oldValue}`);
    console.log(`newValue ${newValue}`);
  }

  @Emit('handleClick')
  // 函数的参数值即是emit的payload
  emitTasks(tasks: Array<string | number>) {
    this.tasks[0] = 'haha';
  }
}
</script>

