<script setup>
import { ref } from 'vue';
import { statuses } from '@/const/statuses';

const input = ref("");
const inputDate = ref("");

function onSubmitForm() {
  // ローカルストレージからデータを取得
  const items = JSON.parse(localStorage.getItem("items")) || [];

  // 保存するタスクのオブジェクトを作成
  const newItem = {
    id: items.length,
    content: input.value,
    limit: inputDate.value,
    state: statuses.NOT_START,
    onEdit: false,
  };

  // 取得したデータに新しいデータをpush
  items.push(newItem);

  // 配列をローカルストレージに保存
  localStorage.setItem("items", JSON.stringify(items));

  // フォームをクリア
  input.value = "";
  inputDate.value = "";
}
</script>

<template>
  <div>
    <form @submit.prevent="onSubmitForm">
      <label>やること<input type="text" v-model="input"></label>
      <label>期限<input type="date" v-model="inputDate"></label>
      <input type="submit" value="登録!">
    </form>
  </div>
</template>
