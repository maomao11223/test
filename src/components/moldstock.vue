<script setup>
import axios from 'axios';
import { reactive, ref } from 'vue';

defineProps({
  id: {
    type: String,
    required: true,
  },
});

const url = 'http://192.168.1.101/api/Commold/GetByID';

// axios
//   .post(url, {
//     Id: id,
//   })
//   .then((response) => console.log(response))
//   .catch((error) => console.log(error));

const data = {
  StatusCode: 200,
  Message: null,
  Payload: {
    ID: 16,
    ModelID: '94100002',
    Name: 'P180108A-MA曲柄飾蓋 (長) 模具',
    Hold: 2,
    Tonnage: 1,
    CustName: null,
    VendorName: null,
    CustomerCode: null,
    VendorCode: null,
    PDF: null,
    CanUseCount: 0,
    SafetyStock: 1,
    MaintainWorkHour: 3,
    CycleTime: 5.8,
    IsEnabled: true,
    Remark: null,
    ProdId: 'A-080-06',
    ProductName: null,
    MoldStockID: 'G1X1Y1',
    MoldStockEnabled: true,
    MoldMaxLimit: 100,
    MoldInjection: 0,
    MoldStatus: 1,
    MoldStatusName: null,
    MoldMaxLifeCycle: 500,
    MoldTotalInjection: 100,
    MoldBlock: 1,
    MoldPicList: [],
    MachineList: [],
    CreateTime: '0001-01-01T00:00:00',
    CreateUser: null,
    UpdateTime: '2022-04-22T15:39:25',
    UpdateUser: null,
  },
  Pagination: {
    Total: null,
    PageSize: null,
    CurrentPage: null,
  },
  ResponseTime: '2022-11-07T16:19:53.7387511+08:00',
};

var isgreen = data.Payload.MoldStatus == 0 ? true : false;
var isyellow = data.Payload.MoldStatus == 1 ? true : false;
var isred = data.Payload.MoldStatus == 2 ? true : false;
</script>

<template>
  <div class="mold">
    <div class="card">
      <div class="cardtop">
        <div>庫格{{ id }}</div>
        <img src="../assets/Mold_PIC.png" alt="" width="100" />
      </div>
      <div class="cardbody row">
        <div class="trafficlight">
          <div class="light" :class="{ 'light_green': isgreen }"></div>
          <div class="light" :class="{ 'light_yellow': isyellow }"></div>
          <div class="light" :class="{ 'light_red': isred }"></div>
        </div>
        <div class="moldDetail">
          <p>
            <strong>
              單次保養上限:
              <span style="color: #fff100">
                {{ data.Payload.MoldMaxLimit }}
              </span>
            </strong>
          </p>
          <p>
            <strong>
              累計模具射出:
              <span> {{ data.Payload.MoldInjection }} </span>
            </strong>
          </p>
          <p>
            <strong
              >大保養上限:
              <span style="color: var(--color-red)">{{
                data.Payload.MoldMaxLifeCycle
              }}</span></strong
            >
          </p>
          <p>
            <strong
              >總射出數:
              <span style="color: #172a88">{{
                data.Payload.MoldTotalInjection
              }}</span></strong
            >
          </p>
        </div>
      </div>
    </div>
    <div class="cardBottom">{{ data.Payload.ModelID }}</div>
  </div>
</template>

<style scoped>
.mold {
  margin: 5px;
  /*display: flex;
  flex-direction: column;
  align-content: center; */
}
.card {
  /* width: 250px; */
  border: 5px solid #444040;
  border-radius: 20px;
}

.cardtop {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 1.5rem;
  text-decoration: underline;
}

img {
  margin-top: 5px;
}

.cardbody {
  margin: 5px 5px;
}

.trafficlight {
  width: 45px;
  height: 120px;
  background: #444040;
  border-radius: 5px;
  padding: 5px;
}

.light {
  border: 2px solid var(--vt-c-white-soft);
  height: 35px;
  width: 35px;
  border-radius: 50%;
}

.light_green {
  background: var(--color-green);
}

.light_yellow {
  width: 100%;
  background: var(--color-yellow);
}

.light_red {
  background: var(--color-red);
}

.moldDetail {
  margin-left: 10px;
  font-size: 1.4rem;
}

.cardBottom {
  width: 220px;
  background-color: var(--vt-c-black);
  color: var(--color-yellow);
  text-align: center;
  margin: 0 auto;
  margin-top: 3px;
  font-size: 1.5rem;
}
p {
  /* 強制不換行,字數太多可能跑版 */
  /* white-space: nowrap; */
}
</style>
