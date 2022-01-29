<template>
  <div class="frame">
    <slot />
  </div>
</template>

<style scoped>
.frame {
  width: 75%;
  border: solid;
  border-width: 1px;
  border-radius: 0.5rem;
  border-color: #4f4789;
  justify-content: space-around;
  font-size: 1.2rem;
}
</style>