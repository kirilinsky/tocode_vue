<template>
  <div class="message">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
      default: "",
    },
  },
};
</script>

<style lang="scss" scoped>
    .message{
        color:#900;
        text-shadow: 0 0 2px #900, 0 0 4px #fff;
    }
</style>
