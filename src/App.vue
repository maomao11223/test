<script setup>
import axios from 'axios';
import MoldStock from './components/moldstock.vue';
import { ref } from 'vue';

// var moldBlock = ref(1);
// var moldBlockName = '內製區';

var moldBlocks = [
  { index: 0, moldBlock: 1, moldBlockName: '內製區' },
  { index: 1, moldBlock: 2, moldBlockName: '墊片區' },
];
//todo:測試用,上線後刪除
// const testData = [
//   {
//     'ID': 17,
//     'ModelID': '101953',
//     'Name': '101953',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 24.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101953',
//     'ProductName': '101953-TVA6開關螺帽',
//     'MoldStockID': 'mold01',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 4919,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 4919,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-27T11:52:36',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 18,
//     'ModelID': '101956',
//     'Name': '101956',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 22.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101956',
//     'ProductName': '101956-TVA6開關襯套',
//     'MoldStockID': 'mold03',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 0,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 0,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-29T13:55:30',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 19,
//     'ModelID': '101957',
//     'Name': '101957',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 22.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101957',
//     'ProductName': '101957-TVA6開關內座',
//     'MoldStockID': 'mold04',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 0,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 9820,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-06-08T09:53:10',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 20,
//     'ModelID': '180648-1',
//     'Name': '180648(YH)',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 0.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '180648',
//     'ProductName': 'TVA15/17/19/21/22內閥(含油封)',
//     'MoldStockID': 'mold02',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 749,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 6048,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-08T12:53:01',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 17,
//     'ModelID': '101953',
//     'Name': '101953',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 24.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101953',
//     'ProductName': '101953-TVA6開關螺帽',
//     'MoldStockID': 'mold12',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 4919,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 4919,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-27T11:52:36',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 18,
//     'ModelID': '101956',
//     'Name': '101956',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 22.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101956',
//     'ProductName': '101956-TVA6開關襯套',
//     'MoldStockID': 'mold11',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 0,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 0,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-29T13:55:30',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 19,
//     'ModelID': '101957',
//     'Name': '101957',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 22.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '101957',
//     'ProductName': '101957-TVA6開關內座',
//     'MoldStockID': 'mold10',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 0,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 9820,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-06-08T09:53:10',
//     'UpdateUser': null,
//   },
//   {
//     'ID': 20,
//     'ModelID': '180648-1',
//     'Name': '180648(YH)',
//     'Hold': 4,
//     'Tonnage': 0,
//     'CustName': null,
//     'VendorName': null,
//     'CustomerCode': null,
//     'VendorCode': null,
//     'PDF': null,
//     'CanUseCount': 0,
//     'SafetyStock': 0,
//     'MaintainWorkHour': 0.0,
//     'CycleTime': 0.0,
//     'IsEnabled': true,
//     'Remark': null,
//     'ProdId': '180648',
//     'ProductName': 'TVA15/17/19/21/22內閥(含油封)',
//     'MoldStockID': 'mold09',
//     'MoldStockEnabled': true,
//     'MoldMaxLimit': 5000,
//     'MoldInjection': 749,
//     'MoldStatus': 1,
//     'MoldStatusName': '良好',
//     'MoldMaxLifeCycle': 500000,
//     'MoldTotalInjection': 6048,
//     'MoldBlock': 1,
//     'MoldPicList': [],
//     'MachineList': [],
//     'CreateTime': '2022-04-01T11:49:08',
//     'CreateUser': null,
//     'UpdateTime': '2022-04-08T12:53:01',
//     'UpdateUser': null,
//   },
// ];
//正式用
var currentBlock = ref(1);
//正式用
var moldBlockNo = [];
//正式用
var datas = [];

const url = 'http://192.168.1.101/api/Commold/GetCommoldList';

//更改所在區域
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
  //正式用
  while (moldBlockNo.length > 0) {
    moldBlockNo.pop();
  }
  getMoldBlockData();

  //todo: 測試用,上線後刪除
  //測試用:取得所在區域的模具架資料
  // testGetData();

  //console.log('length:' + moldBlockNo.length);
}

//todo: 測試用,上線後刪除
//測試用:取得所在區域的模具架資料
// function testGetData() {
//   // //拆出MoldStockID
//   for (var i = 0; i < testData.length; i++) {
//     testData[i].ID = parseInt(testData[i].MoldStockID.replace(/mold/g, ''), 10);
//     //console.log(testData[i].MoldStockID);
//   }

//   // //測試排序  小到大
//   testData.sort(function (a, b) {
//     return a.ID - b.ID;
//   });

//   for (var i = 0, len = testData.length; i < len; i += 4) {
//     moldBlockNo.push(testData.slice(i, i + 4));
//   }

//   //console.log(moldBlockNo);
// }
//testGetData();

//正式用
//取得所在區域的模具架資料
function getMoldBlockData() {
  axios
    .post(url, {
      'MoldBlock': currentBlock,
      'ModelID': '',
      'ModelName': '',
      'MoldStockID': '',
      'PageSize': 10,
      'CurrentPage': 1,
    })
    .then((response) => {
      console.log(response);

      datas = response.Payload;
      //拆出MoldStockID
      for (var i = 0; i < datas.length; i++) {
        datas[i].ID = parseInt(datas[i].MoldStockID.replace(/mold/g, ''), 10);
        //console.log(datas[i].MoldStockID);
      }

      //測試排序  小到大
      datas.sort(function (a, b) {
        return a.ID - b.ID;
      });

      for (var i = 0, len = datas.length; i < len; i += 4) {
        moldBlockNo.push(datas.slice(i, i + 4));
      }

      console.log(moldBlockNo);
    })
    .catch((error) => console.log(error));
}
getMoldBlockData();
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
      <div class="" v-for="items in moldBlockNo" :key="items.index">
        <div class="blockUnits row">
          <MoldStock :id="items[0].MoldStockID" />
          <MoldStock :id="items[1].MoldStockID" />
        </div>
        <div class="blockUnits row">
          <MoldStock :id="items[2].MoldStockID" />
          <MoldStock :id="items[3].MoldStockID" />
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
