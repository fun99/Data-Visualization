<template>
    <div class="content">
       <div class="content-header"></div>
       <div class="content-center">
               <!-- 左侧 -->
               <section class="contenCenterLeft">
                  <!-- 概览区域模块制作 -->
                  <div class="left-data panel">
                     <div class="left-data-center">
                          <ul>
                             <li>
                                <span>99</span>
                                <span style='font-size:12px;margin-top:3px;color:#6489c3'><i style="background-color:#006aff"></i>设备总数</span>
                             </li>
                             <li>
                                <span>99</span>
                                <span style='font-size:12px;margin-top:3px;color:#6489c3'><i style="background-color:#64c1ab"></i>季度新增</span>
                             </li>
                             <li>
                                <span>99</span>
                                <span style='font-size:12px;margin-top:3px;color:#6489c3'><i style="background-color:#67bfa8"></i>运营设备</span>
                             </li>
                             <li>
                                <span>99</span>
                                <span style='font-size:12px;margin-top:3px;color:#6489c3'><i style="background-color:#fc5034"></i>异常设备</span>
                             </li>
                          </ul>
                     </div>
                  </div>
                  <!-- 监控区域模块制作 -->
                   <div class="panel monitoring">
                      <div class="monitoring-center">
                         <div class="monitoring-title">
                            <section :class="{active:num===0}" @click="num=0">故障设备监控</section>
                            <section :class="{active:num===1}" @click="num=1">异常设备监控</section>
                         </div>
                         <div class="monitoring-top">
                              <section>异常时间</section>
                              <section>设备地址</section>
                              <section>异常代码</section>
                         </div>
                         <div class="monitoring-bottom">
                            <div class="hover">
                                <ul>
                                <li v-for="(item,index) in num===0 ? list1 : list2" :key="index">
                                  <span>{{item.data}}</span>
                                  <span>{{item.centent}}</span>
                                  <span>{{item.number}}</span>
                                </li>
                             </ul>
                             <ul>
                                <li v-for="(item,index) in num===0 ? list1 : list2" :key="index">
                                  <span>{{item.data}}</span>
                                  <span>{{item.centent}}</span>
                                  <span>{{item.number}}</span>
                                </li>
                             </ul>
                            </div>
                         </div>
                      </div>
                   </div>
                   <!-- 饼形图模块制作 -->
                   <div class="panel pie">
                        <div class="pieTu">
                           <h3>点位分布统计</h3>
                           <div class="center">
                               <section class="center-left" ref="pieTu">
                                  
                               </section>
                               <section class="center-right">
                                  <div class="center-right-one">
                                      <span style="margin-bottom:7px;color:#fff">99</span>
                                      <span style='font-size:12px;color:#7684d3'><i style="background-color:#f55340"></i>点位总数</span>
                                  </div>
                                  <div class="center-right-one">
                                     <span style="margin-bottom:7px;color:#fff">99</span>
                                     <span style="font-size:12px;color:#7684d3"><i style="background-color:#eac225"></i>本月新增</span>
                                  </div>
                               </section>
                           </div>
                        </div>
                   </div>
               </section>
               <!-- 中间 -->
               <section class="contentCenterCen">
                  <div class="contentCenterCen-top">
                     <div class="title">
                        <span><i class="icon-dell"></i>数据设备统计</span>
                     </div>
                     <div ref="ball" class="ball" style="height:100%"></div>
                  </div>
                  <div class="contentCenterCen-bottom panel">
                      <div class="text">
                         <div class="title-bottom">
                        <span>全国用户总量统计</span>    
                      </div>   
                      <div class="center">
                         <div class="bar" ref="bar"></div>
                         <div class="bar-right">
                             <section>
                                <span>99</span>
                                <span><i style="background-color:#f75934"></i>用户总量</span>
                             </section>
                             <section>
                                <span>99</span>
                                <span><i style="background-color:#ecc919"></i>本月新增</span>
                             </section>
                         </div>
                      </div>
                      </div>
                  </div>
               </section>
               <!-- 右侧 -->
               <section class="contentCenterright">
                   <div class="contentcen-top panel">
                       <div class="centent">  
                           <ul>
                              <li v-for="(item,index) in rightList" :key="index">
                                 <div :class="{activeColor:index===number}" class="top">{{index!==3?item.day+'天':item.day+'时'}}</div>
                              </li>
                           </ul>
                           <div class="center" v-for="(item,index) in centerList" :key="index">
                                 <div class="center-txt" v-if="index===number" :class="{activeColor:index===number}">
                                     <span>{{item.num}}</span>
                                     <span>{{item.num1}}</span>
                                 </div>   
                          </div>
                          <div class="bottom" v-for="(item,index) in bottomList" :key="index"> 
                             <div class="bottom-text" v-if="index===number" :class="{activeColor:index===number}">
                                <span><i></i>{{item.text1}}</span>
                                <span><i></i>{{item.text2}}</span>
                             </div>
                          </div>
                       </div>
                   </div>
               </section>
       </div>
    </div> 
