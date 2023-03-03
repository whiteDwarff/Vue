<template>
    <div id="discount-banner">
        <h4>지금 결제하면 20% 할인!</h4>
    </div>
</template>

<script>
export default {
    name: 'DiscountBanner',
}
</script>

<style>
#discount-banner{
    background-color: #eee;
    padding: 30px;
    margin: 30px;
    border-radius: 5px;
}
</style>
<!--
    components 쓰는 법
        - 1. vue 파일 import 해오기
        - 2. 등록하기 
                ( object 내 components 공간에 )
                object의 key와 value가 같을 때 key 값만 사용해도 오류 발생 x
        - 3. 사용
-->