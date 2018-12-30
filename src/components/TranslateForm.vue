<template>
<div id="translateForm">
  <form v-on:submit="formSubmit" class="jumbotron col-md-auto m-md-5">
    <input type="text" v-model="textToTranslate" placeholder="输入需要的翻译内容" class="form-control w-25 d-inline">
    <select v-model="language" class="btn custom-select w-auto">
      <option value="en">English</option>
      <option value="ru">Russian</option>
      <option value="ko">Korean</option>
      <option value="ja">Janpenese</option>
    </select>
    <input type="submit" value="翻译" class="btn btn-primary">
  </form>
</div>
</template>
<script>
  export default{
    name:'translateForm',
    data(){
      return{
        textToTranslate:"",
        language:"en"
      }
    },
    methods:{
      formSubmit:function(e){
//        alert(this.textToTranslate);
        this.$emit("formSubmit",this.textToTranslate,this.language);
        e.preventDefault();
      }
    }

  }
</script>
<style>

</style>
