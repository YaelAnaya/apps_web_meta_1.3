<template>
    <v-card
    class="mx-auto"
    max-width="900"
    variant="text"
    title="JSON Placeholder Table Viewer"
    >
    <v-card-item>
      <v-table
            fixed-header
            height="600"
          >
            <thead>
              <tr>
                <th v-for="header in headers" :key="header">
                  {{ header }}
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="author in authors" :key="author.id">
                <td>{{ author.name }}</td>
                <td>{{ getPost(author.id).title }}</td>
                <td>{{ getPost(author.id).body }}</td>
              </tr>
            </tbody>
          </v-table>
    </v-card-item>
    </v-card>
</template>

<script lang="ts" setup>

import { ref, toRefs, onMounted } from 'vue';

type Post = {
  userId: number;
  id: number;
  title: string;
  body: string;
};

type User = {
  id: number;
  name: string;
};

const fetchData = async () => {

  authors.value = await fetch ('https://jsonplaceholder.typicode.com/users')
    .then((response) => response.json())
    .then((json) => json);

  posts.value = await fetch('https://jsonplaceholder.typicode.com/posts')
    .then((response) => response.json())
    .then((json) => json);
  
}

const getPostMap = () => {
  return posts.value.reduce((map:any, post:any) => {
    map[post.id] = post;
    return map;
  }, {});
};

const getPost = (userId: number) => {
  const postMap = getPostMap();
  return postMap[userId];
}


const { headers, authors, posts } = toRefs({
  headers: ['Author', 'Title','Post'],
  authors: ref<User[]>([]),
  posts: ref<Post[]>([]),
});

onMounted(async () => {
  await fetchData();
});

</script>