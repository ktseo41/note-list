<script setup>
import NoteList from "./NoteList.vue";
</script>
<template>
  <NoteList
    :todos="['할 일이 산더미 인데', '오늘도 집에는 10시에 가자']"
  ></NoteList>
</template>

<script>
export default {};
</script>

<style></style>
