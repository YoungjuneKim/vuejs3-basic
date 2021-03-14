<template>
  <h1> Hello {{animal}}, Welcome vue3 world~ </h1>
  <h2> {{food}} 줄까? </h2>
  <h2 v-text="food"></h2>
  <input type="text" v-model="food" />
  <div v-html="alertMessage"></div>
  <div v-html="subscribeHTML"></div><br><br>
  <img v-bind:src="imgageSource" alt="random"><br><br>
  <a v-bind:href="naverUrl"> Naver </a> || 
  <a :href="naverUrl"> Naver </a><br><br>
  <input type="text" v-model="naverUrl" />
  ||| <a :href="naverUrl"> {{naverUrl}} </a>
  <hr/><br>
 
  <!-- v-bind:class="{'클래스명':조건}" -->
  <h2 v-bind:class="{'red':food==='apple', 'not-good':food==='rice', 'orange':food==='banana'}"> 원숭이는 {{food}}를 좋아합니다. </h2>
  <hr/><br>

  <div>
    <h2> 당신의 나이는 {{age}}살 입니다. </h2>
    <input type="text" v-model="age" />
    <h3 v-if="age>45"> 당신은 늙었습니다. </h3>
    <h3 v-else-if="age<=13"> 애들은가라. </h3>
    <h3 v-else-if="age>13&&age<=18"> 아직 여유가 있어요. </h3>
    <h3 v-else> 당신은 곧 늙을것입니다. </h3>
  </div>
  <hr/><br>

  <div>
    <h2 v-if="display"> v-if </h2>
    <h2 v-show="display"> v-show </h2><br>

    <h2> {{animals}} </h2>
    <h2 v-for="anim in animals" :key="anim"> {{anim}} </h2><br>
    <h2 v-for="(anim,index) in animals" :key="index"> {{index}} - {{anim}} </h2><br>
    
    <template v-for="(anim,index) in animals" :key="index"> 
      <h2 v-if="anim!=='dog'"> {{index}} - {{anim}} </h2>
    </template><br><br>

    <ul>
      <li v-for="(user, index) in users" :key="index"> {{user}} </li>
      <li v-for="(user, index) in users" :key="index"> Name : {{user.name}}, Job : {{user.job}}
        <p v-for="(skill, item) in user.skills" :key="item"> {{item}} - {{skill}}
        </p>
      </li>
    </ul>
  </div>
  <hr/><br>

  <div>
    <h1> {{count}} </h1>
    <button v-on:click="addNumber($event, 1)">증가</button> || 
    <button v-on:click="minusNumber">감소</button> ||
    <button v-on:mouseover="addNumber($event, 10)">10증가</button><br>
    
    <h2>{{message}} </h2>
    <button @click="greeting">인사하기</button>
    <button @click="goodbye">작별하기</button><br><br><br><br>
    <h2>{{mouseposition}} </h2>
    <div @mouseover="getMousePosition" class="box"></div>
  </div>

</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data:()=>{  //data () {
    return {
      animal:"Monkey",
      food:"banana",
      alertMessage: "<h2> Warnning!! </h2>",
      //subscribeHTML: `<button onclick="document.querySelector('body').style.background='red'">구독</button>`
      subscribeHTML: `<button onclick="document.querySelector('body').style.display='none'">구독</button>`,
      imgageSource: "https://placeimg.com/100/100/any",
      naverUrl: "https://www.naver.com",
      age: 50,
      display: true,
      animals:["dog", "cat", "tiger", "lion"],
      users: [
          {name:"kim", job:"free", gender:"male", age:11, skills:["java", "script", "c++"]},
          {name:"young", job:"samsung", gender:"female", age:21, skills:["cobol", "fortran", "delphi"]},
          {name:"june", job:"sds", gender:"male", age:31, skills:["react", "vue", "spring"]}
      ],
      count:0,
      message:"",
      mouseposition:"",
    };
  },
  methods:{
    addNumber(e, value) {
      console.log(e) ;
      this.count= this.count+value;
    },
    minusNumber() {
      this.count= this.count-1;
    },
    greeting() {
      this.message="Hey~ man!!" ;
    },
    goodbye() {
      this.message="Good Bye!!";
    },
    getMousePosition(e) { //파라메터가 없을때
      this.mouseposition=`마우스위치는 : pageX: ${e.pageX}, pageY: ${e.pageY} 마우스위치는 입니다` ;
    }, 
  },
  components: {
    //HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
input {
  font-size: 20px;
}
.orange {
  color : orange
}
.salmon {
  color : salmon
}
.red {
  color : red
}
.not-good {
  text-decoration: line-through
}
.box {
  width : 100px;
  height : 100px;
  background: orange
}
</style>
