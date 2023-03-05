<template>
    <div class="black-bg" v-if="modal==true">
        <div class="white-bg">
        <img :src="oneRooms[oneRoomsData].image">
        <h4>{{ oneRooms[oneRoomsData].title }}</h4>
        <input type="text" v-model.number="month">
        <p>{{ month }}개월 선택 :  {{ oneRooms[oneRoomsData].price * month }}원</p>
        <p>{{ oneRooms[oneRoomsData].content }}</p>
        <DiscountBanner/>
        <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div><!-- modal -->
</template>

<script>
import DiscountBanner from '../component/DiscountBanner.vue';

export default {
    name : 'ModalCmp',
    components : {
        DiscountBanner
    },
    data() {
        return {
            month : 1,

        }
    },
    // 사용자의 input을 control
    watch : {
        month() {

        }
    },
    props : {
        modal : Boolean,
        oneRooms : Array,
        oneRoomsData : Number,
    },
    methods : {
    }
}
</script>

<style>
.black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    position: fixed;
    top: 0;
    padding: 40px;
}
.white-bg {
    width: 60%;
    background: #fff;
    border-radius : 8px;
    padding: 20px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.white-bg img {
    width: 90%;
}
.white-bg h4 {
    padding-top: 20px; padding-bottom: 10px;
    font-weight: 400; 
}
.white-bg input {
    margin-bottom: 10px;
    text-align: left;
    padding-left: 10px;
    outline: none;
}
</style>