<template>
    <div class="content">
       <div class="content-header"></div>
       <div class="content-center">
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
                               <section class="center-left">
                                  99
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
               <section class="contentCenterCen">2</section>
               <section class="contentCenterright">3</section>
       </div>
    </div> 
</template>
<script>
export default {
   data() {
      return {
         num:0,
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
         }]
      }
   },
   created(){
   },
   computed:{
   },
   methods:{
   },
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
        margin-right: 29px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li span:nth-of-type(2){
        overflow: hidden;
        width: 120px;
        white-space:nowrap;
        text-overflow:ellipsis;
        margin-left: 43px;
     }
     .content-center .contenCenterLeft .monitoring-center .monitoring-bottom .hover ul li span:nth-of-type(3){
        margin-left: 26px
     }
     @keyframes move{
        100%{
           transform: translateY(-50%);
        }
     }
    .content-center .contenCenterLeft .pie{
       height: 122px;
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
       color: pink;
       height: 125px;
       width: 360px;
       margin-top: -6px;
    }
    .content-center .contenCenterLeft .center .center-left{
       /* padding-right: 80px; */
       background: pink;
       width: 1000px;
    }
    .content-center .contenCenterLeft .center .center-right{
       margin-left: 20px;
       width: px !important; 
       display: flex;
       flex-direction: column;
       justify-content: space-around;
       align-items: center;
       background: blue;
       /* background: url('../assets/images/rect.png') no-repeat; */
       /* background-size: 100% 100%; */
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
</style>
