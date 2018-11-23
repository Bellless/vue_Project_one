<template xmlns:v-on="">
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>

  import TranslateForm from './components/TranslateForm'
  import TranslateOutput from './components/TranslateOutput'

  export default {
    name: 'app',
    data:function(){
      return{
        //定义一个变量，在下面mothods中实现获取到变量的数据并在v-text中显示
        translatedText:""
      }
    },
    components: {
      TranslateForm,TranslateOutput
    },
    methods:{
      translateText:function(text,language){
        // alert(text);
        //获取到注册的http请求到指定的页面
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170721T082515Z.54cf3dc583f679db.f4a96182281281d8b5dfe24b4e88298e2133f219&lang='+language+'&text='+text)
          //请求到数据后使用response执行请求数据输出
          .then((response)=>{
            // console.log(response.body.text[0]);
            this.translatedText = response.body.text[0];
          })
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
