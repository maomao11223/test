<script setup>
import axios from 'axios';
import MoldStock from './components/moldstock.vue';
import { reactive, ref, onMounted } from 'vue';

var moldBlocks = reactive([
  { moldBlock: 1, moldBlockName: '內製區' },
  { moldBlock: 2, moldBlockName: '墊片區' },
]);

var currentBlock = ref(1);

var moldBlockNo = reactive([][4]);

var datas = [{ ID: 1, MoldStockID: 'mold01' }];
var MoldStockID = ref(12);
var ID = ref(1);

//測試用
// var Payload = [
//   {
//     ID: 17,
//     MoldStockID: 'mold01',
//   },
//   {
//     ID: 16,
//     MoldStockID: 'mold03',
//   },
//   {
//     ID: 3,
//     MoldStockID: 'mold02',
//   },
//   {
//     ID: 5,
//     MoldStockID: 'mold15',
//   },
//   {
//     ID: 8,
//     MoldStockID: 'mold10',
//   },
// ];

const url = 'http://localhost:3000/data';

//更改所在區域
function changeMoldBlock(addorminus) {
  if (addorminus == 'add') {
    currentBlock.value++;
    console.log('currentBlock: ' + currentBlock.value);
    //如果目前頁面>區域數量,則目前頁面回到第一頁
    if (currentBlock.value > moldBlocks.length - 1) {
      currentBlock.value = 0;
    }
  } else {
    currentBlock.value--;
    if (currentBlock.value < 0) {
      currentBlock.value = moldBlocks.length - 1;
    }
  }
  //正式用
  moldBlockNo = [];
  getMoldBlockData();
}

//正式用
//取得所在區域的模具架資料
function getMoldBlockData() {
  axios
    .post(url, {
      MoldBlock: currentBlock.value + 1,
      ModelID: '',
      ModelName: '',
      MoldStockID: '',
      PageSize: 10,
      CurrentPage: 1,
      // Payload,
    })
    .then((response) => {
      datas = response.data.Payload;

      //測試排序  小到大
      datas.sort(function (a, b) {
        return a.MoldStockID - b.MoldStockID;
      });
      moldBlockNo = [];

      var TmpArray = [];
      for (var i = 0, len = datas.length; i < len; i++) {
        console.log('datas.length: ' + datas.length);
        TmpArray = [];
        for (var j = 0; j < 4; j++) {
          TmpArray.push(datas[4 * i + j]);
        }
        if (TmpArray[0] == null) break;
        moldBlockNo.push(TmpArray);
      }
      console.log('inFunction:' + JSON.stringify(moldBlockNo[0]));
    })

    .catch((error) => console.log(error));
}

onMounted(() => {
  getMoldBlockData();
});
</script>

<template>
  <div class="container">
    <header class="row">
      <img alt="Wisher logo" src="./assets/logo.svg" width="270" />
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
      <div v-for="i in moldBlockNo" :key="i.index">
        <div class="blockUnits row">
          <MoldStock :id="i[0].ID" v-if="i[0] != null" />
          <MoldStock :id="i[1].ID" v-if="i[1] != null" />
        </div>
        <div class="blockUnits row">
          <MoldStock :id="i[2].ID" v-if="i[2] != null" />
          <MoldStock :id="i[3].ID" v-if="i[3] != null" />
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
