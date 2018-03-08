<template>
  <div id="app">
    <div id="navigation">
      <ul>
        <li><a href="#" class="navigation_link">文本</a> </li>
        <li><a href="#" class="navigation_link">翻译</a> </li>
        <li><a href="#" class="navigation_link">单词本</a> </li>
        <li><a href="#" class="navigation_link">找我啊</a> </li>
      </ul>
    </div>
    <h1>Translation</h1>
    <h5>都拉米法搜拉稀</h5>
    <div class="margin_a"></div>
    <translateFom v-on:formSubmit="translateText"></translateFom>
    <transOutput v-text="translatedText" class="output"></transOutput>
  </div>
</template>

<script>

import TranslateFom from './components/TranslateFom.vue'
import TransOutput from './components/TransOutput.vue'
export default {
  name: 'app',
  data:function () {
    return{
        translatedText:''
    }
  },
  components:{
    TranslateFom,TransOutput
  },
  methods:{
    translateText:function (text,language1) {
      this.$http.get('https://translate.yandex.net/api/v1.5' +
        '/tr.json/translate?key=trnsl.1.1.20180113T122227Z.a35fc16d2f104412.' +
        '4290b1c17e42cb10e214fdc5ed6c27e051be61cd&lang='+language1+'&text='+text)
        .then((responce)=>{
        //console.log(responce.body.text[0]);
          this.translatedText = responce.body.text[0]
      });
    }
  }
}
</script>

<style>
  *{
    margin: 0;
    list-style: none;
    text-decoration: none;
  }

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  h1{
    color:red;
    font-size: 7ex;
    font-family: 方正舒体;
    background-color: #f8f9ff;
  }
  h5{
    color: red;
    background-color: #f8f9ff;
  }
  #navigation{
    width: 100%;
    height: 50px;
    display: inline-block;
  }
  #navigation li{
    float: left;
    margin-left: 20px;
  }
  .navigation_link{
      font-size: 15px;
    text-align: center;
    font-weight: 200;
    color: #c9907b;
  }
  .margin_a{
    width: 100%;
    height: 65px;
    background-color: #f8f9ff;
  }
  .output{
    text-align: center;
    font-size: 70px;
    font-family: "Microsoft PhagsPa";
    color: #8648ff;
  }
</style>
