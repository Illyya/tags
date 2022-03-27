<template>
  <v-app>
    <AppTags
      v-for="(tags, index) in tagsList"
      :key="index"
      :tags="tags"
      :isTagsWidth="false"
    />
  </v-app>
</template>

<script>
import AppTags from '@/components/AppTags';

const tagsList = [
  [
    { title: '5', icon: 'mdi-call-split' },
    { title: 'Обзорная', icon: null },
    { title: '28 марта', icon: 'mdi-domain' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
  ],
  [
    { title: '5', icon: 'mdi-call-split' },
    { title: 'Обзорная', icon: null },
    { title: '28 марта', icon: 'mdi-domain' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
  ],
  [
    { title: '5', icon: 'mdi-call-split' },
    { title: 'Обзорная', icon: null },
    { title: '28 марта', icon: 'mdi-domain' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
    { title: '6 часов', icon: 'mdi-call-split' },
  ],
];

export default {
  name: 'App',

  components: {
    AppTags,
  },

  data() {
    return {
      tagsList
    }
  },
};
</script>

<style lang="scss">
/*Сброс стилей*/
* {
	padding: 0;
	margin: 0;
	border: 0;
}

ul {
  li {
    list-style: none;
  }
}
/*--------------------*/
</style>