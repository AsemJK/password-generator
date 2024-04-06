<script setup lang="ts">
import { ref } from "vue";

const generatedPassword = ref<string>("");
const hasUpperCase = ref<boolean>(false);
const hasNumbers = ref<boolean>(false);
const hasSymbols = ref<boolean>(false);
const passwordLength = ref<number>(12);

const lowerChars = ref("abcdefghijklmnopqrstuvwxyz");
const allUpperCase = ref("ABCDEFGHIJKLMNOPQRSTUVWXYZ");
const allNumbers = ref("0123456789");
const allSymbols = ref("!@#$%^&*()_+");
const all = ref("");

const generatePassword = () => {
  all.value = lowerChars.value;
  if (hasUpperCase.value) all.value += allUpperCase.value;
  if (hasNumbers.value) all.value += allNumbers.value;
  if (hasSymbols.value) all.value += allSymbols.value;

  let password = "";
  for (let i = 0; i < passwordLength.value; i++) {
    password += all.value.charAt(Math.floor(Math.random() * all.value.length));
  }
  generatedPassword.value = password;
};

const copyPassword = () => {
  navigator.clipboard.writeText(generatedPassword.value);
};

const resetPassword = () => {
  generatedPassword.value = "";
};
</script>

<template>
  <div>
    <a href="https://asemcode.dev" target="_blank">
      <img src="/logo.png" class="logo" alt="Asem logo" />
    </a>
    <div class="main">
      <div id="div2">
        <label for="hasUpperCase">Has Upper Case</label>
        <input type="checkbox" id="hasUpperCase" v-model="hasUpperCase" />
      </div>

      <div id="div2">
        <label for="hasNumbers">Has Numbers</label>
        <input type="checkbox" id="hasNumbers" v-model="hasNumbers" />
      </div>
      <div id="div3">
        <label for="hasSymbols">Has Symbols</label>
        <input type="checkbox" id="hasSymbols" v-model="hasSymbols" />
      </div>
      <div id="div4">
        <label for="passwordLength">Password Length</label>
        <input
          type="number"
          id="passwordLength"
          v-model="passwordLength"
          min="4"
          max="32"
        />
      </div>
      <div id="div5">
        <button @click="generatePassword">Generate</button>
        <br />
        <p>{{ generatedPassword }}</p>
        <br />
        <a
          href="#"
          v-if="generatedPassword"
          @click="copyPassword"
          class="actionButton"
          >Copy</a
        >
        <a
          href="#"
          v-if="generatedPassword"
          @click="resetPassword"
          class="actionButton"
          >Reset</a
        >
      </div>
    </div>
  </div>
</template>

<style scoped>
.main {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(5, 6em);
  grid-column-gap: 0px;
  grid-row-gap: 10px;
}
.main div {
  display: flex;
  margin: 0.1em;
  justify-content: center;
  align-items: center;
  font-size: 1.5em;
  padding: 1em;
  border: 0.2em solid #000;
  border-radius: 0.5em;
  background-color: #f0f0f0;
  box-shadow: 0 0 1em #00000022;
  transition: box-shadow 300ms;
}
.main div1 {
  grid-area: 1 / 1 / 1 / 2;
}
.main div2 {
  grid-area: 1 / 2 / 1 / 2;
}
.main div3 {
  grid-area: 1 / 3 / 1 / 3;
}
#div4 {
  grid-area: 2 / 1 / 2 / 4;
}
#div5 {
  display: flex;
  flex-direction: column;

  grid-area: 3 / 1 / 7 / 4;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

input[type="checkbox"] {
  width: 2em;
  height: 2em;
  margin: 0.5em;
}
input[type="number"] {
  width: 4em;
  height: 2em;
  margin: 0.5em;
  border: #f0f0f0 0.2em solid;
  border-radius: 0.5em;
}
button {
  width: 6em;
  height: 3em;
  margin: 0.5em;
  border: #f0f0f0 0.2em solid;
  border-radius: 0.5em;
  background-color: #f0f0f0;
  box-shadow: 0 0 1em #00000022;
  transition: box-shadow 300ms;
}
.actionButton {
  width: 6em;
  height: 2em;
  margin: 0.5em;
  border: #f0f0f0 0.2em solid;
  border-radius: 0.5em;
  background-color: #f0f0f0;
  box-shadow: 0 0 1em #00000022;
  transition: box-shadow 300ms;
}
</style>
style
