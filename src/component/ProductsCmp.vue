<template>
    <div class="products">
        <img class="products-img" :src="oneRooms.image">
        <h4 :style="styleRed" @click="$emit('openModal')">{{ oneRooms.title }}</h4>
        <p>{{ `월 ${oneRooms.price}원` }}</p>
        <button @click="$emit('fakeReport')">허위매물신고</button>
        <span>신고 수 : {{ oneRooms.fakeReport + '회'}}</span>
    </div>
</template>

<script>
export default {
    name : 'ProductsCmp',
    props : {
        oneRooms : Object,
        styleRed : String,
    }
}
</script>

<style>

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
    cursor: pointer;
}
.products p {
    margin: 10px 0;
}
.products button {
    margin-right: 10px;
    padding: 5px;
    cursor : pointer;
}
</style>