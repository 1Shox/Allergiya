<template>
      <div class="nav bg-white boder-b-2 py-5">
         <div class="container flex justify-between items-center">
            <router-link to="/" class="logo">
                  <img width="130" height="16" src="../assets/images/logo.svg" alt="">
            </router-link>
            <div class="nav__menu flex items-center gap-11 ml-20">
                  <router-link to="/" class="text-secondary">{{ $t('women') }}</router-link>
                  <router-link to="/about" class="text-secondary">{{ $t('men') }}</router-link>
                  <div class="nav__search flex items-center gap-5">
                        <label for="" class="text-secondary">{{ $t('search') }}</label>
                        <input type="text">
                  </div>
            </div>
            <div class="nav__right flex items-center gap-[57px]">
                  <ul class="nav__langs flex items-center gap-4">
                        <li @click="$i18n.locale = 'ru', lang ='ru'" :class="{active: lang === 'ru'}">Ru</li>
                        <li @click="$i18n.locale = 'uz', lang ='uz'" :class="{active: lang === 'uz'}">Uz</li>
                        <li @click="$i18n.locale = 'en', lang ='en'" :class="{active: lang === 'en'}">En</li>
                  </ul>
                  <div class="nav__icons flex items-center gap-5"> 
                        <router-link to="/personal-account">
                              <UserIconVue />
                        </router-link>
                        <router-link to="/wishlist">
                              <WishlistIconVue />
                        </router-link>
                        <router-link to="/cart">
                              <CartIconVue />
                        </router-link>
                  </div>
            </div>
         </div>
      </div>
</template>

<style lang="scss" scoped>

</style>

 <script setup >
 import { ref } from "vue";
 import UserIconVue from "../components/icons/UserIcon.vue";
import WishlistIconVue from "../components/icons/WishlistIcon.vue";
import CartIconVue from "../components/icons/CartIcon.vue";

let lang = ref("ru");
 </script>