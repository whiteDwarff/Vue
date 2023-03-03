<template>


  <ModalCmp
  :oneRooms="oneRooms" 
  :titleClickEventHandler="titleClickEventHandler"
  :oneRoomsData="oneRoomsData"
  :modal="modal"/>
  <!-- modal -->
  <div class="menu">
    <a v-for="(data, i) in menu" :key="i">{{ data }}</a>
  </div><!-- nav -->
  <DiscountBanner/>
  <ProductsCmp
  :oneRooms="oneRooms"
  :styleRed="styleRed"
  :titleClickEventHandler="titleClickEventHandler"
  :countEventHandler="countEventHandler"
  />



</template>
<script>

import {apple, apple2} from './script/oneroom.js';
console.log(apple, apple2);

// 외부파일을 가져옴 
import data from './script/oneroom.js';
import DiscountBanner from './component/DiscountBanner.vue';
import ModalCmp from './component/ModalCmp.vue';
import ProductsCmp from './component/ProductsCmp.vue';

export default {
  name: 'App',
  data() {
    return {
      // 데이터 보관함, 데이터는 object 자료로 저장, 데이터의 이름 : 값
      menu : ['Home', 'Shop', 'About'],
      oneRooms : data,
      oneRoomsData : 0,
      styleRed : 'color: red',
      modal : false,
    }
  },
  methods : {  
    // function 선언부
    // 함수 내에서 데이터를 쓸 경우 this 연산자 사용
    countEventHandler(i) {
      this.oneRooms[i].fakeReport++;
    },
    titleClickEventHandler(i) {
      this.modal = true;
      this.oneRoomsData = i;
    }
  },
  components: {
    DiscountBanner,
    ModalCmp,
    ProductsCmp,
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  text-decoration: none;
  font-size: 16px;
  font-weight: 200;
  text-align: center;
  box-sizing: border-box;
}

.menu {
  width: 100%;
  background-color: darkslateblue;
  padding: 15px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}
#products-wrap {  
  width: 100%;
  border-top: 1px solid black;
  border-left: 1px solid black;
}
.products {
  width: 33.33%;
  display: inline-block;
  padding-bottom: 30px;
  border-right: 1px solid black;
  border-bottom: 1px solid black;
}
.products-img {
  width: 90%;
  margin: 30px 0;
}
.products h4 {
  font-weight: 400;
}
.products p {
  margin: 10px 0;
}
.products button {
  margin-right: 10px;
}
</style>
