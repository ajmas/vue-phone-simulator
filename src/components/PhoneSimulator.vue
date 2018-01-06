<template>
<div class="phone-simulator" v-bind:style="phoneSimulatorStyles">  
  <div class="phone" v-bind:style="phoneStyles">
    <iframe class="phone-screen" v-bind:style="phoneScreenStyles" :src="url" seamless="seamless" v-on:load="handleIFrameLoad"></iframe>
  </div>
</div>
</template>

<script>

const phones = {
  'iphone-6-white': {
    name: 'iPhone 6 (white)',
    filepath: 'iphone-6-white.png',
    imageDimensions: [482,982],
    screen: {
      left: 34,
      top: 126,
      width: 414,
      height: 736
    }
  },
  'google-pixel': {
    name: 'Google Pixel',
    filepath: 'google-pixel.png',
    imageDimensions: [470,964],
    screen: {
      left: 27,
      top: 109,
      width: 411,
      height: 731
    }    
  }  
};

export default {
  data: function () {
    return {
      baseUrl: '/img/phones',
      phones: phones
    }
  },
  props: {
      url: String,
      phone: {
        type: String,
        default: 'iphone-6-white'
      },
      scale: {
        type: Number,
        default: 0.25
      },
      height: {
        type: Number,
        default: null
      },
  },
  methods: {
    handleIFrameLoad: function (error) {
      console.log('xxx', error);
    },
    listPhones: function () {
      const keys = Object.keys(this.phones);
      return keys.map((key) => {
        return {
          id: key,
          name: this.phones[key].name
        } 
      });
    }
  },
  computed: {
    activePhone: function() {
      return this.phones[this.phone];
    },
    phoneStyles: function() {
      let style='';
      if (this.activePhone) {
        const imageDimensions = this.activePhone.imageDimensions;
        const filepath = this.activePhone.filepath;
        const width = imageDimensions[0];// * this.scale;
        const height = imageDimensions[1];// * this.scale;
        style = `width: ${width}px; height: ${height}px; `;
        style += `background-image: url(${this.baseUrl}/${filepath});`
        style += `transform: scale(${this.scale});transform-origin: 0 0;`
      }
      return style;      
    },
    phoneSimulatorStyles: function () {
      let style='';
        if (this.activePhone) {
        const imageDimensions = this.activePhone.imageDimensions;
        const width = imageDimensions[0] * this.scale;
        const height = imageDimensions[1] * this.scale;
        style = `width: ${width}px; height: ${height}px; `;
      }
      return style;         
    },
    phoneScreenStyles: function () {
      if (this.activePhone) {
        const screen = this.activePhone.screen;
        return `left: ${screen.left}px; top: ${screen.top}px; width: ${screen.width}px; height: ${screen.height}px;`;      
      }
    }
  }
}

</script>

<style>
.phone-simulator {
    position: relative;
}

.phone-screen {
    position: absolute;
    background: white;
}
</style>

// ref: https://dribbble.com/shots/1719571-iPhone-6-Sketch-Template
// ref: https://dribbble.com/shots/3004465-Google-Pixel-Mockup
// ref: https://material.io/devices/
// ref: https://webkit.org/blog/7929/designing-websites-for-iphone-x/