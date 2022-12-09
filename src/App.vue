<script setup>
import axios from 'axios';
import MoldStock from './components/moldstock.vue';
import { reactive, ref, onMounted } from 'vue';

var moldBlocks = reactive([
  { moldBlock: 1, moldBlockName: '內製區' },
  { moldBlock: 2, moldBlockName: '墊片區' },
]);

var currentBlock = ref(1);

var moldBlockNo = reactive([
  [
    {
      'ID': 35,
      'ModelID': '9R228022',
      'Name': '9R228022',
      'Hold': 1,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': '9R228022',
      'ProductName': 'BRN175A塑膠汽缸',
      'MoldStockID': 'mold17',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 2198,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 2198,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:58:27',
      'UpdateUser': null,
    },
    {
      'ID': 36,
      'ModelID': '9R228632',
      'Name': '塑膠後塞毛胚_DWFP12233',
      'Hold': 4,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 65,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': '9R228632',
      'ProductName': '塑膠後塞毛胚_DWFP12233_內製',
      'MoldStockID': 'mold18',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 24,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 24,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-05-12T13:26:45',
      'UpdateUser': null,
    },
    {
      'ID': 37,
      'ModelID': 'empty07',
      'Name': 'Empty',
      'Hold': 0,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': 'TEST',
      'ProductName': 'TEST',
      'MoldStockID': 'mold19',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:58:56',
      'UpdateUser': null,
    },
    {
      'ID': 38,
      'ModelID': 'empty08',
      'Name': 'Empty',
      'Hold': 0,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': 'TEST',
      'ProductName': 'TEST',
      'MoldStockID': 'mold20',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:59:05',
      'UpdateUser': null,
    },
  ],
  [
    {
      'ID': 39,
      'ModelID': '9R227549-8',
      'Name': '9R227549(第8模)',
      'Hold': 144,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': '9R227549',
      'ProductName': '墊片_土黃色_SB-CAP',
      'MoldStockID': 'mold21',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:59:13',
      'UpdateUser': null,
    },
    {
      'ID': 40,
      'ModelID': '9R227549-5',
      'Name': '9R227549(第5模)',
      'Hold': 144,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': '9R227549',
      'ProductName': '墊片_土黃色_SB-CAP',
      'MoldStockID': 'mold22',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 898,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 898,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:58:02',
      'UpdateUser': null,
    },
    {
      'ID': 41,
      'ModelID': '9R232902',
      'Name': '9R232902',
      'Hold': 4,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': '詠豪科技',
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': '9R232902',
      'ProductName': 'BN200SB塑膠汽缸',
      'MoldStockID': 'mold23',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 1638,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 1638,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-29T14:06:56',
      'UpdateUser': null,
    },
    {
      'ID': 42,
      'ModelID': 'empty12',
      'Name': 'Empty',
      'Hold': 0,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': 'TEST',
      'ProductName': 'TEST',
      'MoldStockID': 'mold24',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '2022-04-14T13:40:09',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:59:30',
      'UpdateUser': null,
    },
  ],
  [
    {
      'ID': 43,
      'ModelID': 'empty01',
      'Name': 'Empty',
      'Hold': 4,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': false,
      'Remark': null,
      'ProdId': 'TEST',
      'ProductName': 'TEST',
      'MoldStockID': 'mold13',
      'MoldStockEnabled': null,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '0001-01-01T00:00:00',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:54:16',
      'UpdateUser': null,
    },
    {
      'ID': 44,
      'ModelID': 'empty02',
      'Name': 'Empty',
      'Hold': 4,
      'Tonnage': 0,
      'CustName': null,
      'VendorName': null,
      'CustomerCode': null,
      'VendorCode': null,
      'PDF': null,
      'CanUseCount': 0,
      'SafetyStock': 0,
      'MaintainWorkHour': 0,
      'CycleTime': 0,
      'IsEnabled': true,
      'Remark': null,
      'ProdId': 'TEST',
      'ProductName': 'TEST',
      'MoldStockID': 'mold14',
      'MoldStockEnabled': true,
      'MoldMaxLimit': 5000,
      'MoldInjection': 0,
      'MoldStatus': 1,
      'MoldStatusName': '良好',
      'MoldMaxLifeCycle': 500000,
      'MoldTotalInjection': 0,
      'MoldBlock': 2,
      'MoldPicList': [],
      'MachineList': [],
      'CreateTime': '0001-01-01T00:00:00',
      'CreateUser': null,
      'UpdateTime': '2022-04-14T14:57:06',
      'UpdateUser': null,
    },
    null,
    null,
  ],
]);

var datas = [{ ID: 1, MoldStockID: 'mold01' }];
var MoldStockID = ref(12);
var ID = ref(1);

const url = 'http://test';

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
        datas[i].ID.toString();
        for (var j = 0; j < 4; j++) {
          TmpArray.push(datas[4 * i + j]);
        }
        if (TmpArray[0] == null) break;
        moldBlockNo.push(TmpArray);
      }
      console.log('inFunction:' + JSON.stringify(moldBlockNo));
    })

    .catch((error) => console.log(error));
}

onMounted(() => {
  // getMoldBlockData();
  console.log(typeof moldBlockNo[0][0].ID);
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
      <div v-for="item in moldBlockNo" :key="item.index">
        <div class="blockUnits row">
          <MoldStock :id="item[0].ModelID" v-if="item[0] != null" />
          <MoldStock :id="item[1].ModelID" v-if="item[1] != null" />
        </div>
        <div class="blockUnits row" v-if="item[2] != null">
          <MoldStock :id="item[2].ModelID" v-if="item[2] != null" />
          <MoldStock :id="item[3].ModelID" v-if="item[3] != null" />
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
  display: -webkit-box;
}
</style>
