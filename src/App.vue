<template>
<div>
  <h1>Vue Phone Simulator</h1>
  <SimulatorView></SimulatorView>
</div>
</template>

<script>
import SimulatorView from './views/SimulatorView';

export default {
  name: 'app',
  components: { SimulatorView },
  data () {
    return {
      data: '', 
      msg: 'Welcome to the Web Phone Simulator'
    }
  }
}
</script>

<style>
body {
    font-family: sans-serif;
}
</style>