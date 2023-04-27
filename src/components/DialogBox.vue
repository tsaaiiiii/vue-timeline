<template>
  <div>
    <div class="dialog-content">
      <slot name="DialogText"> </slot>
      <slot name="DialogButton"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ['status']
}
</script>

<style scoped></style>
