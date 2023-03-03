<template>

  <div class="menu">
    <!-- 
      v-for : 
      <tagName v-for="data in 반복횟수 || data" :key="data">{{ data }}</tagName>
      - html 내 반복문
      - in은 참조할 데이터 입력
      - key 없을 시 오류발생, 반복문 돌린 요소를 컴퓨터가 구분하기 위해 사용 (data의 index)
      - data 입력 시 data의 갯수만큼 반복실행
    -->
    <a v-for="(data, i) in menu" :key="i">{{ data }}</a>
  </div>
  <div v-for="(data, i) in products" :key="i">
    <h4 :style="style">{{ data }}</h4>
    <p>{{ price[i] }}</p>
    <button @click="countEventHandler(i)">허위매물신고</button>
    <span>신고 수 : {{ count[i] }}</span>
  </div>

</template>
<script>

export default {
  name: 'App',
  data() {
    return {
      // 데이터 보관함, 데이터는 object 자료로 저장, 데이터의 이름 : 값
      menu : ['Home', 'Shop', 'About'],
      style : 'color : red',
      price : [50, 70, 85],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      count : [0,0,0]
    }
  },
  methods : {
    countEventHandler(i) {
      this.count[i]++;
    }
  },
  components: {
  }
}
/*
  데이터 바인팅 하는 이유  {{ }}
    - HTML 하드 코딩 시 변경작업이 까다롭다.
    - vue가 제공하는 실시간 렌더링 기능을 쓰려면 필요함 (웹앱 )
    - 자주 변하는 데이터들은 데이터로 보관해야한다!!
*/
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius : 5px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}
</style>
