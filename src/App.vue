<template>
  <v-app>
    <Appbar />
    <v-main>
      <router-view />
    </v-main>
    <v-footer app>
      <v-container>
        <v-row>
          <v-col class="text-center">
            <span>take</span>
          </v-col>
          <v-divider />
          <v-col class="text-center ">
            <span>&copy; 2025</span>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script lang="ts" setup>
import Appbar from './components/Appbar.vue'
</script>
