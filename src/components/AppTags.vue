<template>
  <ul :class="{ 'tags--width': isTagsWidth }" class="tags">
    <li
      v-for="(tag, index) in tags"
      :key="index"
      ref="tags"
      class="tags__tag"
    >
      <v-icon
        v-if="index !== 0"
        small
        color="purple darken-2"
        class="separator"
      >
        mdi-circle-small
      </v-icon>

      <v-icon
        small
        color="purple darken-2"
      >
        {{ tag.icon }}
      </v-icon>

      {{ tag.title }}
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
    isTagsWidth: {
      type: Boolean,
      required: true
    }
  },

  created() {
    window.addEventListener('resize', this.checkWidthTag);
  },

  mounted () {
    this.checkWidthTag();
  },

  beforeDestroy() {
    window.removeEventListener('resize', this.checkWidthTag);
  },

  methods: {
    checkWidthTag() {
      this.$refs.tags.forEach((el) => {
        if (this.isTagsWidth) {
          this.$nextTick(() => {
            if (el.previousElementSibling) {
              const leftEl = parseInt(el.getBoundingClientRect().left);
              const rightElPrev = parseInt(el.previousElementSibling.getBoundingClientRect().right);
              const separator = el.querySelector('.separator');

              const distance = (leftEl - rightElPrev) / 2;

              separator.style.left = '-' + distance + 'px';
            }
          })
        }

        const rightEl = parseInt(el.getBoundingClientRect().right);
        const widthWin = document.documentElement.clientWidth;

        if (widthWin <= rightEl - 3) {
          el.style.height = '0';
          el.style.opacity = '0';
        } else {
          el.style.height = '100%';
          el.style.opacity = '1';
        }
      })
    },
  }
}
</script>

<style lang="scss">
.tags {
  display: inline-flex;
  align-items: baseline;

  &--width {
    justify-content: space-between;
  }

  &__tag {
    position: relative;
    white-space: nowrap;

    &:not(&:last-of-type) {
      margin-right: 20px;
    }

    &:first-of-type::before {
      content: none;
    }
  }
}

.separator {
  left: -10px;
}
</style>
