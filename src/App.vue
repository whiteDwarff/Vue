<template>

<Transition name="fade">
  <ModalCmp 
  @closeModal="modal=false"
  :modal="modal"
  :oneRooms="oneRooms"
  :oneRoomsData="oneRoomsData"/> <!-- modal -->
</Transition>
  <div class="menu">
    <a v-for="(data, i) in menu" :key="i">{{ data }}</a>
  </div><!-- nav -->
  
  <DiscountBanner
  v-if="showDiscount==true"/>


  <select name="" id="option" @change="selectOption">
    <option value="0">기본순정렬</option>
    <option value="1">가격낮은순</option>
    <option value="2">가격높은순</option>
    <option value="3">이름빠른순</option>
    <option value="4">이름느린순</option>
  </select>
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
      orgData : [...data],
      oneRoomsData : 0,
      styleRed : 'color: red',
      modal : false,
      showDiscount : true,
      orgCount : 20
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
    },
    selectOption() {
      const selectOption = document.getElementById('option').value;
      if(selectOption == 0) this.oneRooms = [...this.orgData];
      else if(selectOption == 1) 
        this.oneRooms.sort((a,b) => { return a.price - b.price });
      else if(selectOption == 2)
        this.oneRooms.sort((a,b) => { return b.price - a.price });
      else if(selectOption == 3) {
        this.oneRooms.sort( (a,b) => {
          return a.title < b.title ? -1 : a.title > b.title ? 1 : 0;
        })
      } else {
        this.oneRooms.sort( (a,b) => {
          return b.title < a.title ? -1 : b.title > a.title  ? 1 : 0;
        })
      }
    }
  },
  created() {

  },
  beforeMount() {
    // mount되기 전에 코드를 실행할게 ~
  },
  mounted() {
    // mount되고 나서 코드를 실행할게 ~
    // setTimeout(() => {
    //   this.showDiscount = false;
    // },2000) 
    setInterval(() => {
      const bannerText = document.querySelector('#discount-banner h4');
      let count = this.orgCount;
      if(count) {
        bannerText.innerText = `지금 결제하면 ${count--}% 할인!`;
        this.orgCount = count;
      }
    }, 1000)
  
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
/* 시작 스타일 */
.fade-enter-from { opacity: 0; }
.fade-enter-active { transition: ease-in-out .3s; }
  /* 종료 스타일 */
.fade-enter-to { opacity: 1; }
/* 시작 스타일 */
.fade-leave-from { opacity: 1; }
.fade-leave-active { transition: ease-in-out .3s; }
  /* 종료 스타일 */
.fade-leave-to { opacity: 0; }
</style>
