<template>
    <div class="black-bg" v-if="modal==true">
        <div class="white-bg">
        <img :src="oneRooms[oneRoomsData].image">
        <h4>{{ oneRooms[oneRoomsData].title }}</h4>
        <p>{{ oneRooms[oneRoomsData].content }}</p>
        <DiscountBanner/>
        <button @click="$emit('modalClose')">닫기</button>
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
    props : {
        oneRooms : Array,
        oneRoomsData : Number,
        // modal : Boolean
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
</style>