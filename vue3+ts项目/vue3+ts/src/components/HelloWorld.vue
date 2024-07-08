<template>
  <div class="container">
    <h1>{{text}}</h1>
    <div>{{ person.zhangsan.name }}</div>
    <div>{{ person.zhangsan.age }}</div>
    <button @click="changeZhangsan">修改张三</button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'HelloWorld',
});
</script>
<script setup lang="ts">
import { reactive, ref,watch,onBeforeMount,onMounted,onBeforeUpdate,onUpdated,onBeforeUnmount,onUnmounted } from 'vue'
const text = ref('hello world')
let person = reactive({
  zhangsan:{
    name:'张三',
    age:18 ,
  }
})
watch(()=>person.zhangsan,()=>{
  console.log('zhangsan',person.zhangsan.age)
},{deep:true})
function changeZhangsan(){
  // person.value.zhangsan.name = '李四'
  // person.zhangsan = {name:'lisi',age:20}
  person.zhangsan.age +=1
}
onBeforeMount(()=>{console.log('挂载钱')})
onMounted(()=>{console.log('挂载完毕')})
onBeforeUpdate(()=>{console.log('更新前')})
onUpdated(()=>{console.log('更新后')})
onBeforeUnmount(()=>{console.log('卸载前')})
onUnmounted(()=>{console.log('卸载完毕')})
</script>

<style scoped>

</style>
