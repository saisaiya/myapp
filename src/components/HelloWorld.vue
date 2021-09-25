<template>

  <div class="mainBox">
    <div class="nowBox">
      <div>当前期数:({{this.dataArr[0]?this.dataArr[0].preDrawIssue:''}})</div>
      <div class="ball" v-for="(v,index) in nowData" :key="index">{{v}}</div> 
    </div>
    <div class="bottomBox">
      <input type="number" placeholder="输入回查数字 回车键筛选" v-model="value" @keyup.enter="search">
      <span> 数据量：{{count}}</span>
    </div>
    <div class="ballBox">
      <table border="1" class="tableBox" width='350'>
        <tr>
            <th>序号</th>
          <th>位置</th>
          <th>数字</th>
           <th>缺漏次数</th>
           
        </tr>
        <tr v-for="(i,index) in rankArr" :key="index">
            <td>{{index+1}}</td>
          <td>{{i.place}}</td>
          <td>{{i.num}}</td>
          <td :class="i.numIndex>=30?'redColor':i.numIndex>=20?'blueColor':i.numIndex>=10?'greenColor':''">{{i.numIndex}}</td>
        
        </tr>
      </table>
       <!-- <div class="lineBox">
        <div class="lineItem" >
          <div></div><div class="ball" ></div> 缺漏：
        </div>
    </div> -->
    
  </div>
    
    
  </div>
</template>

