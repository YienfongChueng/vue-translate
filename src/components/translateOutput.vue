<template>
  <div class="translateOutput">
    <h2>{{result}}</h2>
  </div>
</template>

<script>

export default {
  name: 'translateOutput',
  props:["result"]
  
}
</script>

<style lang="scss">
  .translateOutput {
    height: 200px;
    width: 600px;
    font-size: 18px;
    color: #000;
    margin: 0 auto;
  }
</style>
