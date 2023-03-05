<template>


  <ModalCmp
  @closeModal="modal=false"
  :modal="modal"
  :oneRooms="oneRooms"
  :oneRoomsData="oneRoomsData"/> <!-- modal -->
  <div class="menu">
    <a v-for="(data, i) in menu" :key="i">{{ data }}</a>
  </div><!-- nav -->
  <DiscountBanner/>

  <div id="products-wrap">
  <ProductsCmp v-for="(data, i) in oneRooms" :key="i"
  @openModal="titleClickEventHandler(i)"
  @fakeReport="countEventHandler(i)"
  :oneRooms="oneRooms[i]"
  :styleRed="styleRed"
  /><!-- product -->
</div>

</template>
<script>
// oneRooms Data 
import data from './script/oneroom.js';
// components
import DiscountBanner from './component/DiscountBanner.vue';
import ModalCmp from './component/ModalCmp.vue';
import ProductsCmp from './component/ProductsCmp.vue';

export default {
  name: 'App',
  data() {
    return {
      // 데이터 보관함, 데이터는 object 자료로 저장, 데이터의 이름 : 값
      // event가 발생하는 순서 : title클릭 -> oneRoomsData 변경 -> modal열기
      menu : ['Home', 'Shop', 'About'],
      oneRooms : data,
      oneRoomsData : 0,
      styleRed : 'color: red',
      modal : false,
    }
  },
  methods : {  
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
</style>
