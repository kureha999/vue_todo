<script setup>
// ローカルストレージからデータを取得
let items = ref(JSON.parse(localStorage.getItem('items')) || []); //文字列を配列に変換
let inputContent = ref();
let inputLimit = ref();
let inputState = ref();

import { statuses } from '@/const/statuses'
import { ref } from 'vue';

function onEdit(id) {
  items.value[id].onEdit = true;
}

function onUpdate(id) {
  id: id,
  content: inputContent.value,
  limit: inputLimit.value,
  state: inputState.value,
  onEdit: false,
};

items.value.splice(id, 1, newItem);
</script>

<template>
  <div>
    <table v-if="items.length > 0">
      <thead>
        <tr>
          <th>ID</th>
          <th>やること</th>
          <th>期限</th>
          <th>状態</th>
          <th>編集</th>
          <th>削除</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{ item.id }}</td>
          <td>
            <span v-if="!item.onEdit">{{ item.content }}</span>
            <input v-else v-model="inputContent" type="text" />
          </td>
          <td>
            <span v-if="!item.onEdit">{{ item.limit }}</span>
            <input v-else v-model="inputLimit" type="date" />
          </td>
          <td>
            <span v-if="!item.onEdit">{{ item.state.value }}</span>
            <select v-else v-model="inputState">
              <option
                v-for="state in statuses"
                :key="state.id"
                :value="state"
                :selected="state.id == item.state.id"
              >
                {{ state.value }}
              </option>
            </select>
          </td>
          <td>
            <button @click="onEdit(item.id)">編集</button>
            <button v-else @click="onUpdate(item.id)">完了</button>
          </td>
          <td><button>削除</button></td>
        </tr>
      </tbody>
    </table>
    <p v-else>やることがありません。</p>
  </div>
</template>
