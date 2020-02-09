<template>
      <div class="calculator">
        <input type="text" name="title" v-model="expression" placeholder="0" disabled>

        <div class="row">
          <div class="btn" @click="expressionBuild('(')">
          <p>(</p>
          </div>
          <div class="btn" @click="expressionBuild(')')">
            <p>)</p>
          </div>
          <div class="btn" @click="expressionErase">
            <p>C</p>
          </div>
          <div class="btn" @click="expressionBackSpace">
            <p>CE</p>
          </div>
        </div>

        <div class="row">
          <div class="btn" @click="expressionBuild(7)">
          <p>7</p>
          </div>
          <div class="btn" @click="expressionBuild(8)">
            <p>8</p>
          </div>
          <div class="btn" @click="expressionBuild(9)">
            <p>9</p>
          </div>
          <div class="btn" @click="expressionBuild('/')">
            <p>/</p>
          </div>
        </div>
        
        <div class="row">
          <div class="btn" @click="expressionBuild(4)">
          <p>4</p>
          </div>
          <div class="btn" @click="expressionBuild(5)">
            <p>5</p>
          </div>
          <div class="btn" @click="expressionBuild(6)">
            <p>6</p>
          </div>
          <div class="btn" @click="expressionBuild('*')">
            <p>X</p>
          </div>
        </div>

        <div class="row">
          <div class="btn" @click="expressionBuild(1)">
          <p>1</p>
          </div>
          <div class="btn" @click="expressionBuild(2)">
            <p>2</p>
          </div>
          <div class="btn" @click="expressionBuild(3)">
            <p>3</p>
          </div>
          <div class="btn" @click="expressionBuild('-')">
            <p>-</p>
          </div>
        </div>

         <div class="row">
          <div class="btn" @click="expressionBuild(0)" >
          <p>0</p>
          </div>
          <div class="btn" @click="expressionBuild('.')">
            <p>.</p>
          </div>
          <div class="btn" @click="expressionEvaluate">
            <p>=</p>
          </div>
          <div class="btn" @click="expressionBuild('+')">
            <p>+</p>
          </div>
        </div>

      </div>
</template>

<script>
export default {
    name: "Calculator",
    methods:{
      expressionBuild(num){
        var actions = "*+-./"
          if(this.answer==this.expression && !actions.includes(num+"")){
            this.answer=""
            this.expression = num+"";
          }
          else{
            this.expression +=num;
          }
      },
      expressionBackSpace(){
        this.expression = this.expression.substring(0,this.expression.length-1)
      },
      expressionErase(){
        this.expression = ""
      },
      expressionEvaluate(){
        var result;
        try{
          result = eval(this.expression)+""
        }
        catch(e){
          result  = e.message
        }
        this.expression=result;
        this.answer = this.expression
      }
    },
    data(){
      return{
        expression:"",
        answer:""
      }
    }
}
</script>

<style>
.row{
  display: flex;
  flex:1;
}
.calculator{
  font-size:30px;
  display: flex;
  flex-direction: column;
  width:600px;
  /* border:1px white solid; */
}
.btn{
  flex:1;
  margin:10px;
  /* border:5px rgb(32, 43, 56) solid; */
  background-color: #354357;
  padding: 0;
  transition: 0.2s all ease;
}
.btn p{
  background-color: inherit;
}
.btn:hover{
  background-color: #948CF8;
}
.btn:active{
  background-color: #6B63F9;
}
input[type="text"]{
  
  text-align: right;
  font-size: 50px;
  padding:30px 0;
  display:flex;
  width:98%;
  color:white;
  border:none;
}
input::placeholder{
  color:#354357
}
</style>