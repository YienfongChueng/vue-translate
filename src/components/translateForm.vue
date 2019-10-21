<template>
  <div class="translateForm">
    <form @submit="formSubmit">
        <input class="translateText" type="text" v-model="textToTranslate" placeholder="请输入翻译内容" />
        <select class="language" v-model="language">
            <option value="en">English</option>
            <option value="ko">Korean</option>
            <option value="es">Spanish</option>
            <option value="de">German</option>
            <option value="ja">Japanese</option>
            <option value="ru">Russian</option>
        </select>
        <input class="btn" type="submit" value="翻译" />
    </form>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data() {
      return {
          textToTranslate: '',
          language: ''
      }
  },
  methods: {
      formSubmit: function(e) {
          this.$emit('formSubmit',this.textToTranslate,this.language);
          e.preventDefault();
      }
  },
  created() {
    this.language = 'en';
  }
}
</script>

<style lang="scss">
  .translateForm {
    width: 600px;
    margin: 0 auto;
    padding: 10px;
  }
  .translateText {
    width: 400px;
    height: 30px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 5px;
  }
  .language {
    width: 100px;
    height: 30px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-left: 5px;
    margin-right: 5px;
  }
  .btn {
    width: 60px;
    height: 30px;
    padding: 5px;
    background: rgb(24, 174, 233);
    color: #fff;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
</style>
