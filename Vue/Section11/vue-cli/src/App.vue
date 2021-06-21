<template>
<div id="app">
    {{ str }}
    <app-header 
    v-bind:appvuedata="object_return" 
    v-on:emitdata="emitHeaderData"></app-header>
    
</div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
export default {
  // 기존에  new Vue 인스턴스에서 이렇게 사용하던것이 
  // Cli에서는 여러 컴포넌트를 사용하는데, 데이터를 재사용해야하고
  // 그렇다면 데이터는 공유되면 안됌. 그래서 객체 반환방식 아래처럼 사용
  // data: {
  //   str: 'TestStr',
  // }
  data: function(){
    return {
      // str : 'appvueStringData',
      object_return: '데이터 객체로 반환'
    }
  },
  components: {
    'app-header' : AppHeader
  },
  methods: {
    emitHeaderData: function() {
      this.object_return = 'emit 데이터 변경 확인'
      console.log('appvue emitHeaderData()')
    },
  }
  
}
</script>

<style>

</style>
