<script setup>
import { ref } from 'vue';
import { statuses } from '@/const/statuses';

const input = ref("");
const inputDate = ref("");

function onSubmitForm() {
    // ローカルストレージからデータを取得
  const items = JSON.parse(localStorage.getItem("items")) || []; //文字列を配列に変換
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
  localStorage.setItem("items", JSON.stringify(items)); //配列を文字列に変換
}
</script>

<template>
  <div>
    <form @submit="onSubmitForm">
      <label>やること<input type="text" v-model="input"></label>
      <label>期限<input type="date" v-model="inputDate"></label>
      <input type="submit" value="登録!">
    </form>
  </div>
</template>