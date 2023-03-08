<template>
  <v-navigation-drawer expand-on-hover location="left" rail>
    <v-list density="compact" nav>
      <v-list-item 
        v-for="link in links" 
        :prepend-icon="link.icon" 
        :title="link.title.toUpperCase()" 
        :value="link.value"
        active-color="teal-darken-2" 
        color="white"
        variant="text"
        @click="goTo(link.route)"
      />
    </v-list>
  </v-navigation-drawer>
</template>

<script lang="ts" setup>
import { useRouter } from 'vue-router';
import { toRefs } from 'vue';

const router = useRouter();

const {links } = toRefs({
  links: [
    { icon: 'mdi:mdi-home', title: 'Home', value: 'home', route: '/'},
    { icon: 'mdi:mdi-table', title: 'Table', value: 'table', route: '/table' },
  ],
});

const goTo = (route: string) => {
  router.push(route);
}


</script>
