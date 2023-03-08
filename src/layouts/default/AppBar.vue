<template>
  <v-app-bar 
  density="compact"
  border
  >
    <v-app-bar-title
      class="d-flex flex-col align-center justify-center"
      style="font-size: 1.2rem"
    >
      <v-icon icon="fa:fa-solid fa-droplet" size="xs-small"/>
        S O U L M A T E
    </v-app-bar-title>
    <slot name="side-bar" />
  </v-app-bar>
</template>

<script lang="ts" setup>
  //
</script>
