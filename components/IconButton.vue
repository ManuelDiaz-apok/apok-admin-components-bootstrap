<template>
  <b-button
    :class="[materialIcon && 'd-inline-flex align-items-center']"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <slot name="icon">
      <icon
        v-if="icon && !right"
        :material-icon="materialIcon"
        :icon="icon"
        :class="[materialIcon && 'md-18']"
      ></icon>
    </slot>
    <span class="mx-2" v-if="hasContent">
      <slot></slot>
    </span>
    <slot name="right-icon">
      <icon
        v-if="icon && right"
        :material-icon="materialIcon"
        :icon="icon"
        :class="[materialIcon && 'md-18']"
      ></icon>
    </slot>
  </b-button>
</template>

<script>
  import Icon from './Icon';

  export default {
    name: 'IconButton',
    components: { Icon },
    props: {
      iconOnly: {
        type: Boolean,
        default: false,
      },
      right: Boolean,
      icon: {
        type: String,
        default: null,
      },
      materialIcon: Boolean,
    },
    computed: {
      hasContent() {
        return this.$slots && this.$slots.default && this.$slots.default.length && this.$slots.default[0].text
      }
    }
  };
</script>

<style scoped>
</style>
