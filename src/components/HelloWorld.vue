<template>
  <div class="hello">
  <div class = "input_div">
    <div class="val">
      {{txt}}
    </div>
  
    <table >
  <tr>
    <button @click ="clear" class="AC" type="button">AC</button>
    <button @click = "sign" class="AC" type="button">+/-</button>
    <button @click = "percent" class= "AC" type="button">%</button>
    <button @click = "devide" class= "operator" type="button">/</button>
  </tr>
  <tr>
   <button @click="print" type="button">7</button>
    <button @click="print" type="button">8</button>
    <button @click="print" type="button">9</button>
    <button @click ="multi" class= "operator" type="button">*</button>
  </tr>
  <tr>
    <button @click = "print" type="button">4</button>
    <button @click = "print" type="button">5</button>
    <button @click = "print" type="button">6</button>
    <button  @click = "minus" class= "operator" type="button">-</button>
  </tr>
   <tr>
    <button @click = "print" type="button">1</button>
    <button @click = "print" type="button">2</button>
    <button @click = "print" type="button">3</button>
    <button @click = "add" class= "operator" type="button">+</button>
  </tr>
  <tr>
    <button @click = "print" class ="zero" type="button">0</button>
    <button @click = "dot" type="button">.</button>
    <button @click = "output" class ="operator" type="button">=</button>
  </tr>
</table>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      txt: "",
      operator: '',
      previous: "",
      checkoperator: false
    }
  },
   methods: {
    print: function (event) {
      if(this.checkoperator)
      {
        this.txt ="";
        this.checkoperator = false;
      }
      this.txt += event.target.innerText
    },
    clear: function(){
     this.txt =""

    },
    sign: function(){
     this.txt = this.txt.charAt(0) === '-' ? this.txt.slice(1) : '-'+ this.txt;
    },
    percent(){
      this.txt = parseFloat(this.txt)/100;
    },
    dot(){
      if(this.txt.indexOf('.') === -1)
      {
        this.txt =  this.txt + '.';
      }
    },
    setprevious(){
     this.previous = this.txt;
     this.checkoperator = true;
    },
    devide(){
      this.operator = (a,b) => a/b;
     this.setprevious();
    },
    add(){
      this.operator = (a,b) => a+b;
      this.setprevious();
    },
    minus(){
      this.operator = (a,b) => a-b;
      this.setprevious();
    },
    multi(){
      this.operator = (a,b) => a*b;
      this.setprevious();
    },
    output(){
      this.txt = this.operator(parseFloat(this.txt),parseFloat(this.previous));
      this.previous = null
    }

  }
} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.input_div {

  width: 275px;
  height: 443px;
  background-color:black;
  .val {
    color: white;
    height: 85px;
    font-size: 24px;
    
  }
}
button {
  background-color:#696969;
  border: none;
  color: white;
  
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 10px 8px;
  width:50px;
  height: 50px;
outline:none;
border:none;
   border-radius: 50%;
   box-shadow: 0 8px 16px 0 rgba(0,0,0,1), 0 6px 20px 0 rgba(0,0,0,0.19);
   
}


button:hover {
  box-shadow: 0 12px 16px 0 rgba(100,39,22,1), 0 17px 50px 0 rgba(100,39,22,1);
}
.operator
{
  background-color: orange
}
.AC{
     background-color: #C0C0C0;
     text-decoration: none;

   }
   .zero{
     border-radius:42px;
     width:116px
   }
 
   
</style>
