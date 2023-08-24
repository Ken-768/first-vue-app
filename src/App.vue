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
  //繰り返し処理

  const clickButton = (event) => {
    console.log(event.target);
    event.target.style.backgroundColor = 'red';
  }
  const another = (msg) => {
    console.log(msg);
  }
  const send = () => {
    console.log('send');
  };
  //イベント

  import { reactive, computed } from 'vue';
  const state = reactive({
    count: 0,
  });
  const addCount = () => {
    state.count++;
    console.log(state.count)
  };

  import { ref } from 'vue';
  const state2 = ref({
    count: 0,
  });
  const addCount2 = () => {
    state2.value.count++;
  };
  //reactivity

  const message2 = ref('Hello World');

  const clickButton2 = () => {
    console.log(message2.value);
  };

  const form = reactive({
    message: 'Hello World',
  });

  const clickButton3 = () => {
    console.log(form.message);
  };
  //form

  const user2 = reactive({
    firstName: 'John',
    lastName: 'Doe'
  })

  const fullName = computed(() => `${user2.firstName} ${user2.lastName}`);
  const users3 = [
    { id: 1, name: 'John Doe', email: 'john@test.com', admin: true },
    { id: 2, name: 'Jane Doe', email: 'jane@example.com', admin: false },
    { id: 3, name: 'Kevin MacDonald', email: 'kevin@test.com', admin: false },
  ];
  const adminUsers = computed(() =>
    users3.filter((user) => user.admin === true)
  );
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
  <!-- 繰り返し処理 -->

  <button @click="clickButton($event), another('click')">クリック</button>
  <form @submit.prevent="send">
    <button @keyup.enter>送信</button>
  </form>
  <!-- イベント -->

  <button type="button" @click="addCount">
    count is:{{ state.count }}
  </button>
  <button type="button" @click="addCount2">count is: {{ state2.count }}</button>
  <!-- reactivity -->

  <p>{{ message2 }}</p>
  <input v-model="message2" />
  <div><button @click="clickButton2">Click</button></div>

  <p>{{ form.message }}</p>
  <input v-model.trim="form.message" />
  <div><button @click="clickButton3">Click</button></div>
  <!-- form -->

  <h2>fullName: {{ fullName }}</h2>
  <div v-for="user in adminUsers" :key="user.id">
    <div>{{ user.id }} {{ user.name }} {{ user.email }}</div>
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
