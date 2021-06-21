<template>
  <div>
      
          <h1>{{ appvuedata }}- header component</h1>
          <button v-on:click="sendEvent">Send</button>
          
  </div>
</template>

<script>
export default {
    props: ['appvuedata'],
    methods: {
        sendEvent: function() {
            this.$emit('emitdata');
            console.log('emit')
        }
    }
}
</script>

<style scoped>
h1 {border:2px solid #F0F;}

</style>