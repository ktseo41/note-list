<script setup>
import { toRefs } from "vue";
// todolist todo에서 소수번째 글자는 음표 중 하나로 변경한다.
const props = defineProps({
  todos: {
    type: Array,
    default: () => [],
  },
});

const { todos } = toRefs(props);

// check if input number is prime number, with memoization
const memo = {};

function isPrimeNumber(n) {
  if (n < 2) return false;
  if (n === 2) return true;
  if (n % 2 === 0) return false;
  if (memo[n]) return memo[n];
  for (let i = 3; i * i <= n; i += 2) {
    if (n % i === 0) {
      memo[n] = false;
      return false;
    }
  }
  memo[n] = true;
  return true;
}

// 문자열에서 소수번째에 있는 문자는 음표를 붙인다
const notes = ["♪", "♪", "♫", "♬", "🎵", "🎶"];
function trunIntoNote(string) {
  return string
    .split("")
    .map((char, index) => {
      if (isPrimeNumber(index + 1)) {
        return `${char}${
          notes[Math.round(Math.random() * (notes.length - 1))]
        }`;
      }

      return char;
    })
    .join("");
}
</script>
<template>
  <ul>
    <li :key="`${todo}-${index}`" v-for="(todo, index) in todos">
      {{ trunIntoNote(todo) }}
    </li>
  </ul>
</template>

<script>
export default {};
</script>

<style></style>
