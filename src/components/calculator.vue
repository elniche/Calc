<template>
  <div class="background">
      <!-- calculator result -->
   <div class="wan"> 
     {{calculatorValue || 0}}
   </div>

   <!-- calulator button -->
   <div class="row">
     <div class="col-3" v-for="n in calculatorElements" :key="n">
         <div class= "leader text-black text-center m-1 py-3 bg-vue-dark rounded hover-class" :class="{'bg-vue-green': ['C','*','/','-','+','%','='].includes(n)}" @click="actor(n)">
             {{n}}
         </div>
      </div>
   </div>
   
  </div>


</template>


<script>
export default {
  name: 'calculator',
  props: {
    msg: String
  },

  data() {
    return {
      calculatorValue: '',
      calculatorElements: ['C','*','/','-','7','8','9','+','4','5','6','%','1','2','3', '=','0','.'],
      operator: null,
      previousCalc: '',
    }
  },
  methods: {
    actor(n) {
      if(!isNaN(n) || n === '.') {
        this.calculatorValue += n + '';
      }

      /* to clear */
  if(n === 'C') {
    this.calculatorValue = '';
  }

  if(n === '%') {
    this.calculatorValue = this.calculatorValue / 100 + '';
  }

  if(['/','*','-','+'].includes(n)) {
this.operator = n;
this.previousCalc = this.calculatorValue;
this.calculatorValue = '';
  }

  if(n === '=') {
    this.calculatorValue = eval(
       this.previousCalc + this.operator + this.calculatorValue
    )

    /*  reset  */
    this.previousCalc = '';
    this.operator = null;
  }

    }
  }
}
</script>


<style scoped>

.background {
  max-width: 400px;
  margin: 50px auto;
  background:lightblue;
}

.wan {
  background-color: blue;
}

.hover-class:hover {
  cursor: pointer;
  background: white;
}

.bg-vue-green {
  background: darkcyan;
}
</style>
