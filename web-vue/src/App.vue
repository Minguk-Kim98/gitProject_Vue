<template>
  <div id="app">
    <Webtoon :items="webtoons"/>
  </div>
  <div>
    <h2>찜목록</h2>
    <input type="checkbox" id="프롬스타" value="프롬스타" v-model="checkedWebtoons">
    <label for="프롬스타">프롬스타</label>
    <input type="checkbox" id="햄스터와그녀" value="햄스터와 그녀" v-model="checkedWebtoons">
    <label for="햄스터와그녀">햄스터와그녀</label>
    <input type="checkbox" id="위대한로맨스" value="위대한 로맨스" v-model="checkedWebtoons">
    <label for="위대한로맨스">위대한로맨스</label>
    <input type="checkbox" id="아귀" value="아귀" v-model="checkedWebtoons">
    <label for="아귀">아귀</label>
    <br>
    <span>찜한 웹툰 : {{ checkedWebtoons }}</span>
  </div>
</template>

<script>

import Webtoon from "@/components/Webtoon";
export default {
  components: {
    Webtoon
  },
  data() {
    return {
      webtoons: [
        {
          name: "햄스터와 그녀",
          link: "http://webtoon.daum.net/webtoon/view/hamsterandher",
          img: "http://t1.daumcdn.net/webtoon/op/478cdf37f585607982ffa9e35b432e8503be8a54",
          isUpdate : true
        },
        {
          name: "프롬 스타",
          link: "http://webtoon.daum.net/webtoon/view/fromstar",
          img: "http://t1.daumcdn.net/webtoon/op/a7fb953d722c1130bfc18440f7e3ce448ece57a1",
          isUpdate : true
        },
        {
          name: "위대한 로맨스",
          link: "http://webtoon.daum.net/webtoon/view/greatromance",
          img: "http://t1.daumcdn.net/webtoon/op/a816281cb4df5c50a20ac386fd6e496643d0f085",
          isUpdate : false
        },
        {
          name: "빛나는 손을",
          link: "http://webtoon.daum.net/webtoon/view/Hand",
          img: "http://t1.daumcdn.net/cartoon/5913FCAC0234C50001",
          isUpdate : false
        }
      ],
      title : "",
      checkedWebtoons : []
    };
  }
}
</script>

<style>
</style>
