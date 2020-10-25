<!--
 描述: 祈福模板
 作者: yijia
 日期: 2020-10-25
-->

<template>
   <div>
    <input
      autocomplete="off"
      type="text"
      class="input"
      v-model="bestWish"
      placeholder="请输入祈福语句"
      />
    <Button
      type="primary"
      @click.stop="goWish">
      立即祈福
    </Button>
    <span id="time"></span>
    <span id="count">0</span>
    <p>心想事成</p>
    <div id="id"></div>
    
   </div>
</template>

<script>

export default {
  name: 'wishing',
  components: {

  },
  data() {
    return {
      bestWish : '一甲(王超)贷款顺利',
      timer: ''
    }
  },
  mounted() {
    this.getCookie();
       setInterval(function () {console.log("一甲(王超)贷款顺利")} ,1000)
      
  },
  methods: {
   

    // 立即祈福
    wishing() {
        document.getElementById('time').innerText=new Date()
        let text=document.getElementById('id').innerText
        let num=document.getElementById('count').innerText
            num = num*1 + 1
        document.getElementById('count').innerText = num  
        text+= ' ' + this.bestWish + ' ' 
        document.getElementById('id').innerText=text
    },
    goWish() {
      //点击祈福 清理上一个定时器 和祈福内容 并新开一个定时器
      // let timer
      clearInterval(this.timer)
      document.getElementById('id').innerText= ''
      document.getElementById('count').innerText= ''
      this.timer = setInterval(
        ()=>{
          this.wishing()
        }
        ,1000)

    }
  }
};
</script>

<style lang="scss" scoped>

</style>
