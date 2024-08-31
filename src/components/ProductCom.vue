<template>
  <div class="product" v-if="item">
    <div class="product__img">
      <router-link :to="{ name: 'about-product', params: { id: item.id } }">
        <img :src="item.img" alt="product-img" />
      </router-link>
      <div class="discount text-white bg-tomato">{{ item.discount }}</div>
      <div class="wishlist-btn bg-white" @click="addToWishlist">
        <svg
          width="21"
          height="18"
          viewBox="0 0 21 18"
          :fill="fill ? 'crimson' : 'none'"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M2.31802 2.31802C4.07538 0.56066 6.92462 0.56066 8.68198 2.31802L10.5 4.13604L12.318 2.31802C14.0754 0.56066 16.9246 0.56066 18.682 2.31802C20.4393 4.07538 20.4393 6.92462 18.682 8.68198L10.5 16.864L2.31802 8.68198C0.56066 6.92462 0.56066 4.07538 2.31802 2.31802Z"
            :stroke="stroke ? 'crimson' : '#0F303F'"
            stroke-linecap="round"
          />
        </svg>
      </div>
    </div>
    <div class="product__info">
      <div class="title">{{ item.title }}</div>
      <div class="category">{{ item.name }}</div>
      <div class="price">
        <div class="old-price">{{ item.price.oldPrice }}</div>
        <div class="new-price">{{ item.price.newPrice }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const props = defineProps(["item"]);

let fill = ref(false);
let stroke = ref(false);
function addToWishlist() {
  fill.value = !fill.value;
  stroke.value = !stroke.value;
}
</script>

<style lang="scss" scoped>
.product {
  &__img {
    position: relative;
    width: 100%;
    height: 325px;
    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .discount {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 45px;
      height: 45px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      font-weight: 700;
      font-size: 14px;
      line-height: 17px;
    }

    .wishlist-btn {
      position: absolute;
      bottom: 10px;
      right: 10px;
      width: 45px;
      height: 45px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      cursor: pointer;
    }
  }

  &__info {
    text-align: center;
    .title {
      font-weight: 700;
      font-size: 18px;
      line-height: 22px;
      margin-top: 20px;
      color: #0f303f;
    }

    .category {
      font-weight: 400;
      font-size: 14px;
      line-height: 17px;
      color: #0f303f;
      opacity: 0.5;
      margin: 20px 0;
    }

    .price {
      display: flex;
      justify-content: center !important;
      align-items: center;
      gap: 3.5px;
      text-align: center;
      height: 20px;
      .old-price {
        text-decoration-line: line-through;
        color: #0f303f;
        width: 60px;
        height: 20px;
        font-family: Jost;
        font-size: 14px;
        font-weight: 500;
      }

      .new-price {
        font-weight: 700;
        color: #0f303f;
        width: 60px;
        height: 20px;
        font-family: Jost;
        font-size: 14px;
        letter-spacing: 0.045em;
        color: var(--tomato-color);
      }
    }
  }
}
</style>