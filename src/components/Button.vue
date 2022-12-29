<template>
  <button :style="{ background: bgColor, color: color }">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",

  props: {
    text: String,
    bgColor: String,
    color: String,
  },
};
</script>
