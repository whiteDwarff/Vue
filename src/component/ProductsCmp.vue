<template>
    <div id="products-wrap">
        <div class="products" v-for="(data, i) in oneRooms" :key="i">
        <!-- html의 속성을 데이터바인딩 한다면 : 필요!! (style, class, src, href...)-->
        <img class="products-img" :src="data.image">
        <h4 :style="styleRed" @click="titleClickEventHandler(i)">{{ data.title }}</h4>
        <p>{{ `월 ${data.price}원`}}</p>
        <!-- v-on == @ (eventHandler) -->
        <button @click="countEventHandler(i)">허위매물신고</button>
        <span>신고 수 : {{ data.fakeReport + '회'}}</span>
        </div>
    </div><!-- product-wrap -->
</template>

<script>
export default {
    name : 'ProductsCmp',
    props : {
        oneRooms : Array,
        titleClickEventHandler : Function,
        countEventHandler : Function,
        styleRed : String,
    }
}
</script>

<style>

</style>