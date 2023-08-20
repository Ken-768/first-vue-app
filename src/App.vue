<script setup>
  let message = 'Hello World';

  const upperCase = () => {
    message = message.toUpperCase();
  }
  upperCase();

  let link = 'https://google.com';

  const isActive = true;
  const isBlack = true;
  // v-bind

  const error = '';
  const stock = 0;
  const error2 = false;
  // 条件分岐

  const languages = ['JavaScript', 'TypeScript', 'Vue.js', 'React', 'Node.js', 'Flutter'];
  const users = [
    { id: 1, name: 'John Doe', email: 'john@test.com', admin: true },
    { id: 2, name: 'Jane Doe', email: 'jane@example.com', admin: false },
    { id: 3, name: 'Kevin MacDonald', email: 'kevin@test.com', admin: false },
  ]
</script>

<template>
  <h1>Vue 3 入門</h1>
  <p>{{ message.length > 10 ? 'Long' : 'Short' }}</p>
  <p v-text="message"></p>
  <div>
    <a v-bind:href="link">Google</a>
  </div>
  <p class="active">v-bindの設定方法の確認</p>
  <p class="underLine" :class="{ active: isActive, back: isBlack }">v-bindの設定方法の確認-1</p>
  <p :class="isActive ? 'active back' : 'underline'">v-bindの設定方法の確認-2</p>
  <!-- v-bind -->

  <div v-if="error">{{ error }}</div>
  <div v-else="error">エラーはありません。</div>

  <div v-if="stock > 5">在庫があります</div>
  <div v-else-if="stock === 0">売り切れです</div>
  <div v-else>在庫が少ないです</div>

  <div v-if="error2">エラーが発生しています。(v-if)</div>
  <div v-show="error2">エラーが発生しています。(v-show)</div>
  <!-- 条件分岐 -->

  <p v-for="language in languages" :key="language">{{ language }}</p>
  <div v-for="user in users" :key="user.id">
    <div v-for="(value, name) in user" :key="value">
      {{ name }}: {{ value }}
    </div>
  </div>
</template>

<style scoped>
.active {
    color: red;
    font-weight: 900;
  }
.underLine {
  text-decoration: underline;
}
.back {
  background-color: black;
}
</style>
