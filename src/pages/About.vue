<template>
  <HeaderParallax :imageSrc="Myoko" text="ABOUT" />
  <v-container class="my-12">
    <v-row>
      <v-col>
        <h1>About</h1>
        <v-divider :thickness="5" />
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <p>このサイトは、Vue.js 3 と Vuetify 3 を使用して作成したサンプルサイトです。</p>
        <p>GitHub リポジトリ一覧を表示しています。</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
import HeaderParallax from '../components/HeaderParallax.vue';
import Myoko from '@/assets/Myoko.png';
import AboutTwitter from '../components/AboutTwitter.vue';
</script>