<script>
import { setInterval, clearInterval } from "timers";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      dataArr: [],
      yestDataArr: [],
      line1: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line2: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line3: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line4: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line5: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line6: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line7: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line8: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line9: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      line10: [
        {
          num: 1,
          numIndex: 0
        },
        {
          num: 2,
          numIndex: 0
        },
        {
          num: 3,
          numIndex: 0
        },
        {
          num: 4,
          numIndex: 0
        },
        {
          num: 5,
          numIndex: 0
        },
        {
          num: 6,
          numIndex: 0
        },
        {
          num: 7,
          numIndex: 0
        },
        {
          num: 8,
          numIndex: 0
        },
        {
          num: 9,
          numIndex: 0
        },
        {
          num: 10,
          numIndex: 0
        }
      ],
      allData: [],
      nowData: [],
      timeClock: null,
      paihangArr: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      rankArr: [],
      value: "",
      count: 0
    };
  },
  mounted() {
    this.search();
    this.timeClock = setInterval(() => {
      this.search();
    }, 60000);
  },
  methods: {
    search() {
      this.yesDayInit();
    },
    paihangArrFn() {
      this.paihangArr=[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
      this.line1.forEach((v, index) => {
        v.place='一'
      });
      this.line2.forEach((v, index) => {
        v.place='二'
      });
      this.line3.forEach((v, index) => {
        v.place='三'
      });
      this.line4.forEach((v, index) => {
       v.place='四'
      });
      this.line5.forEach((v, index) => {
        v.place='五'
      });
      this.line6.forEach((v, index) => {
        v.place='六'
      });
      this.line7.forEach((v, index) => {
        v.place='七'
      });
      this.line8.forEach((v, index) => {
       v.place='八'
      });
      this.line9.forEach((v, index) => {
        v.place='九'
      });
      this.line10.forEach((v, index) => {
        v.place='十'
      });
      this.rankArr = [];
      this.rankArr=this.line1.concat(this.line2).concat(this.line3).concat(this.line4).concat(this.line5).concat(this.line6).concat(this.line7).concat(this.line8).concat(this.line9).concat(this.line10)
     
     this.rankArr.sort((a,b)=>{
       return b.numIndex - a.numIndex
     })
     console.log(this.rankArr,'rank')
    },
    todayInit() {
      this.$axios({
        method: "get",
        url:
          "https://luckylottoz.com/api/result/getPksHistoryList.do?lotCode=10057",
        params: {}
      })
        .then(res => {
          //这里使用了ES6的语法
          //请求成功返回的数据
          this.dataArr = res.data.result.data;
          let str = this.dataArr[0].preDrawCode;
          let all = [];
          this.nowData = str.split(",");
          all = this.dataArr.concat(this.yestDataArr);
          if (this.value > 0) {
            all = all.splice(this.value, all.length);
          }
          console.log(all[0],99999)

          this.allData = all;
          this.count = this.allData.length;
          this.jisuanFn();
        })
        .catch(err => {
          console.log(err); //请求失败返回的数据
        });
    },
    yesDayInit() {
      var day1 = new Date();
      day1.setTime(day1.getTime() - 24 * 60 * 60 * 1000);
      var s1 =
        day1.getFullYear() + "-" + (day1.getMonth() + 1) + "-" + day1.getDate();
      this.$axios({
        method: "get",
        url:
          "https://luckylottoz.com/api/result/getPksHistoryList.do?lotCode=10057",
        params: { date: s1 }
      })
        .then(res => {
          //这里使用了ES6的语法
          //请求成功返回的数据
          this.yestDataArr = res.data.result.data;
          this.todayInit();
        })
        .catch(err => {
          console.log(err); //请求失败返回的数据
        });
    },
    jisuanFn() {
      let line1Arr = [];
      let line2Arr = [];
      let line3Arr = [];
      let line4Arr = [];
      let line5Arr = [];
      let line6Arr = [];
      let line7Arr = [];
      let line8Arr = [];
      let line9Arr = [];
      let line10Arr = [];

      let num1Arr = [];
      let num2Arr = [];
      let num3Arr = [];
      let num4Arr = [];
      let num5Arr = [];
      let num6Arr = [];
      let num7Arr = [];
      let num8Arr = [];
      let num9Arr = [];
      let num10Arr = [];
      let data = this.allData.reverse();
      console.log(data);
      data.forEach(v => {
        num1Arr.push(v.preDrawCode.split(",")[0]); //第一列
        num2Arr.push(v.preDrawCode.split(",")[1]); //第二列
        num3Arr.push(v.preDrawCode.split(",")[2]); //第3列
        num4Arr.push(v.preDrawCode.split(",")[3]); //4
        num5Arr.push(v.preDrawCode.split(",")[4]); //5
        num6Arr.push(v.preDrawCode.split(",")[5]); //6
        num7Arr.push(v.preDrawCode.split(",")[6]); //7
        num8Arr.push(v.preDrawCode.split(",")[7]); //8
        num9Arr.push(v.preDrawCode.split(",")[8]); //9
        num10Arr.push(v.preDrawCode.split(",")[9]); //10
      });
      num1Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line1Arr[0] = {
            num: 1,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line1Arr[1] = {
            num: 2,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line1Arr[2] = {
            num: 3,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line1Arr[3] = {
            num: 4,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line1Arr[4] = {
            num: 5,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line1Arr[5] = {
            num: 6,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line1Arr[6] = {
            num: 7,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line1Arr[7] = {
            num: 8,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line1Arr[8] = {
            num: 9,
            numIndex: num1Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line1Arr[9] = {
            num: 10,
            numIndex: num1Arr.length - (index + 1)
          };
        }
      });

      num2Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line2Arr[0] = {
            num: 1,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line2Arr[1] = {
            num: 2,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line2Arr[2] = {
            num: 3,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line2Arr[3] = {
            num: 4,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line2Arr[4] = {
            num: 5,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line2Arr[5] = {
            num: 6,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line2Arr[6] = {
            num: 7,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
         
          line2Arr[7] = {
            num: 8,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line2Arr[8] = {
            num: 9,
            numIndex: num2Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line2Arr[9] = {
            num: 10,
            numIndex: num2Arr.length - (index + 1)
          };
        }
      });

      num3Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line3Arr[0] = {
            num: 1,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line3Arr[1] = {
            num: 2,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line3Arr[2] = {
            num: 3,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line3Arr[3] = {
            num: 4,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line3Arr[4] = {
            num: 5,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line3Arr[5] = {
            num: 6,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line3Arr[6] = {
            num: 7,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line3Arr[7] = {
            num: 8,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line3Arr[8] = {
            num: 9,
            numIndex: num3Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line3Arr[9] = {
            num: 10,
            numIndex: num3Arr.length - (index + 1)
          };
        }
      });
      num4Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line4Arr[0] = {
            num: 1,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line4Arr[1] = {
            num: 2,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line4Arr[2] = {
            num: 3,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line4Arr[3] = {
            num: 4,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line4Arr[4] = {
            num: 5,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line4Arr[5] = {
            num: 6,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line4Arr[6] = {
            num: 7,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line4Arr[7] = {
            num: 8,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line4Arr[8] = {
            num: 9,
            numIndex: num4Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line4Arr[9] = {
            num: 10,
            numIndex: num4Arr.length - (index + 1)
          };
        }
      });
      num5Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line5Arr[0] = {
            num: 1,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line5Arr[1] = {
            num: 2,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line5Arr[2] = {
            num: 3,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line5Arr[3] = {
            num: 4,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line5Arr[4] = {
            num: 5,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line5Arr[5] = {
            num: 6,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line5Arr[6] = {
            num: 7,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line5Arr[7] = {
            num: 8,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line5Arr[8] = {
            num: 9,
            numIndex: num5Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line5Arr[9] = {
            num: 10,
            numIndex: num5Arr.length - (index + 1)
          };
        }
      });
      num6Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line6Arr[0] = {
            num: 1,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line6Arr[1] = {
            num: 2,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line6Arr[2] = {
            num: 3,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line6Arr[3] = {
            num: 4,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line6Arr[4] = {
            num: 5,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line6Arr[5] = {
            num: 6,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line6Arr[6] = {
            num: 7,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line6Arr[7] = {
            num: 8,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line6Arr[8] = {
            num: 9,
            numIndex: num6Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line6Arr[9] = {
            num: 10,
            numIndex: num6Arr.length - (index + 1)
          };
        }
      });
      num7Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line7Arr[0] = {
            num: 1,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line7Arr[1] = {
            num: 2,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line7Arr[2] = {
            num: 3,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line7Arr[3] = {
            num: 4,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line7Arr[4] = {
            num: 5,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line7Arr[5] = {
            num: 6,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line7Arr[6] = {
            num: 7,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line7Arr[7] = {
            num: 8,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line7Arr[8] = {
            num: 9,
            numIndex: num7Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line7Arr[9] = {
            num: 10,
            numIndex: num7Arr.length - (index + 1)
          };
        }
      });
      num8Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line8Arr[0] = {
            num: 1,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line8Arr[1] = {
            num: 2,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line8Arr[2] = {
            num: 3,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line8Arr[3] = {
            num: 4,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line8Arr[4] = {
            num: 5,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line8Arr[5] = {
            num: 6,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line8Arr[6] = {
            num: 7,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line8Arr[7] = {
            num: 8,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line8Arr[8] = {
            num: 9,
            numIndex: num8Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line8Arr[9] = {
            num: 10,
            numIndex: num8Arr.length - (index + 1)
          };
        }
      });

      num9Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line9Arr[0] = {
            num: 1,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line9Arr[1] = {
            num: 2,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line9Arr[2] = {
            num: 3,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line9Arr[3] = {
            num: 4,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line9Arr[4] = {
            num: 5,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line9Arr[5] = {
            num: 6,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line9Arr[6] = {
            num: 7,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line9Arr[7] = {
            num: 8,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line9Arr[8] = {
            num: 9,
            numIndex: num9Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line9Arr[9] = {
            num: 10,
            numIndex: num9Arr.length - (index + 1)
          };
        }
      });

      num10Arr.forEach((v, index) => {
        if (Number(v) == 1) {
          line10Arr[0] = {
            num: 1,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 2) {
          line10Arr[1] = {
            num: 2,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 3) {
          line10Arr[2] = {
            num: 3,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 4) {
          line10Arr[3] = {
            num: 4,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 5) {
          line10Arr[4] = {
            num: 5,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 6) {
          line10Arr[5] = {
            num: 6,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 7) {
          line10Arr[6] = {
            num: 7,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 8) {
          line10Arr[7] = {
            num: 8,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 9) {
          line10Arr[8] = {
            num: 9,
            numIndex: num10Arr.length - (index + 1)
          };
        }
        if (Number(v) == 10) {
          line10Arr[9] = {
            num: 10,
            numIndex: num10Arr.length - (index + 1)
          };
        }
      });
      for (let m = 0; m < line1Arr.length; m++) {
        if (!line1Arr[m]) {
          // 当前数组为empty时
          line1Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line2Arr.length; m++) {
        if (!line2Arr[m]) {
          // 当前数组为empty时
          line2Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line3Arr.length; m++) {
        if (!line3Arr[m]) {
          // 当前数组为empty时
          line3Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line4Arr.length; m++) {
        if (!line4Arr[m]) {
          // 当前数组为empty时
          line4Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line5Arr.length; m++) {
        if (!line5Arr[m]) {
          // 当前数组为empty时
          line5Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line6Arr.length; m++) {
        if (!line6Arr[m]) {
          // 当前数组为empty时
          line6Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line7Arr.length; m++) {
        if (!line7Arr[m]) {
          // 当前数组为empty时
          line7Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line8Arr.length; m++) {
        if (!line8Arr[m]) {
          // 当前数组为empty时
          line8Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line9Arr.length; m++) {
        if (!line9Arr[m]) {
          // 当前数组为empty时
          line9Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      for (let m = 0; m < line10Arr.length; m++) {
        if (!line10Arr[m]) {
          // 当前数组为empty时
          line10Arr[m] = {
            num: m + 1,
            numIndex: this.allData.length
          };
        }
      }
      line1Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line2Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line3Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line4Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line5Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line6Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line7Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line8Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line9Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });
      line10Arr.sort((a, b) => {
        return b.numIndex - a.numIndex;
      });

      this.line1 = line1Arr;
      this.line2 = line2Arr;
      this.line3 = line3Arr;
      this.line4 = line4Arr;
      this.line5 = line5Arr;
      this.line6 = line6Arr;
      this.line7 = line7Arr;
      this.line8 = line8Arr;
      this.line9 = line9Arr;
      this.line10 = line10Arr;
     
      this.paihangArrFn();
    }
  },
  destroyed() {
    clearInterval(this.timeClock);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mainBox {
  width: 80%;
  margin: 20px auto;
}
.lineBox {
  margin-right: 20px;
}
.lineItem {
  display: flex;
  align-items: center;
}
.ballBox {
  margin-top: 20px
}
.ball {
  color: black;
  background: aqua;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  text-align: center;
  line-height: 40px;
  margin: 10px;
}
.nowBox {
  display: flex;
  align-items: center;
  width: 80%;
  margin: 20px auto;
  text-align: center;
}
.rankItem {
  display: flex;
  align-items: center;
  margin-right: 10px;
}
.rankBox {
  display: flex;
  align-items: center;
  margin: 20px auto;
  text-align: center;
}
.bottomBox{
  text-align: center;
}
.tableBox{
  margin: 0 auto;
  text-align: center
}
.redColor{
  color:red;
}
.blueColor{
  color:blue
}
.greenColor{
  color:green
}
</style>
