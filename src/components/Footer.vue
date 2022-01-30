<template>
  <div class="footer">
    <slot />
  </div>
</template>

<style scoped>
.footer {
  color: #ffffff;
  font-weight: bold;
  height: auto;
  background-color: #4f4789;
  width: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  border-radius: 0 0 0.4rem 0.4rem;
  /* #261447 */
}
/* span {
  width: 100%;
}
span:hover {
  cursor: pointer;
  background-color: #5c5588;
  border-radius: 0 0 0.4rem 0.4rem;
} */
label {
  cursor: pointer;
  width: 100%;
}
label:hover {
  background-color: #5c5588;
}
input {
  visibility: hidden;
}
.checked {
  background-color: #261447;
}
.checked:hover {
  background-color: #261447;
  cursor: default;
}
</style>