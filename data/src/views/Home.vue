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
                   <div class="content-center panel">
                       <div class="centent">
                          <div>
                             <h2>销售额统计</h2>
                          <section>
                             <a href="#" @click="Abtn(index)" :class="{bg:index===num1}" v-for="(item,index) in aList" :key="index">{{item.name}}</a>
                          </section>
                          </div>
                          <div class="text"><span>单位:万</span></div>
                          <div class="bottom" ref="cate"></div>
                       </div>
                   </div> 
                   <div class="content-wrap">
                           <div class="wrap-left panel">
                               <div class="wrap">
                                   <h2>渠道分布</h2>
                                  <section ref="aLeft"></section>
                               </div>    
                           </div>
                           <div class="wrap-right panel">
                              <div class="wrap">
                                  <h3>统计</h3>
                                 <section ref="bRight"></section>
                                  <div class="abs">50%</div>
                                  <div class="flex">
                                     <div class="bottomLeft">
                                        <span>99</span>
                                        <span>销售额(万元)</span>
                                     </div>
                                     <div class="bottomRight">
                                        <span>150%</span>
                                        <span>同比增长</span>
                                     </div>
                                  </div>
                              </div>
                           </div>
                   </div>
                   <div class="content-after panel">
                       <div class="after">
                          <div class="after-left">
                               <h3>全国可爱多</h3>
                               <ul>
                                  <li>
                                    <span>1</span>
                                    <span>可爱多</span>
                                  </li>
                                  <li>
                                    <span>2</span>
                                    <span>娃哈哈</span>
                                  </li>
                                  <li>
                                    <span>3</span>
                                    <span>喜之郎</span>
                                  </li>
                               </ul>
                          </div>
                          <div class="after-right">
                           <div class="after-right-top">
                              <h3>各省热销</h3>
                              <span>//近30日//</span>
                           </div>
                           <div class="after-right-content">
                              <div class="after-right-content-left">
                                       <ul>
                                          <li v-for="(item,index) in hotData" :key='index' @mouseenter='mouse(index)' :class="{a:index===hotIndex}">
                                             <span style="margin-right:10px">{{item.city}}</span>
                                             <span>{{item.sales}}</span>
                                             <span style="margin-left:3px"><i :class="item.flag ? 'icon-up' : 'icon-down'" :style="item.flag ? 'color:#da503e' : 'color:#46af9d' "></i></span>
                                          </li>
                                       </ul>
                              </div>
                              <div class="after-right-content-right">
                                    <ul>
                                       <li v-for="(item,index) in hotData" :key="index">
                                          <div v-for="item in item.brands" :key="item">
                                           <div v-if="hotIndex===index">  
                                          <span style="margin-right:10px">{{item.name}}</span>
                                          <span>{{item.num}}</span>
                                          <span style="margin-left:3px"><i :class="item.flag ? 'icon-up' : 'icon-down'" :style="item.flag ? 'color:#da503e' : 'color:#46af9d' "></i></span>
                                          </div>
                                          </div>
                                       </li>
                                    </ul>
                              </div>
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
         num1:0,
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
        ],
        aList:[
           {name:'年'},
           {name:'季'},
           {name:'月'},
           {name:'周'}
        ],
        data:[
       {
      a:[24, 40, 101, 134, 90, 230, 210, 230, 120, 230, 210, 120],
      b:[40, 64, 191, 324, 290, 330, 310, 213, 180, 200, 180, 79]
       },
      {
      a:[23, 75, 12, 97, 21, 67, 98, 21, 43, 64, 76, 38],
      b:[43, 31, 65, 23, 78, 21, 82, 64, 43, 60, 19, 34]
      },
      {
      a:[34, 87, 32, 76, 98, 12, 32, 87, 39, 36, 29, 36],
      b:[56, 43, 98, 21, 56, 87, 43, 12, 43, 54, 12, 98]
      },
      {
      a:[43, 73, 62, 54, 91, 54, 84, 43, 86, 43, 54, 53],
      b:[32, 54, 34, 87, 32, 45, 62, 68, 93, 54, 54, 24]
      },
       ],
        hotData:[
         {
        city: '北京',  // 城市
        sales: '25, 179',  // 销售额
        flag: true, //  上升还是下降
        brands: [   //  品牌种类数据
          { name: '可爱多', num: '9,086', flag: true },
          { name: '娃哈哈', num: '8,341', flag: true },
          { name: '喜之郎', num: '7,407', flag: false },
          { name: '八喜', num: '6,080', flag: false },
          { name: '小洋人', num: '6,724', flag: false },
          { name: '好多鱼', num: '2,170', flag: true },
        ]
      },
      {
        city: '河北',
        sales: '23,252',
        flag: false,
        brands: [
          { name: '可爱多', num: '3,457', flag: false },
          { name: '娃哈哈', num: '2,124', flag: true },
          { name: '喜之郎', num: '8,907', flag: false },
          { name: '八喜', num: '6,080', flag: true },
          { name: '小洋人', num: '1,724', flag: false },
          { name: '好多鱼', num: '1,170', flag: false },
        ]
      },
      {
        city: '上海',
        sales: '20,760',
        flag: true,
        brands: [
          { name: '可爱多', num: '2,345', flag: true },
          { name: '娃哈哈', num: '7,109', flag: true },
          { name: '喜之郎', num: '3,701', flag: false },
          { name: '八喜', num: '6,080', flag: false },
          { name: '小洋人', num: '2,724', flag: false },
          { name: '好多鱼', num: '2,998', flag: true },
        ]
      },
      {
        city: '江苏',
        sales: '23,252',
        flag: false,
        brands: [
          { name: '可爱多', num: '2,156', flag: false },
          { name: '娃哈哈', num: '2,456', flag: true },
          { name: '喜之郎', num: '9,737', flag: true },
          { name: '八喜', num: '2,080', flag: true },
          { name: '小洋人', num: '8,724', flag: true },
          { name: '好多鱼', num: '1,770', flag: false },
        ]
      },
       {
        city: '山东',
        sales: '20,760',
        flag: true,
        brands: [
          { name: '可爱多', num: '9,567', flag: true },
          { name: '娃哈哈', num: '2,345', flag: false },
          { name: '喜之郎', num: '9,037', flag: false },
          { name: '八喜', num: '1,080', flag: true },
          { name: '小洋人', num: '4,724', flag: false },
          { name: '好多鱼', num: '9,999', flag: true },
        ]
      }
    ],
    hotIndex:0,
      }
   },
   mounted(){
      this.pie(),  // pie
      this.ball(),  // ball
      this.bar(),  
      this.full(),
      this.cate(),
      this.time(),
      this.radar(),
      this.pies(),
      this.set()
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
      },
      time(){
         setInterval(() => {
            if(this.num1>=3) {
                   this.num1 = 0
                   this.Abtn(this.num1)
                   return 
                }
                this.Abtn(this.num1)
                this.num1++ 
         }, 1500);
      },
     cate(){
       var myChart = echarts.init(this.$refs.cate)
         var option = {
            tooltip: {
               trigger: 'axis'
            },
            legend: {
               data: ['预期销售额', '实例销售额'],
               textStyle:{
                  fontSize:7,
                  color:'#4c9bfd'
               },
               right:'10%'
            },
            grid: {
               left: '3%',
               right: '4%',
               bottom: '3%',
               top:'25%',
               containLabel: true,
               show:true,
               borderColor:'#012f4a'
            },
            height:70,
            xAxis: {
               type: 'category',
               boundaryGap: false,
               data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月','8月','9月','10月','11月','12月'],
                axisTick:{
                   show:false // 去除刻度
               },
                axisLine:{
                    show:false  // 去除x轴横线颜色
                },
                axisLabel:{
                    fontSize:6,  // x轴文字大小
                    color:'#4c9bfd'  // x轴文字的颜色
                },
                
            },
            yAxis: {
               type: 'value',
               axisTick:{
                   show:false // 去除刻度
               },    
                axisLabel:{
                   fontSize:6,
                   color:'#4c9bfd' // y轴文字颜色
                },
                splitLine:{
                    lineStyle:{
                        color:'#012f4a' //y轴的分隔线
                    }
                }
            },
            color:['pink','orange'],
            series: [
               {
                  name: '预期销售额',
                  type: 'line',
                  stack: 'Total',
                  smooth:true,
                  data: this.data[this.num1].a
               },
               {
                  name: '实例销售额',
                  type: 'line',
                  stack: 'Total',
                  smooth:true,
                  data: this.data[this.num1].b
               },
            ]
            };
       myChart.setOption(option);
     },
     Abtn(index){
      if(this.num1>=3) this.num1=0
      this.num1=index
      this.cate()
     },
     radar(){
        var myChart = echarts.init(this.$refs.aLeft)
        var option;
      option = {
         tooltip:{
    show:true,  // 鼠标经过显示提示框组件 
    position:['60%','10%'], // 修改提示框组件位置可以用百分比,也可以用数字
  },
      radar: {
         indicator: [
            { name: '机场', max: 100 },
            { name: '商场', max: 100 },
            { name: '火车站', max: 100 },
            { name: '汽车站', max: 100 },
            { name: '地铁', max: 100 },
         ],
         center:['50%','50%'],  // 调整雷达图位置,
         radius:'40%',
         shape: 'circle',
         splitNumber: 4,
         axisName: {
            color: '#4c9bfd',
            fontSize:9
         },
         splitLine: {
            lineStyle: {
            color: 'rgba(225,255,255,.5)'
            }
         },
         splitArea: {
            show: false
         },
         axisLine: {
            lineStyle: {
            color: 'rgba(225,255,255,.5)'
            }
         }
      },
      series: [
         {
            name: '武汉',
            type: 'radar',
            lineStyle: {
               normal:{
                  color:'#fff',
                  width: 1,
                  opacity: 0.5
               }
            },
            data: [[90,19,56,11,34]],
             symbol: 'circle', // 雷达图区域做标记(小圆点)
             symbolSize:5, // 标记小圆点大小
             itemStyle:{
              color:'#fff'  // 设置标记小圆点颜色
             },
        label:{  
            show:true,  // 显示小圆点相关数据
            color:'#fff',  // 设置小圆点数据颜色
            fontSize:6  // 设置小圆点数据字体大小
        },
            areaStyle: {
             color:'rgba(238,197,102,.6)'  
            }
         },
      ]
      };
      option && myChart.setOption(option);
     },
     pies(){
       var myChart = echarts.init(this.$refs.bRight);
         var option;
         option = {
         series: [
            {
               name: '统计',
               type: 'pie',
               radius: ['70%', '80%'],
               center: ['50%', '70%'],
               labelLine: {
               show: false
               },
               startAngle:180,
               data: [
                  { value: 100,
                   itemStyle:{  // 设置颜色渐变 
                     color: new echarts.graphic.LinearGradient(
                     0,
                     0,
                     0,
                     1,
                     [{offset:0,color:'#00c9e0'},{offset:1,color:'#005fc1'}])
                 } 
               }, 
               { value: 100,itemStyle:{color:'#12274d'} }, 
               { value: 200,itemStyle:{color:'transparent'} }]
            }
         ]
         };
    option && myChart.setOption(option);
     },
     mouse(index){
        this.hotIndex = index
     },
     set(){
        setInterval(()=>{
          if(this.hotIndex===4){
             return this.hotIndex = 0
          }
          this.hotIndex++;
        },1000)
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
   .content-center .contentCenterright .content-center{
      height: 90px;
      position: relative;
      right: 12px;
   }
   .content-center .contentCenterright .content-center .centent{
      position: absolute;
      top:-51px;
      bottom: -20px;
      right:-38px;
      left:-132px;
      padding-top: 10px;
      padding-left: 38px;
   }
   .content-center .contentCenterright .content-center .centent h2 {
      font-size: 12px;
      font-weight: normal;
      letter-spacing: 1px;
      color:#fff;
      padding-right: 10px;
      border-right: 2px solid #56d9f0;
         }
   .content-center .contentCenterright .content-center .centent div {
      display: flex;
   }
   .content-center .contentCenterright .content-center .centent section{
      padding-left: 10px;
   }
   .content-center .contentCenterright .content-center .centent section a {
      display: inline-block;
      margin-top: 8px;
      width: 27px;
      text-align: center;
      margin-right: 22px;
      text-decoration: none;
      color:#526986;
   }
   .content-center .contentCenterright .content-center .centent section a:last-of-type{
      margin-right: 0;  
   }
   .content-center .contentCenterright .content-center .centent .text{
      font-size:12px;
      color: #526986;
      position: absolute;
      z-index: 99;
   }
  .content-center .contentCenterright .content-center .centent .bottom{
      height:97px;
      margin-right:10px;
  }
  .bg{
     background: #6691ff;
     color:#fff !important;
  }
 .content-center .contentCenterright .content-wrap {
    position: relative;
    right:10px;
    height: 60px;
 }
 .content-center .contentCenterright .content-wrap{
    display: flex;
 }
 .content-center .contentCenterright .content-wrap .wrap-left,.wrap-right{
    position: relative;
    height: 100%;
 }
 .content-center .contentCenterright .content-wrap .wrap-left .wrap,.wrap-right .wrap{
    position: absolute;
    top:-45px;
    right:-38px;
    left:-132px;
    bottom: -20px;
 }
 .content-center .contentCenterright .content-wrap .wrap-left .wrap h2{
    position: absolute;
    top:-5px;
    left:15px;
    font-weight: normal;
    font-size:9px;
    color:#fff
 }
 .content-center .contentCenterright .content-wrap .wrap-left .wrap section{
    height: 100%;
 }
 .content-center .contentCenterright .content-wrap .wrap-right .wrap h3{
   font-weight: normal;
   font-size:9px;
   position: absolute;
   top:-5px;
   left:15px;
   color:#fff;
 }
 .content-center .contentCenterright .content-wrap .wrap-right .wrap section {
    height: 80px;
    
 }
 .content-center .contentCenterright .content-wrap .wrap-right .wrap .flex{
    display: flex;

 }
 .content-center .contentCenterright .content-wrap .wrap-right .wrap .bottomLeft{
    font-size:9px;
    color: #fff;
    display: flex;
    flex-direction: column;
    margin-left: 15px;
    align-items: center;
 } 
 .content-center .contentCenterright .content-wrap .wrap-right .wrap .bottomRight{
    font-size:2px;
    color:#fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-left:35px;
 }
 .content-center .contentCenterright .content-wrap .wrap-right .wrap .abs{
    position: absolute;
    left:72px;
    top:43px;
    font-size:9px;
    color:#fff;
 }
.content-center .contentCenterright .content-after {
   margin-top: 80px;
   height: 75px;
   position: relative;
   right: 10px;
}
.content-center .contentCenterright .content-after .after {
   position: absolute;
   top: -51px;
   right: -38px;
   left: -132px;
   bottom: -20px;
   padding:10px;
   display: flex;
}
.content-center .contentCenterright .content-after .after .after-left {
   width:120px;
   height: 100%;
   text-align: center;
}
.content-center .contentCenterright .content-after .after .after-left h3 {
   font-size:15px;
   font-weight: 600;
   color:#fff;
   text-align: left;
   margin-left:20px;
   margin-bottom: 7px;
   margin-top: 0;
}
.content-center .contentCenterright .content-after .after .after-left ul {
   list-style: none;
   margin:0;
   padding:0;
   color:#7291ff
}
.content-center .contentCenterright .content-after .after .after-left ul li {
  line-height: 29px;
}
.content-center .contentCenterright .content-after .after .after-left ul span:nth-of-type(1){
   margin-right:15px
}
.content-center .contentCenterright .content-after .after .after-right{
   flex: 1;
}
.content-center .contentCenterright .content-after .after .after-right-top {
   display: flex;
   justify-content: space-around;
}
.content-center .contentCenterright .content-after .after .after-right-top h3{
  color:#fff;
  font-size: 15px;
  margin:0;
  margin-bottom: 10px;
  margin-left:-15px
}
.content-center .contentCenterright .content-after .after .after-right-top span{
   color:#479ce7;
   font-size: 12px;
}
.content-center .contentCenterright .content-after .after .after-right-content-left ul{
   list-style: none;
   margin:0;
   padding:0;
   margin-top:-10px;
   padding-left:15px;
}
.content-center .contentCenterright .content-after .after .after-right-content{
   display: flex;
}
.content-center .contentCenterright .content-after .after .after-right-content-left ul li span{
   font-size:10px;
   color:#617cd2;
   cursor: pointer;
}
.content-center .contentCenterright .content-after .after .after-right-content-left ul li:hover{
   background: #040c2c;
}
.content-center .contentCenterright .content-after .after .after-right-content-right ul{
   list-style: none;
   margin: 0;
   padding: 0;
   margin-top:-6px;
   padding-left:10px;
   background: #040c2c;
}
.content-center .contentCenterright .content-after .after .after-right-content-right ul li {
   font-size:10px;
   color:#617cd2
}
.a{
   background: #040c2c;
}
</style>
