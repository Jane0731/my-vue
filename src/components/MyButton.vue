<template>
  <button @click="my-event">請戳我</button>
</template>

<script>
export default {
  emits: ["my-event"],
};
</script>

<style>
</style>