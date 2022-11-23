<script setup>
import MoldStock from './components/moldstock.vue';
import { ref } from 'vue';

// var moldBlock = ref(1);
// var moldBlockName = '內製區';

var moldBlocks = [
  { index: 0, moldBlock: 1, moldBlockName: '內製區' },
  { index: 1, moldBlock: 2, moldBlockName: '墊片區' },
];
var currentBlock = ref(1);

function changeMoldBlock(addorminus) {
  if (addorminus == 'add') {
    currentBlock.value++;
    //如果目前頁面>區域數量,則目前頁面回到第一頁
    if (currentBlock.value >= moldBlocks.length) {
      currentBlock.value = 0;
    }
  } else {
    currentBlock.value--;
    if (currentBlock.value < 0) {
      currentBlock.value = moldBlocks.length - 1;
    }
  }
}
</script>

<template>
  <div class="container">
    <header class="row">
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="270" />
      <div class="row">
        <button @click="changeMoldBlock('minus')">
          <img src="./assets/leftArrow.svg" alt="" width="15" />
        </button>
        <div class="moldBlock">
          所在區域 :{{ moldBlocks[currentBlock].moldBlockName }}
        </div>
        <button @click="changeMoldBlock('add')">
          <img src="./assets/rightArrow.svg" alt="" width="15" />
        </button>
      </div>
    </header>

    <main class="row justifycontent_center">
      <div>
        <div class="blockUnits row">
          <MoldStock id="1" />
          <MoldStock id="2" />
        </div>
        <div class="blockUnits row">
          <MoldStock id="3" />
          <MoldStock id="4" />
        </div>
      </div>
      <div>
        <div class="blockUnits row">
          <MoldStock id="5" />
          <MoldStock id="6" />
        </div>
        <div class="blockUnits row">
          <MoldStock id="7" />
          <MoldStock id="8" />
        </div>
      </div>
      <div>
        <div class="blockUnits row">
          <MoldStock id="9" />
          <MoldStock id="10" />
        </div>
        <div class="blockUnits row">
          <MoldStock id="11" />
          <MoldStock id="12" />
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

header > div {
  margin: 0 auto;
}
.logo {
  /* display: block; */
  /* margin: 0 auto 2rem; */
  /* position: absolute; */
  /* top: 0px; */
  /* left: 2rem; */
}

.container {
  padding: 0 auto;
  margin: 0 auto;
}

.moldBlock {
  background: #3e3a39;
  color: var(--vt-c-white-soft);
  border-radius: 8px;
  margin: 0px 10px;
  padding: 10px 50px;
}
main {
  margin: 1rem 0 auto;
}
button {
  background: none;
  border: none;
}

.blockUnits {
  background: no-repeat url(./assets/blockUnits.svg);
  background-position: bottom;
  margin-top: 0.5rem;
  margin-right: 0.5rem;
  padding-bottom: 1rem;
}
</style>
