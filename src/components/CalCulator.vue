<template>
  <div>
    <h1>Calculator Using Javascript</h1>
    <div class="Calculator"  style="margin-top: 10px;">
    
    <div class="Dis">{{ current || 0 }}</div>
    <div @click="clear" id="btnA" value="AC" type="button" >
      AC
    </div>
    <div @click="sign" id="btns">+/-</div>
    <div @click="add" id="btns" value="+" type="button" onclick="">+</div>
    <div @click="sub" id="btns" value="-" type="button" onclick="">-</div>
    <div @click="append(7)" id="btn" value="7" type="button" onclick="">7</div>
    <div @click="append(8)" id="btn" value="8" type="button" onclick="">8</div>
    <div @click="append(9)" id="btn" value="9" type="button" onclick="">9</div>
    <div @click="multiply" id="btns" value="*" type="button" onclick="">*</div>
    <div @click="append(4)" id="btn" value="4" type="button" onclick="">4</div>
    <div @click="append(5)" id="btn" value="5" type="button" onclick="">5</div>
    <div @click="append(6)" id="btn" value="6" type="button" onclick="">6</div>
    <div @click="divide" id="btns" value="/" type="button" onclick="">/</div>
    <div @click="append(1)" id="btn" value="1" type="button" onclick="">1</div>
    <div @click="append(2)" id="btn" value="2" type="button" onclick="">2</div>
    <div @click="append(3)" id="btn" value="3" type="button" onclick="">3</div>
    <div @click="dot" id="btn" value="." type="button" onclick="">.</div>
    <div
      @click="append(0)"
      id="btn0"
      value="0"
      type="button"
      onclick=""
      style="grid-column: 1/3"
    >
      0
    </div>
    <div
      @click="equal"
      id="btne"
      value="="
      type="button"
      onclick=""
      style="grid-column: 3/5"
    >
      =
    </div>
  </div>

</div>
</template>

<script>
export default {
  name: "CalCulator",
  data() {
    return {
      current: "",
      pre: null,
      oc: false,
      operator: null,
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    append(number) {
      if(this.oc){
        this.current='';
        this.oc=false;
      }
      this.current = this.current + number;
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setpre(){

      this.pre = this.current;
      this.oc = true;
    },
    divide() {
      // this.append('/');
      this.operator = (a, b) => b/a;
      this.setpre();
    },
    multiply() {
      // this.append('*');
      this.operator = (a, b) => a * b;
      this.setpre();

    },
    add() {
      // this.append('+');
      this.operator = (a, b) => a + b;
      this.setpre();

    },
    sub() {
        // this.append('-');
      this.operator = (a, b) => b-a;
      this.setpre();

    },
    equal(){
      this.current= this.operator(
        parseFloat(this.current),
        parseFloat(this.pre));  
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? 
        this.current.slice(1) : `-${this.current}`;
    },
  },
};
</script>
<style >
.Calculator {
  display: grid;
  grid-column: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  width: 40%;
  
  margin: auto;
}
#btnA{
  background-color:red;
  color:black;
  font-weight:1000 ;
  padding:20px;
  border: 2px solid blue;

}
#btnA:hover{
  background-color: aqua;
}
.Dis {
  grid-column: 1/5;
  width: 550px;
  margin: auto;
  padding: 20px;
  font-size: 30px;
  text-align: right;
  color: white;
  border: 2px solid blue;

  background-color: black;
}
#btn {
  background-color: green;
  border: 2px solid blue;
  color: white;
  text-align: center;
  padding: 20px;
}
#btn:hover{
  background-color: greenyellow;
}
#btns{
  background-color: yellow;
  border: 2px solid blue;
  color: white;
  text-align: center;
  padding: 20px;
  color:black;
  font-weight: 600;
}
#btns:hover{
  background-color: palegreen;
}
#btn0 {
  grid-column: 1/3;
  background-color: green;
  border: 2px solid blue;
  color: white;
  text-align: center;
  padding: 20px;
}
#btne {
  grid-column: 3/5;
  border: 2px solid blue;
  color: black;
  text-align: center;
  padding: 20px;

  background-color: red;
  border: 2px solid blue;
}
#btne:hover{
  background-color: aqua
}
#btn0:hover{
  background-color: yellowgreen;
}
</style>
