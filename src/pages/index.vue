<template>
  <HeaderParallax :imageSrc="Yamato" text="TOP" />
  <v-container class="my-12">
    <v-row>
      <v-col>
        <h1>Github Repositories</h1>
        <v-divider :thickness="5" />
      </v-col>
    </v-row>
    <!-- GitHubリポジトリ一覧 -->
    <v-row v-if="loading">
      <v-col class="text-center">
        <p>Loading...</p>
      </v-col>
    </v-row>
    <v-row v-else-if="error">
      <v-col class="text-center">
        <p>Error: {{ error }}</p>
      </v-col>
    </v-row>
    <v-row v-else>
      <v-col cols="12" md="6" v-for="repo in repos" :key="repo.id">
        <v-card class="mb-4" :href="repo.html_url" target="_blank">
          <v-card-title>{{ repo.name }}</v-card-title>
          <v-divider />
          <v-card-text>
            <p>{{ repo.description }}</p>
            <p><strong>Language:</strong> {{ repo.language }}</p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import HeaderParallax from '@/components/HeaderParallax.vue';
import Yamato from '@/assets/Yamato.png';

const repos = ref<any[]>([]);
const loading = ref<boolean>(false);
const error = ref<string>('');

// GitHub APIからリポジトリ一覧を取得（例: "take5054" ユーザー）
onMounted(async () => {
  loading.value = true;
  try {
    const res = await fetch('https://api.github.com/users/take5054/repos');
    if (!res.ok) throw new Error(`HTTP error! status: ${res.status}`);
    repos.value = await res.json();
  } catch (err: any) {
    error.value = err.message;
  } finally {
    loading.value = false;
  }
});
</script>
