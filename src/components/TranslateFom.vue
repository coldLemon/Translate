<template>
  <div id="translateFom">
    <form @submit="formSubmit">
      <select class="select_op" v-model="language1">
        <option value="en">中英</option>
        <option value="ru">中俄</option>
        <option value="ko">中韩</option>
        <option value="ja">中日</option>
        <option value="fr">中法</option>
        <option value="pt">中葡</option>
        <option value="nl">中荷</option>
        <option value="el">中希</option>
        <option value="jv">中爪</option>
        <option value="hi">中甘</option>
      </select>
      <input class="search_put" type="text"  v-model="textToTranslate"  placeholder="在此输入你需要翻译的文字">
      <input class="submit" type="submit" value="翻译">
    </form>

  </div>
</template>
<script>


  export default {
    name: 'translateFom',
    data:function () {
      return{
        textToTranslate:'',
        language1:'en'
      }
    },
    methods:{
      formSubmit:function (e) {
        //alert(this.textToTranslate);
        this.$emit('formSubmit',this.textToTranslate,this.language1);     //事件注册
        e.preventDefault();
      },

    }
  }
</script>

<style>
  *{
    text-decoration: none;

    margin: 0;
  }
  #translateFom{
    margin: 0;
  }
  .search_put{
    height: 36px;
    width: 250px;
    border: 2px solid #c9c9c9;
    border-radius: 3px;
    font-family: 楷体;
    font-size: 18px;
    background-color: white;
  }
  .select_op{
    cursor:pointer;
    height: 36px;
    border: 2px solid #c9c9c9;
    border-radius: 3px;
    background-color: #e5e5e5;
    font-family: 楷体;

  }
  .submit{
    height: 36px;
    width: 72px;
    border: 0 none;
    cursor: pointer;
    font-family: 楷体;
    font-size: 15px;
    border-radius: 3px;
    color: white;
    background-color: red;
  }

</style>