</template>
<script>
// * 所有 将echarts中全部以对象方式导入到echarts中
import * as echarts from 'echarts'
import 'echarts-gl';
export default {
   data() {
      return {
         num:0,
         number:0,
         list1:[{
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         {
            data:'2019-09-09',
            centent:'武汉市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000002
         },
         ],
         list2:[{
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         },
         {
            data:'2019-10-10',
            centent:'襄阳市数据可视化平台全市几乎都在使用用的比例很大',
            number:10000000003
         }],
         rightList:[
           {day:365},
           {day:90},
           {day:30},
           {day:24},
         ],
        centerList:[
         {
          num:666,
          num1:777,
         },
         {
          num:888,
          num1:999,
         },
         {
          num:111,
          num1:222,
         },
         {
          num:456,
          num1:789,
         }
        ],
        bottomList:[
           {
              text1:'订单量',
              text2:'销售额(万元)'
           },
           {
              text1:'订单量',
              text2:'销售额(万元)'
           },
           {
              text1:'订单量',
              text2:'销售额(万元)'
           },
           {
              text1:'订单量',
              text2:'销售额(万元)'
           }
        ]  
      }
   },
   mounted(){
      this.pie(),  // pie
      this.ball(),  // ball
      this.bar()
      this.full()
   },
   computed:{
      
   },
   methods:{
     pie(){
        let myChart = echarts.init(this.$refs.pieTu)
      var option;
      option = {
         tooltip: {
         trigger: 'item',
         formatter: '{a} <br/>{b} : {c} ({d}%)'
       },
      //  颜色
       color:['#006cff','#60cda0','#ed8884','#ff9f7f','#0096ff','#9fe6b8','#32c5e9','#1d9dff'],
  series: [
    {
      name: '点图分布',
      type: 'pie',
      radius: ["10%", "60%"],
      center: ['50%', '50%'],
      roseType: 'radius',
      data: [
        { value: 40, name: '北京' },
        { value: 38, name: '上海' },
        { value: 32, name: '深圳' },
        { value: 30, name: '广州' },
        { value: 28, name: '杭州' },
        { value: 26, name: '武汉' },
        { value: 22, name: '天津' },
        { value: 18, name: '南京' }
      ],
      labelLine:{
       length:6, 
       length2:8
    },
    label:{
      fontSize:10,
      color:'#fff'
    }
    }
  ]
};
option && myChart.setOption(option);
window.addEventListener('resize',function(){
   myChart.resize()
})
     },
     ball(){
      let ROOT_PATH ='https://cdn.jsdelivr.net/gh/apache/echarts-website@asf-site/examples';
      let myChart = echarts.init(this.$refs.ball);
      let option;
      option = {
         backgroundColor: '#000',
         globe: {
            baseTexture: ROOT_PATH + '/data-gl/asset/earth.jpg',
            shading: 'lambert',
            environment: ROOT_PATH + '/data-gl/asset/starfield.jpg',
            atmosphere: {
               show: true
            },
            light: {
               ambient: {
               intensity: 0.1
               },
               main: {
               intensity: 1.5
               }
            }
         },
         series: []
         };
         option && myChart.setOption(option);

     },
     bar(){
        let item = {
             // 在data中放对象是对当前柱子值设置样式或别的
                          value:1200, // 设置单个数据项的数值,
                          itemStyle:{  // 修改单个柱子样式
                              color:'#254065'
                          },
                          emphasis:{  // 不让高亮显示属性   
                              itemStyle:{
                                  color:'inherit'  // 不让高亮显示   //  设置的颜色值跟当前单个柱子样式一样可也以#254065
                              }
                          },
                          tooltip:{
                        extraCssText :'opacity:0'  // 取消当前项提示框  因为没有show这个属性 使用opacity透明度来设置0-1 0一点看不到 1显示看到
                        
                      }
        }
       let myChart = echarts.init(this.$refs.bar)
       let option = {
          color:{
           type:'linear',
           x:0,
           y:0,
           x2:0,
           y2:1,
          colorStops:[{
               offset:0,color:'red',//0%开始的颜色
            },{
               offset:1,color:'blue',//100%结束颜色
            }],    
            globalCoord:false  // 缺省为false
          },
         tooltip: {
            trigger: 'item',
         },
         grid: {
            left: '0%',
            right: '22%',
            bottom: '0%',
            containLabel: true,
            height:90,
            width:260,
            show:true,
            borderColor:'rgba(0,240,255,.3)'
         },
         xAxis: [
            {
               type: 'category',
               data: ['上海', '广州', '北京', '深圳', '合肥', '', '......', '', '杭州', '厦门', '济南', '成都', '重庆'],
               axisTick: {
               alignWithLabel: false,
               show:false,
               },
               axisLabel:{
                  color:'#4c9bfd'
               },
               axisLine:{
                  lineStyle:{
                     color:'rgba(0,240,255,.3)'
                  }
               }
            }
         ],
         yAxis: [
            {
             type: 'value',
             axisTick: {
               alignWithLabel: false,
               show:false,
               },
               axisLabel:{
                  color:'#4c9bfd'
               },
               axisLine:{
                  lineStyle:{
                     color:'rgba(0,240,255,.3)'
                  }
               },
               splitLine:{
                  lineStyle:{
                     color:'rgba(0,240,255,.3)'
                  }
               }
            }
         ],
         series: [
            {
               name: 'Direct',
               type: 'bar',
               barWidth: '60%',
               data: [2100,1900,1700,1560,1400,item,item,item,900,750,600,480,240],
            },
         ]
         };
         option && myChart.setOption(option);
     },
     full(){
        setInterval(()=>{
                if(this.number===3) return this.number = 0
                this.number++
         },1500)
      }
   }
}
</script>
<style scoped>
     .content-header{
        width: 100%;
        height: 80px; 
        background: url('~@/assets/images/logo.png');
        background-size: 100% 100%;
     }
     .content .content-center{
        display: flex;
     }
     .content .content-center section{
        flex: 3;
     }
     .content-center section:nth-child(2){
        flex: 4;
     }
     .content-center section:nth-child(3){
        flex: 3;
     }
     .content-center .contenCenterLeft .left-data .left-data-center{
        position: absolute;
        top: -55px;
        bottom: -20px;
        left:-160px;
        right:-38px;
     }
     .content-center .contenCenterLeft .left-data .left-data-center ul{
        display: flex;
        justify-content: space-between;
        align-items: center;
        list-style: none;
     }
     .content-center .contenCenterLeft .left-data .left-data-center ul li{
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
     }
     .content-center .contenCenterLeft .left-data .left-data-center ul li span:nth-of-type(1){
        color: #fff;
     }
     .content-center .contenCenterLeft .left-data .left-data-center ul li span:nth-of-type(2) i{
        width: 5px;
        height: 12px;
        position: relative;
        top: 1.5px;
        right: 5px;
        border-radius: 2px;
        display: inline-block;
     }
     .content-center .contenCenterLeft .monitoring{
        height: 245px;
     }
     .content-center .contenCenterLeft .monitoring-center{
        position: absolute;
        top: -35px;
        bottom: -20px;
        left:-90px;
        right:-38px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-title{
        display: flex;
        width: 240px;
        font-size: 14px;
        color: #333793;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-title section:nth-of-type(1){
        border-right:1px solid #53dcf1 ;
        cursor: pointer;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-title section:nth-of-type(2){
        margin-left: 12px;
        cursor: pointer;
     }
     .active{
        color: #fff;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-top{
        display: flex;
        margin-top: 12px;
        color: #7db1e5;
        font-size: 12px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom{
        height: 222px;
        margin-top: 7px;
        overflow: hidden;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover { 
        animation: move 15s linear infinite;
        height: 100%;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover:hover{
        animation-play-state: paused;
        cursor: pointer;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul{
        list-style: none;
        margin: 0;
        padding: 0;
        font-size: 12px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li{
        display: flex;
        color: #7db1e5;
        line-height: 22.3px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li:hover{
        background:#181920;
        width: 287px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li span:nth-of-type(1){
        overflow: hidden;
        width: 90px;
        padding-left: -10px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li span:nth-of-type(2){
        overflow: hidden;
        width: 120px;
        white-space:nowrap;
        text-overflow:ellipsis;
        margin-left: -10px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li span:nth-of-type(3){
        margin-left: 6px
     }
     @keyframes move{
        100%{
           transform: translateY(-50%);
        }
     }
    .content-center .contenCenterLeft .pie{
       height: 90px;
    }
    .content-center .contenCenterLeft .pieTu{
       position: absolute;
       top: -50px;
       bottom: -20px;
       left:-92px;
       right:-38px;
    }
    .content-center .contenCenterLeft .pie h3 {
       font-size: 15px;
       color: #fff;
       font-weight: normal;
    }
    .content-center .contenCenterLeft .center{
       display: flex;
       height: 100px;
       width: 360px;
       margin-top: -6px;
    }
    .content-center .contenCenterLeft .center .center-left{
       margin-left: -30px;
       width: 230px;
    }
    .content-center .contenCenterLeft .center .center-right{
       margin-right: 70px;
       padding: 15px;
       /* width: 10px; */
       flex:1;
       display: flex;
       flex-direction: column;
       justify-content: space-around;
       align-items: center;
       /* background: blue; */
       background: url('../assets/images/rect.png') no-repeat;
       background-size: 100% 100%;
    }
    .content-center .contenCenterLeft .center .center-right .center-right-one{
       display: flex;
       justify-content: center;
       flex-direction: column;
       align-items: center;
    }
    .content-center .contenCenterLeft .center .center-right .center-right-one span:nth-of-type(2) i {
       width: 5px; 
       height: 12px;
       display: inline-block;
       border-radius: 2px;
       margin-left: -7px;
       margin-right: 7px;
       position: relative;
       top: 1px;
    }
    /* 中间样式 */
     .contentCenterCen .contentCenterCen-top {
        border: 1px solid transparent;
        height: 375px;
        margin: 0 15px;
     }
     .contentCenterCen .contentCenterCen-top .title{
        font-size: 15px;
        color: #fff;
        margin: 2px 0 10px 10px;
     }
     .contentCenterCen .contentCenterCen-top .title span i {
        position: relative;
        top: 1px;
        right: 5px;
        color: #fff;
     }
    .contentCenterCen .contentCenterCen-bottom {
       height: 90px;
       margin-top:50px;
       margin-left:20px;
       margin-right:20px;
       color:#fff;
       font-size: 15px;
    }
    .contentCenterCen .contentCenterCen-bottom .text{
       position: absolute;
       top:-35px;
       left:-95px;
       right: -38px;
       bottom: -20px;
    }
    .contentCenterCen .contentCenterCen-bottom .text .center{
       display: flex;
    }
   .contentCenterCen .contentCenterCen-bottom .text .center .bar {
      margin-top: 3px;
      width: 370px;
      height: 100px;
   }
  .contentCenterCen .contentCenterCen-bottom .text .center .bar-right{
     width: 103px;
     margin-top: 3px;
     margin-left: -87px;
     background: url('../assets/images/rect.png') no-repeat;
     background-size: 100% 100%;
     display: flex;
     flex-direction: column;
     justify-content:space-around;
     align-items: center;
  }
  .contentCenterCen .contentCenterCen-bottom .text .center .bar-right section{
     display: flex;
     flex-direction: column;
     justify-content: space-around;
     align-items: center;
  }
  .contentCenterCen .contentCenterCen-bottom .text .center .bar-right section span:nth-of-type(2){
     font-size: 12px;
  }
  .contentCenterCen .contentCenterCen-bottom .text .center .bar-right section span:nth-of-type(2) i{
     width:5px;
     height: 12px;
     border-radius: 2px;
     display: inline-block;
     position: relative;
     top:1px;
     right: 5px;
     }
     /* 右侧内容 */
     .content-center .contentCenterright .contentcen-top {
        position: relative;
        right: 12px;
        height: 50px;
     }
     .content-center .contentCenterright .contentcen-top .centent{
        position: absolute;
        top:-51px;
        right: -38px;
        bottom:-20px;
        left: -132px;
     }
     .content-center .contentCenterright .contentcen-top ul {
        list-style: none;
        margin: 0;
        padding: 20px 0 0 20px;
        display: flex;
     }
     .content-center .contentCenterright .contentcen-top ul li{
        color: #414874;
        flex: 1;
     }
     .content-center .contentCenterright .contentcen-top ul li .top{
        border-right: 2px solid #4fb5c8;
        text-align: center;
     }
    .content-center .contentCenterright .contentcen-top .centent .center{
        margin-top: 10px;
        margin-left: 40px;
    }
    .content-center .contentCenterright .contentcen-top .centent .center .center-txt{
        position: absolute;
        color: #414874;
    }
    .content-center .contentCenterright .contentcen-top .centent .center span:nth-of-type(1){
        margin-right: 220px
    }
    .content-center .contentCenterright .contentcen-top .centent .bottom{
       position:relative
    }
    .content-center .contentCenterright .contentcen-top .centent .bottom-text{
       position: absolute;
       top: 27px;
       left: 40px;
       color: #414874;
       font-size: 12px;
    }
    .content-center .contentCenterright .contentcen-top .centent .bottom-text span:nth-of-type(1){
       margin-right: 173px;
    }
    .activeColor{
       color: #fff !important;
    }
    .content-center .contentCenterright .contentcen-top .centent .bottom-text span:nth-of-type(1) i{
       display: inline-block;
       position: relative;
       top: 2px;
       right: 2px;
       width: 5px;
       height: 12px;
       border-radius: 2px;
       background: #f5563e;
    }
    .content-center .contentCenterright .contentcen-top .centent .bottom-text span:nth-of-type(2) i{
       display: inline-block;
       position: relative;
       top: 2px;
       right: 2px;
       width: 5px;
       height: 12px;
       border-radius: 2px;
       background: #ecc615;
    }
</style>
