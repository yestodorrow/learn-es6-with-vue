<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
      <input type="text" placeholder="输入需要翻译的内容" v-model="textToTranslate">
      <select name="" id="">
        <option value="en">英文</option>
      </select>
      <input type="submit" value="翻译">
    </form>
  </div>
</template>

<script>


  export default {
    name: 'translateForm',
    data(){
        return{
            textToTranslate:""
        }
    },
    methods:{
        formSubmit:function(e){
            e.preventDefault();
            this.$emit("formSubmit",this.textToTranslate);
            alert(this.textToTranslate)
        }
    }

  }
</script>

<style>

</style>
