<template>
  <div class="hello">
    <h1>{{ msg }}--{{aa}}</h1>
    <button v-for="(item,index) in array" :key="item" @click="selectAFun(index)">
      {{index}}---{{ item }}
    </button>
    <div>
      choose: {{selectA}}
    </div>
    <div>
      <button @click="watchFunction">测试</button>
      <div>{{watchText}}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { 
  defineComponent,
  ref,
  reactive,
  toRefs,
  watch,
  onMounted,
  onBeforeMount,
  onBeforeUpdate,
  onRenderTracked,
  onRenderTriggered,
  onUpdated, } from 'vue';

interface DataProps{
  array: string[];
  selectA: string;
  selectAFun: (index: number) => void;
}
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  // data() {
  //   return {
  //     aa: '99'
  //   }
  // },
  /**1、setup和ref */
  // setup(){
  //   const aa = ref('99')
  //   const array = ref(['a', 'b', 'c'])
  //   const selectA = ref('')
  //   const selectAFun = (index: number)=>{
  //     selectA.value = array.value[index]
  //   }

  //   return {
  //     aa,
  //     array,
  //     selectA,
  //     selectAFun
  //   }
  // },
  /* 2、reactive*/
  setup() {
    const data: DataProps = reactive({
      aa: '99',
      array: ['a', 'b', 'c'],
      selectA: '',
      selectAFun: (index: number)=>{
        data.selectA = data.array[index]
      }
    })
    // onBeforeMount(() => {
    //   console.log("2-组件挂载到页面之前执行-----onBeforeMount()");
    // });

    // onMounted(() => {
    //   console.log("3-组件挂载到页面之后执行-----onMounted()");
    // });
    // onBeforeUpdate(() => {
    //   console.log("4-组件更新之前-----onBeforeUpdate()");
    // });

    // onUpdated(() => {
    //   console.log("5-组件更新之后-----onUpdated()");
    // });
    // onRenderTracked((event)=>{
    //   console.log("状态跟踪组件----------->");
    //   console.log(event);
    // })
    // onRenderTriggered((event)=>{
    //   console.log("状态触发组件--------------->");
    //   console.log(event);
    // })
    const refData = toRefs(data);
    const watchText = ref('yes')
    const watchFunction = ()=>{
      watchText.value = watchText.value + 'finnish'
      
    }
    // watch([watchText, () => data.selectA],(newValue, oldValue)=>{
    //   console.log('newValue', newValue[0]);
    //   console.log('oldValue', oldValue);
    //   // document.title = newValue[1]
    // })
    watch([watchText, () => data.selectA], (newValue, oldValue) => {
      console.log(`new--->${newValue}`);
      console.log(`old--->${oldValue}`);
      document.title = `${newValue[0]}`;
    });

    return {
      ...refData,
      watchText,
      watchFunction
    }
  },
  beforeCreate() {
    console.log("1-组件创建之前-----beforeCreate()");
  },
  beforeMount() {
    console.log("2-组件挂载到页面之前执行-----BeforeMount()");
  },
  mounted() {
    console.log("3-组件挂载到页面之后执行-----Mounted()");
  },
  beforeUpdate() {
    console.log("4-组件更新之前-----BeforeUpdate()");
  },
  updated() {
    console.log("5-组件更新之后-----Updated()");
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
