<template>
    <div class="content">
       <div class="content-header"></div>
       <div class="content-center">
               <section class="contenCenterLeft">
                  <div class="left-data">
                     <div class="left-data-center">
                          <ul>
                             <li>1</li>
                             <li>2</li>
                             <li>3</li>
                             <li>4</li>
                          </ul>
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
        color: blue;
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
     .content-center .contenCenterLeft .left-data{
        position: relative;
        border: 15px solid transparent;
        border-width: 51px 38px 20px 132px;
        border-image-source: url('~@/assets/images/border.png');
        border-image-slice: 51 38 20 132;
        margin-left: 52px;
     }
     .content-center .contenCenterLeft .left-data .left-data-center{
        position: absolute;
        top: -50px;
        bottom: -20px;
        left:-132px;
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
     }
</style>
