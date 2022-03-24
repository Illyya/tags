<template>
  <ul class="tags">
    <li
      v-for="(tag, index) in tags"
      :key="index"
      ref="tags"
      class="tags__tag"
    >
      <v-icon
        large
        color="purple darken-2"
      >
        {{ tag.iconTitle }}
      </v-icon>

      4.3

      <v-icon
        small
        color="blue"
      >
        mdi-circle-medium
      </v-icon>

      {{ tag.title }}

      <v-icon
        small
        color="blue"
      >
        mdi-circle-medium
      </v-icon>

      1,2 км от вас
    </li>
  </ul>
</template>

<script>
export default {
  name: 'AppTags',

  props: {
    tags: {
      type: Array,
      required: true
    },
  },

  created() {
    window.addEventListener('resize', this.checkWidthTag);
  },

  beforeDestroy() {
    window.removeEventListener('resize', this.checkWidthTag);
  },

  methods: {
    checkWidthTag() {
      this.$refs.tags.forEach((el) => {
        const widthEl = parseInt(getComputedStyle(el).width);
        const widthWin = document.documentElement.clientWidth;

        if (widthWin <= widthEl) {
          el.style.height = '0';
          el.style.opacity = '0';
        } else {
          el.style.height = '100%';
          el.style.opacity = '1';
        }
      })
    }
  }
}
</script>

<style lang="scss">
.tags {
  display: flex;
  flex-direction: column;

  &__tag {
    align-self: flex-start;
    white-space: nowrap;
    transition: .1s ease;
  }
}
</style>
