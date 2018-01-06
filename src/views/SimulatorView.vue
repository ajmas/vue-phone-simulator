<!-- This is just here for test the simulator, during development -->
<template>
<div>
  <simulator id="simulator" :url="url" :scale="scale" :phone="phone" class="simulator"></simulator>
  <form v-on:submit="handleSubmit">
  
  <div class="row"><label>URL:</label> <input type="text" name="url" size="100" :value="url" v-on:change="handleChange"/> <input type="submit" value="Apply" /></div>
  
  <div class="row"><label>Phone:</label> 
    <select v-model="phone" >
      <option v-for="entry in phones" :key="entry.id" :value="entry.id" >{{entry.name}}</option>
    </select>
  </div>

  <div class="row"><label>Scale:</label> <input type="range" min="25" max="100" :value="integerScale" v-on:change="changeScale"> </div>
  
  </form>

</div>   
</template>

<script>
import Simulator from '../components/PhoneSimulator';

export default {
  data: function() {
    return {
      url: 'https://vuejs.org/',
      integerScale: 60,
      tmpData: {},
      phone: 'google-pixel',
      phones: []
    };
  },
  components: { Simulator },
  mounted() {
    const phoneSimulator = simulator.__vue__;
    this.phones = phoneSimulator.listPhones();
    console.dir(phoneSimulator.listPhones());
  },
  updated() {
    console.log('...', this.phone)
    console.log('...', this.integerScale)
  },
  methods: {
    changeScale: function(event) {
      this.integerScale = parseInt(event.target.value);
    },
    // changePhone: function(event) {
    //   this.phone = event.target.value;

    //   console.log(event.target.value);
    // },
    handleSubmit: function(event) {
      event.preventDefault();

      const keys = Object.keys(this.tmpData);
      for (let i = 0; i < keys.length; i++) {
        this[keys[i]] = this.tmpData[keys[i]];
      }
    },
    handleChange: function(event) {
      this.tmpData[event.target.name] = event.target.value;
    }
  },
  computed: {
    scale: function() {
      return this.integerScale / 100;
    }
  }
};
</script>

<style>
.simulator {
  /* float: left; */
  display: inline-block;
  margin-left: 20px;
}

form {
  margin-left: 20px;
  margin-top: 10px;
  display: inline-block;
  vertical-align: top;
}

form .row {
  margin: 5px 0 5px 0;
  display: block;
}

form label {
   width: 75px;
   display: inline-block;
}
</style>