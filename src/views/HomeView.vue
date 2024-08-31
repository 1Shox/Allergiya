<template>
  <div>
    <section class="banner">
      <Swiper
        :modules="modules1"
        :pagination="pagination"
        :loop="true"
        :autoplay="{
          delay: 3000, // 3 soniya kutadi
          disableOnInteraction: false, // foydalanuvchi slider bilan o'zaro ta'sir qilganda ham davom etadi
        }"
      >
        <!-- Slaydlar -->
        <SwiperSlide v-for="(image, index) in bannerImages" :key="index">
          <div class="banner__item relative">
            <div class="banner__img absolute top-0 left-0">
              <img :src="image" alt="" />
            </div>
            <div class="banner__info absolute">
              <h1 class="text-[40px] uppercase">
                <span class="block text-[20px]">бренд</span>
                american vintage
              </h1>
              <router-link to="./collection/collection.vue">{{
                $t("collection")
              }}</router-link>
            </div>
          </div>
        </SwiperSlide>
      </Swiper>
    </section>

    <section class="ads bg-grey">
      <div class="container flex justify-between items-center">
        <div
          class="ads__left flex flex-col gap-5 justify-center p-[50px] text-white"
        >
          <h1 class="text-[90px]">
            <span class="block">new </span>
            arrival
          </h1>
          <p>
            Lorem ipsumLorem ipsumLorem ipsumLorem ipsumLorem ipLorem ipsumLorem
            ipLorem ipsumLorem ipsumLorem ipsumLorem ipsumLorem ipLorem
            ipsumLorem ip
          </p>
          <router-link to="./collection/collection.vue">{{
            $t("collection")
          }}</router-link>
        </div>
        <div class="ads__right relative">
          <div class="flex items-end p-[35px]">
            <img
              class="absolute z-10"
              src="../assets/images/person.png"
              alt=""
            />
            <p class="text-center z-40 text-white">
              Lorem ipsumLorem ipsumLorem ipsumLorem ipsumLorem ipLorem
              ipsumLorem ip
            </p>
          </div>
        </div>
      </div>
    </section>
    <section class="products py-[120px]">
      <div class="container">
        <h1 class="products__title text-center mb-12 text-[48px]">
          Популярное
        </h1>
        <div class="swiper2-container">
          <swiper
            :slidesPerView="4"
            :spaceBetween="30"
            :navigation="true"
            :modules="modules2"
            :breakpoints="breakpoint"
            class="mySwiper"
          >
            <swiper-slide v-for="item in productItem" :key="item.id"
              ><ProductCom :item="item"></ProductCom
            ></swiper-slide>
          </swiper>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import ProductCom from '@/components/ProductCom.vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import { onMounted, ref } from 'vue'
import axios from 'axios'
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
const modules1 = [Pagination, Autoplay];
const modules2 = [Navigation];
const pagination = {
  clickable: true,
  renderBullet: function (index, className) {
    return `<span class="${className}">0${index + 1}</span>`;
  },
};
const  bannerImages = [
        '/images/banner-img1.png',
        '/images/banner-img2.png',
        '/images/banner-img3.png'
      ]

const breakpoint = {
  500:{
    slidesPerView: 1,
    spaceBetween: 30
  },
  640:{
    slidesPerView: 2,
    spaceBetween: 30
  },
  768:{
    slidesPerView: 3,
    spaceBetween: 30
  },
  1024:{
    slidesPerView: 4,
    spaceBetween: 30
  }
}

const productItem = ref([])
const getProducts = async () => {
  const { data } = await axios.get('http://localhost:3000/products')
  productItem.value = data
  console.log(data[0]);
}

onMounted(() => {
  getProducts()
})
</script>

<style lang="scss" scoped>
/* Add any necessary styles here */
</style>
