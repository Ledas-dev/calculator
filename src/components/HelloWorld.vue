<template>
  <div class="hello">
    <span class="text">Calculator</span>
    <form class="calculator"  v-on:submit.prevent>
      <input @keyup.enter="summ"
        type="text" placeholder="0" class="input-num" v-model="result">
      <button type="button" name="button" class="item col-1" @click="minusNum()">CE</button>
      <button type="button" name="button" class="item col-1" @click="zero()">C</button>
      <button type="button" name="button" class="item col-1" @click="minus()">D</button>
      <button
        type="button"
        name="button"
        class="operation col-1"
        v-for="(oper, index) in operation"
        :key="index"
        @click="input(oper)"
      >
        {{ oper }}
      </button>
      <button
        type="button"
        name="button"
        class="operation col-1"
        @click="summ()"
      >=</button>
    </form>
    <div class="num-cal">
      <button
        type="button"
        name="button"
        class="number"
        v-for="(num, index) in number"
        :key="index"
        :class="{'col-1': num.isActiv}"
        @click="input(num.x)"
      >
        {{ num.x }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return {
      number:[
        {x:1, isActiv:false},
        {x:2, isActiv:false},
        {x:3, isActiv:false},
        {x:4, isActiv:false},
        {x:5, isActiv:false},
        {x:6, isActiv:false},
        {x:7, isActiv:false},
        {x:8, isActiv:false},
        {x:9, isActiv:false},
        {x:'+-', isActiv:true},
        {x:0, isActiv:false},
        {x:'.', isActiv:true}
      ],
      operation:['+','-','/','*'],
      result:''
    }
  },
  methods:{
    input(char){
        this.result = this.result.toString()
        this.result += char + ''
    },
    zero(){
      this.result = ''
    },
    minus(){
      this.result = this.result.substring(0, this.result.length - 1)
    },
    summ(){
      event.preventDefault()
      this.result = eval(this.result)
    },
    minusNum(){
      if(Number(this.result)){
        this.result = ''
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator{
  width: 351px;
  height: 371px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.input-num{
  width: 99%;
  height: 84px;
  border: none;
  font-size: 30px;
  outline: 0;
  background-color: #E4E4E4;
  grid-column: 1/-1;
  text-align: right;
}
.text{
  width: 351px;
  font-style: normal;
  font-weight: normal;
  font-size: 28px;
  line-height: 33px;
  text-align: center;
}
.operation{
  grid-column: 5/4;
  width: 100%;
  height: 84px;
  padding: 20px;
  text-align: center;
  border: 1px solid #E4E4E4;
  outline: none;
  background: #fff;
  font-style: normal;
  font-weight: normal;
  font-size: 28px;
}
.col-1:hover{
  background: #E5E5E5;
}
.number{
  width: 100%;
  height: 84px;
  padding: 20px;
  text-align: center;
  border: 1px solid #E4E4E4;
  outline: none;
  background: #fff;
  font-style: normal;
  font-weight: normal;
  font-size: 28px;
  transition: 0.2s;
}
.number:hover{
  background: #E4E4E4;
}
button{
  padding: 0;
  margin: 0;
}
.item{
  width: 100%;
  height: 84px;
  padding: 20px;
  text-align: center;
  border: 1px solid #E4E4E4;
  outline: none;
  background: #fff;
  font-style: normal;
  font-weight: normal;
  font-size: 28px;
}
.col-1{
  background: #F3F3F3;
    transition: 0.2s;
}
.decision{
  margin-right: 20px;
  font-size: 18px;
line-height: 21px;
}
.answer{
  margin-right: 20px;
  margin-top: -20px;
  font-size: 32px;
}
.num-cal{
  width: 265px;
  position: relative;
  top:-201px;
  left:605px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
</style>
