<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <div class="content">
      <translateForm @formSubmit="translate"></translateForm>
      <translateOutput :result="translateText"></translateOutput>
    </div>
    <router-view/>
  </div>
</template>

<script>
import translateForm from './components/translateForm';
import translateOutput from './components/translateOutput';
import axios from 'axios';
export default {
  name: 'app',
  data() {
    return {
      translateText: ''
    }
  },
  components:{
    translateForm,
    translateOutput
  },
  methods: {
    translate: function(text,language) {
      console.log(language);
      axios.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20191016T141651Z.0c99c8f85dcfcc81.df604d8f582e437beabeaf31f6f7aaffbd74ec9e&lang=' + language + '&text=' + text).then(res => {
        console.log(res)
        this.translateText = res.data.text[0];
      });
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

h5 {
  color: #ccc;
}
.content {
  width: 650px;
  margin: 0 auto;
  border: 1px solid #ccc;
  border-radius: 10px;
}

</style>
