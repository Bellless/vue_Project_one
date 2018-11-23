<template xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <!--v-model它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理，
      v-model 会忽略所有表单元素的 value、checked、selected 特性的初始值而是将 Vue 实例的数据作为数据来源-->
      <!--那么 v-model 其实就是 v-bind 和 v-on 的语法糖-->
      <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Janpenese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
    return {
      //定义变量，在下面mothods中实现获取到变量的数据
      textToTranslate:"",
      language:""
    }
  },
  methods: {
    formSubmit:function(e){
      // alert(this.textToTranslate);
      //要使用http协议必须安装resource模块
      //注册一个http事件 --this.$emit
      this.$emit("formSubmit",this.textToTranslate,this.language);
      e.preventDefault();
    }
  },
  //页面渲染前自动执行的方法
  created:function(){
    //this就是上面data return出来的对象
    this.language = "en";
  }
}
</script>

<style>
  #transForm{
    border-radius: 10px;
    border: 1px #ccc solid;
  }
</style>
