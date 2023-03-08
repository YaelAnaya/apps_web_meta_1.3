<template>
  <v-card variant="outlined" class="mx-auto" max-width="688">
    <v-img :src="imageURL" height="400px" cover>
    </v-img>

    <v-card-title class="font-weight-bold">
      The best way to travel is by foot.
    </v-card-title>

    <v-card-subtitle>
      1,000 miles of hiking trails
    </v-card-subtitle>
   
    <v-card-actions class="py-6 px-4">
      <v-btn 
        :loading="loading"
        :disabled="loading"
        @click="load" 
        color="teal-darken-2" 
        variant="outlined" 
        rounded="35"
      >
        Reload
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts" setup>
  import { ref, toRefs } from 'vue';

  const { imageURL, loading } = toRefs({
    imageURL: ref('https://random.imagecdn.app/v1/image?width=688&height=400&category=nature'),
    loading: ref(false),
  });

  // make an async arrow function to refresh the image.
  const fetchNewImage = async () => {
    loading.value = false;
    imageURL.value = await fetch('https://random.imagecdn.app/v1/image?width=688&height=400&category=nature&format=json')
      .then((res) => res.json())
      .then((data) => data.url);
  };

  const load = () => {
    loading.value = true;
    setTimeout(() => {
      fetchNewImage();
    }, 1000);
  }

</script>

<style scoped>
  .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>