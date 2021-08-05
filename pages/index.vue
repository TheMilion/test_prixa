<template>
  <div style="background-color:#f2f2f2">
   <div class="box">
    </div>
    <div class="main">
      <div style="display:flex;justify-content:space-between">
        <span style="font-size:12pt;font-weight:800">Saldo Punti</span>
        <span style="font-size:14pt;font-weight:800">680</span>
      </div>
      <div style="background-color:#f3f2f5;margin-top:10px;margin-bottom:10px;height:3px" />
      <div style="display:flex;justify-content: space-around;">
        <div style="display:flex;flex-direction: column;align-items: center;">
          <img src="test.png" style="width:40px;height:40px">
          <span style="padding-top:5px;font-size:8pt;font-weight:1000">Richiedi</span>
        </div>
        <div style="display:flex;flex-direction: column;align-items: center;">
          <img src="test3.png" style="width:40px;height:40px">
          <span style="padding-top:5px;font-size:8pt;font-weight:1000">Trasferisci</span>
        </div>
        <div style="display:flex;flex-direction: column;align-items: center;">
          <img src="test.png" style="width:40px;height:40px">
          <span style="padding-top:5px;font-size:8pt;font-weight:1000">Attività</span>
        </div>
        <div style="display:flex;flex-direction: column;align-items: center;">
          <img src="test3.png" style="width:40px;height:40px">
          <span style="padding-top:5px;font-size:8pt;font-weight:1000">QR Code</span>
        </div>
      </div>
    </div>
    <div style="margin-top:25px">
      <div class="ml-25 mr-25" style="display:flex;flex-direction:column">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <span style="font-size:15pt;font-weight:800">Catalogo Premi</span>
          <!-- <van-icon name="expand-o" /> -->
        </div>
        <span style="font-size:8pt;font-weight:800; color:#8a898c">12 Categorie Disponibili</span>
      </div>
      <van-swipe @change="onChangeCatalogo" style="margin-bottom:15px" :loop="false" :width="290">
        <template #indicator>
          <div></div>
        </template>
        <van-swipe-item v-for="(item,indexCat) in arrCatalogo" :key="indexCat" >
          <div :class="currSwipeCatalogoPosition == 0 && indexCat == 0 ? 'ml-15' : currSwipeCatalogoPosition == arrCatalogo.length-1 && indexCat == arrCatalogo.length-1 ? 'mr-15' : 'ml-10 mr-10' " style="display:flex;justify-content:space-between;padding-top:20px">
            <van-grid :column-num="3" :gutter="8">
              <van-grid-item v-for="(value,indexVal) in item" :key="value.title+'_'+indexVal">
                <template #icon>
                  <img :src="value.img" style="width:30px;height:30px">
                </template>
                <template #text>
                  <span style="padding-top:5px;font-size:8pt;font-weight:1000">{{value.title}}</span>
                </template>
              </van-grid-item>
            </van-grid>
          </div>
        </van-swipe-item>
      </van-swipe>
    </div>

    <div>
      <div class="ml-25 mr-25" style="display:flex;flex-direction:column">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <span style="font-size:15pt;font-weight:800">Esercizi Convenzionati</span>
          <van-icon name="expand-o" />
        </div>
        <span style="font-size:8pt;font-weight:800; color:#8a898c">30 Esercizi disponibili</span>
      </div>
      <van-swipe @change="onChangeEsercizi" style="margin-bottom:205px" :loop="false" :width="282">
        <template #indicator>
          <div></div>
        </template>
        <van-swipe-item v-for="(item,indexArr) in arr" :key="item.title+'_'+indexArr" >
        <div  :class="currSwipeEserciziPosition== 0 ? 'card ml-25' : currSwipeEserciziPosition == 3 ? 'card mr-25' : 'card ml-25' ">
          <van-image
            fit="cover"
            width="100%"
            height="110px"
            :src="item.img"
          />
          <transition name="van-slide-left">
            <div style="padding-left:10px;padding-top:5px">
              <span style="font-size:12pt;font-weight:800">{{item.title}}</span><br>
              <span style="font-size:8pt;font-weight:800; color:#8a898c">{{item.descrizione}}</span>
            </div>
          </transition>
            <!-- <div style="border-top-left-radius: 10px;border-top-right-radius: 10px;background-color:red;height:110px">
            </div> -->
            <div style="height:40px;display:flex;justify-content: center;align-items: center;">
              <span style="font-size:10pt;font-weight:800;color:red">Vai Ora</span>
            </div>
          </div>
        </van-swipe-item>
      </van-swipe>
    </div>
  </div>
</template>

<script>

export default {
  layout: 'default',

  data() {
    return {
      arrCatalogo: [
        [{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"}],
        [{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"},{img:"test.png",title:"Biancheria"}]],
      arr: [{img:"negozi/daversa.png",title:"Farmacia D'Aversa Napoli",descrizione: "Descrizione attivita"},{img:"negozi/gcm.png",title:"GCM Mugnano",descrizione: "Descrizione attivita"},{img:"negozi/gcm.png",title:"GCM Mugnano",descrizione: "Descrizione attivita"},{img:"negozi/gcm.png",title:"GCM Mugnano",descrizione: "Descrizione attivita"}],
      currSwipeEserciziPosition : 0,
      currSwipeCatalogoPosition : 0
    }
  },

  methods: {
    onChangeEsercizi(val){
      this.currSwipeEserciziPosition = val
      console.log("val",val)
    },
    onChangeCatalogo(val){
      this.currSwipeCatalogoPosition = val
      console.log("val",val)
    }
  }
}
</script>

<style>
.van-image .van-image__img{
  border-top-left-radius: 10px !important;border-top-right-radius: 10px !important
} 
body{
  height:100%;
  background-color:#f2f2f2
}
.card{
  background-color:white;height:200px;margin-bottom:50px;margin-top:10px;border-radius:10px
}
.ml-10{
  margin-left:10px
}
.mr-10{
  margin-right: 10px;
}
.ml-15{
  margin-left:15px
}
.mr-15{
  margin-right: 15px;
}
.ml-25{
  margin-left:25px
}
.mr-25{
  margin-right: 25px;
}

.mr-35{
  margin-right: 35px;
}
.pr-3{
  margin-right:30px
}

.box {
  height: 200px;
  border-radius: 5px;
  background: #4c609f;
  position: relative;
  overflow: hidden;
}
.content{
  margin:25px
}
.main{
  border-radius: 5px;
  height:100px;
  background-color:white;
  position: relative;
  margin-top:-35px;
  margin-left:25px;
  margin-right:25px;
  padding:20px
}

.van-grid-item__content{
  border-radius:10px
}
.van-grid{
  /* padding-left: 0px !important */
}


</style>
