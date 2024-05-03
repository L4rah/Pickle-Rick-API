<template>
  <div class="item">
    <i>
      <slot name="icon"></slot>
    </i>
    <div class="details">
      <h3>
        <slot name="heading"></slot>
      </h3>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Component'
}
</script>

<style src="./ComponentStyles.css" scoped></style>
