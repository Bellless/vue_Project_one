
<template>
  <div id="translateOutput">
    <h2>{{translatedText}}</h2>
  </div>
</template>

<script>


export default {
  name: 'translateOutput',
  //定义props变量，接收父组件传递过来的内容(父组件向子组件中传递数据)
  props:[
  	"translatedText"
  ]

}
</script>

<style>

</style>
