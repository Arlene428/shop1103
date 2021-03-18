<template>
  <div>
    <!-- 标题 -->
    <van-nav-bar title="首页" fixed />
    <van-swipe class="my-swipe" :autoplay="2000" indicator-color="white">
      <van-swipe-item v-for="item in bannerList" :key="item.id">
        <img :src="$preImg + item.img" alt="" />
      </van-swipe-item>
    </van-swipe>
    <van-tabs v-model="active">
      <van-tab title="热门推荐">
        <van-card
          v-for="item in GoodsList[0].content"
          :key="item.id"
          tag="hot"
          num="1"
          :price="item.price"
          desc="描述信息"
          :title="item.goodsname"
          :thumb="$preImg + item.img"
        >
          <template #tags>
            <van-tag plain type="danger">标签</van-tag>
            <van-tag plain type="danger">标签</van-tag>
          </template>
          <template #footer>
            <van-button
              type="primary"
              size="mini"
              icon="shopping-cart-o"
            ></van-button>
          </template>
        </van-card>
      </van-tab>
      <van-tab title="发现新品">
            <van-card
          v-for="item in GoodsList[1].content"
          :key="item.id"
          tag="new"
          num="1"
          :price="item.price"
          desc="描述信息"
          :title="item.goodsname"
          :thumb="$preImg + item.img"
        >
          <template #tags>
            <van-tag plain type="danger">标签</van-tag>
            <van-tag plain type="danger">标签</van-tag>
          </template>
          <template #footer>
            <van-button
              type="primary"
              size="mini"
              icon="shopping-cart-o"
            ></van-button>
          </template>
        </van-card>
      </van-tab>
      <van-tab title="全部商品">
            <van-card
          v-for="item in GoodsList[2].content"
          :key="item.id"
          num="1"
          :price="item.price"
          desc="描述信息"
          :title="item.goodsname"
          :thumb="$preImg + item.img"
        >
          <template #tags>
            <van-tag plain type="danger">标签</van-tag>
            <van-tag plain type="danger">标签</van-tag>
          </template>
          <template #footer>
            <van-button
              type="primary"
              size="mini"
              icon="shopping-cart-o"
            ></van-button>
          </template>
        </van-card>
      </van-tab>
    </van-tabs>
  </div>
</template>

<script>
import { getBanner, getIndexGoods } from "../utils/request";
export default {
  data() {
    return {
      active: 0,
      bannerList: [],
      GoodsList: [{ content: [] }, { content: [] }, { content: [] }]
    };
  },
  methods: {
    requestBanner() {
      getBanner().then(res => {
        this.bannerList = res.data.list;
      });
    },
    requestGoodsList() {
      getIndexGoods().then(res => {
        this.GoodsList = res.data.list;
      });
    }
  },
  mounted() {
    // 发起轮播图请求
    this.requestBanner();
    // 发起获取商品信息
    this.requestGoodsList();
  }
};
</script>

<style scoped>
.my-swipe .van-swipe-item img {
  width: 90%;
  padding-left: 5%;
  margin-top: 20px;
}
.van-tab__pane {
  margin-bottom: 50px;
}

</style>
