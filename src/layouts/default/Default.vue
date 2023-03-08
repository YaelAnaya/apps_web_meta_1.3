<template>
  <v-app>
    <v-responsive class="d-flex align-center fill-height">
      <v-content>
        <DefaultBar />
        <v-row class="d-flex align-center justify-center">
          <v-col cols="auto">
            <DefaultSideBar />
          </v-col>
          <v-col cols="center">
            <DefaultView />
          </v-col>
        </v-row>
      </v-content>
    </v-responsive>

  </v-app>
</template>

<script lang="ts" setup>
import DefaultBar from './AppBar.vue'
import DefaultView from './View.vue'
import DefaultSideBar from '@/layouts/default/SideBar.vue'
</script>
