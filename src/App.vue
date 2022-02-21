<template>
  <div id="app"  >
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
   <!-- <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div> -->
    <div class="contenedor" :style="{ background: '#' + color}">
    <img @mouseover="toggleShowPrices" @mouseout="toggleShowPrices" :src="img" :alt="name">
    <h1 :class="changePercent > 0 ? 'green': 'red'">{{title}}
      <span> {{changePercent > 0 ? '👍' : (changePercent==0? '🤞' : '👎') }}</span>
      <span  @click="toggleShowPrices">{{ShowPrices ? '🙊' : '🙈'}}</span>
    </h1>
    <input type="number" v-model="value">
    <span>{{value}}</span>
    <ul  v-show ="ShowPrices">
      <li :class="{orange: p.value === price , red: p.value < price , green: p.value > price}" 
      v-for="(p , i) in  pricesWithDays" :key="p.day" >
        {{i}} - {{p.day}} - {{p.value}}
      </li>
    </ul>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      name:'bitcoin',
      symbol:'BTC',
      img:'https://cryptologos.cc/logos/bitcoin-btc-logo.png',
      changePercent:-10,
         pricesWithDays: [
                { day: 'Lunes', value: 8400 },
                { day: 'Martes', value: 7900 },
                { day: 'Miercoles', value: 8200 },
                { day: 'Jueves', value: 9000 },
                { day: 'Viernes', value: 9400 },
                { day: 'Sabado', value: 10000 },
                { day: 'Domingo', value: 10200 },
            ],
      ShowPrices: false,
      price:8400,
      color:'f4f4f4',
      value:0
    }
  },
  computed: {
    title () {
      return `${this.name} - ${this.symbol}`
    }
  },
  watch:{
    ShowPrices(newVal, olVal){
     console.log(newVal, olVal)
    }
  },
  components: {
   
  },
  methods:{
    toggleShowPrices(){
      this.ShowPrices = !this.ShowPrices
      this.color = this.color.split('').reverse().join('')
    }
  }
  
}

</script>

<style>

/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
