<template>
  <div id="app">
    <header>
      <div class="header__content">
        <div class="header__content__area">
          <div class="header__content__left">
            <h1 class="header__content__logo">
              Vue.js
            </h1>
          </div>
          <div class="header__content__right">
            <h1 class="header__content__app">
              自動車 見積もりシミュレータ
            </h1>
          </div>
        </div>
      </div>
    </header>
    <div class="grade">
      <div class="grade__left">
        <span class="grade__left__logo">
          グレードを変更する
        </span>
        <select class="grade__left__lank" >
          
        </select>
        <input type="radio" name="grade" id="g" class="grade__input" v-model="opt4_use" :value="4" @click="clear3" hecked="checked">
          <label for="g" class="grade__label">G</label>
        <input type="radio" name="grade"  id="gt" class="grade__input" v-model="opt5_use" value="5" @click="clear4">
          <label for="gt" class="grade__label">GT</label>
        <input type="radio" name="grade" id="gtl" class="grade__input" v-model="opt6_use" value="6" @click="clear5">
          <label for="gtl" class="grade__label">GT-Limited</label>
        <div class="grade__left__price" v-if="opt4_use == '4'">
          <span class="grade__left__price__span">総額 2,671,900 円</span> 
        </div>
        <div class="grade__left__price" v-if="opt5_use == '5'">
          <span class="grade__left__price__span">総額 3,037,100 円</span> 
        </div>
        <div class="grade__left__price" v-if="opt6_use == '6'">
          <span class="grade__left__price__span">総額 3,242,800 円</span> 
        </div>
      </div>
      <div class="grade__right">
        <div class="color__content__left__body" v-if="isActive == '3'">
          <img src="../assets/images/８６red part2.jpg" alt="" >
        </div>
        <div class="color__content__left__body" v-if="isActive == '2'">
          <img src="../assets/images/８６dark gray.jpg" alt="" >     
        </div>    
        <div class="color__content__left__body" v-if="opt1_use == 'true'">
          <img src="../assets/images/90A67D6C-6095-4FBC-AB12-B21297D75D35_1_105_c.jpeg" alt="" >
        </div>
      </div>
    </div>
    <div class="estimation">
      <div class="estimation__top">
        見積もり詳細
      </div>
      <div class="estimation__bottom">
        グレード、カラー、オプションなど お見積りプラン内容の変更が可能です。
      </div>
    </div>
    <div class="color">
      <div  class="color__head">
        <div class="color__head__top">
          車両概要
        </div>
        <div class="color__head__body">
          
        </div>       
        <div class="color__head__bottom">
          燃費：11.8kml/駆動：2WD  FR  定員：４名 総排気量：2.0L 
        </div>       
      </div>
      <div class="color__content">
        <div class="color__content__left">
          <div class="color__content__left__title">
            ボディカラー
          </div>
          <div class="color__content__left__body" v-if="isActive == '2'">
            <img src="../assets/images/８６dark gray.jpg" alt="" >
          </div>
          <span v-if="isActive == '2'">クリスタルブラックシリカ + 0円</span>
          <div class="color__content__left__body" v-if="isActive == '3'">
            <img src="../assets/images/８６red part2.jpg" alt="" >     
          </div>
           <span v-if="isActive == '3'">ピュアレッド + 0円</span>       
          <div class="color__content__left__body" v-if="opt1_use == 'true'">
            <img src="../assets/images/90A67D6C-6095-4FBC-AB12-B21297D75D35_1_105_c.jpeg" alt="" >
          </div>
          <span v-if="opt1_use == 'true'">クリスタルホワイトパール + 33,000円</span>
          <div class="color__content__left__price">
            <div class="color__content__left__color--option">
               
            </div>
            <div class="color__content__left__color--select">
              <input type='radio' name="gender" class="white" v-model="opt1_use" value="true" @click="clear2"/>
              <input type='radio' name="gender" class="black" v-model="isActive" :value="2" @click="clear"/>
              <input type='radio' name="gender" class="red" v-model="isActive" :value="3" @click="clear"/>
            </div>
          </div>
        </div>
        <div class="color__content__right">
          <div class="color__content__right__title">
            インテリアカラー
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '1'">
            <img src="../assets/images/E9B4A4A9-A66F-48AC-A6F4-7EF1EE2F7D87_1_105_c.jpeg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '2'">
            <img src="../assets/images/ハンドル赤.jpg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '3'">
            <img src="../assets/images/ハンドルオレンジ.jpg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '4' " >
            <img src="../assets/images/D5B58C24-0DE1-46C6-A338-B2FA23E15018_1_105_c.jpeg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '5'">
            <img src="../assets/images/座席オレンジ.jpg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__image" v-if="isActive3 == '6'">
            <img src="../assets/images/seat orange.jpg" alt="" class="color__content__right__image--seat ">
          </div>
          <div class="color__content__right__price">
            <div class="color__content__right__button">
              <!-- <button class="color__content__right__button--in" @click="active">インパネ</button>
              <button class="color__content__right__button--seat" @click="active2">シート</button> -->
              <input type="radio" name="color" id="in" class="interior" v-model="isActive2" :value="1" @click="clear6">
                <label for="in" class="color__content__right__button--in" >インパネ</label>
              <input type="radio" name="color" id="seat" class="interior" v-model="isActive2" :value="2" @click="clear6">
                <label for="seat" class="color__content__right__button--seat">シート</label>
            </div>
          </div>
          <div class="color__content__right__color--option" v-if="isActive3 == '1' || isActive3 == '4'" >
            ブラック + 0円
          </div>
          <div class="color__content__right__color--option" v-if="isActive3 == '2' || isActive3 == '5'">
            レッド + 0円
          </div>
          <div class="color__content__right__color--option" v-if="isActive3 == '3' || isActive3 == '6'">
            オレンジ + 0円
          </div>
          <div class="color__content__right__color--select">
            <input type='radio' name="inpane" class="black__seat" v-if="isActive2 == '1'" v-model="isActive3" :value="1" @click="clear7"/>
            <input type='radio' name="inpane" class="red__seat" v-if="isActive2 == '1'" v-model="isActive3" :value="2" @click="clear7"/>
            <input type='radio' name="inpane" class="orange__seat" v-if="isActive2 == '1'" v-model="isActive3" :value="3" @click="clear7"/>
            <input type='radio' name="seat2" class="black__seat" v-if="isActive2 == '2'" v-model="isActive3" :value="4" @click="clear7">
            <input type='radio' name="seat2" class="red__seat" v-if="isActive2 == '2'" v-model="isActive3" :value="5" @click="clear7">
            <input type='radio' name="seat2" class="orange__seat" v-if="isActive2 == '2'" v-model="isActive3" :value="6" @click="clear7">
          </div>
        </div>
      </div>
    </div>
    <div class="option">
      <div class="option__content">
        <div class="option__content__wheel">
          <div class="option__content__wheel__left">
            <input type="checkbox" name="wheel" id="" calss="option__content__wheel__check" v-model="opt2_use">
          </div>
          <div class="option__content__wheel__right">
            <div class="option__content__wheel__right--top">
              スペアタイヤ（応急用タイヤ）
            </div>
            <div class="option__content__wheel__right--bottom">
              11,000円 
            </div>
          </div>
        </div>
      </div>
      <div class="option__content">
        <div class="option__content__cold">
          <div class="option__content__cold__left">
            <input type="checkbox" name="cold" id="" v-model="opt3_use">
          </div>
          <div class="option__content__cold__right">
            <div class="option__content__cold__right--top">
              寒冷地仕様（大型バッテリー）
            </div>
            <div class="option__content__cold__right--bottom">
              6,600円
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="total">
      <div class="total__price">
        <div class="total__price__left">
          <div class="total__price__left__title">
            お支払い総額
          </div>
        </div>
        <div class="total__price__right">
          <div class="total__price__right__box">
            合計
          </div>
          <span class="total__price__right__fee" :value="taxedTotalPrice">
             {{ taxedTotalPrice | number_format }} 円(税込)
          </span>
        </div>
      </div>
      <div class="total__car">
        <div class="total__car__left">
          <div class="total__car__left__title">
            車両本体価格
          </div>
        </div>
        <div class="total__car__right">
          <div class="total__car__right__box">
            合計
          </div>
          <span class="total__car__right__fee" :value="taxedBasePrice">
            {{ taxedBasePrice | number_format}}円(税込)
          </span>
        </div>
      </div>
      <div class="total__option">
        <div class="total__option__left">
          <div class="total__option__left__title">
            選択オプション
          </div>
        </div>
        <div>
          <div v-if="opt2_use">
            スペアタイヤ
          </div>
          <div v-if="opt3_use">
            寒冷地仕様 (大型バッテリー)
          </div>
          <div v-if="opt1_use == 'true'">
            ボディカラー：クリスタルホワイトパール
          </div>
          <div v-if="isActive == '2'">
            ボディカラー：クリスタルブラックシリカ
          </div>
          <div v-if="isActive == '3'">
            ボディカラー：ピュアレッド
          </div>
          <div v-if="isActive3 == '1' || isActive3 == '4'">
            インテリアカラー：ブラック
          </div>
          <div v-if="isActive3 == '2' || isActive3 == '5'">
            インテリアカラー：レッド
          </div>
          <div v-if="isActive3 == '3' || isActive3 == '6'">
            インテリアカラー：オレンジ
          </div>
        </div>
        <div class="total__option__right">
          <div class="total__option__right__box">
            合計
          </div>
          <span class="total__option__right__fee">
            <div class="form-control text-right" v-bind:value="taxedOptPrice" >
              {{ taxedOptPrice | number_format }}円(税込)
            </div>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import './filter.js';

export default {
  name: 'Product',
  props: {
    msg: String
  },
  data: function() {
    return {
      selectedKey: '',
      isActive: '2',
      isActive2: 1,
      isActive3: 1,
      taxRate: 0.08,
      optPrice: 0,
      opt1_use: false,              
      opt1_price: 33000,            
      opt2_use: false,              
      opt2_price: 11000,             
      opt3_use: false,              
      opt3_price: 6600,
      opt4_use: '4',              
      opt4_price: 2671900,
      opt5_use: false,              
      opt5_price: 3037100,
      opt6_use: false,              
      opt6_price: 3242800,
    }
  },
  methods:{
    selected: function(){
        this.selectedItem = this.items[this.selectedKey];
    },
    incTax: function(untaxed) {
      return Math.floor(untaxed * (1 + this.taxRate));    
    },
    clear: function () {
      this.opt1_use = ''
    },
    clear2: function () {
      this.isActive = ''
    },
    clear3: function () {
      this.opt5_use = ''
      this.opt6_use = ''
    },
    clear4: function () {
      this.opt4_use = ''
      this.opt6_use = ''
    },
    clear5: function () {
      this.opt5_use = ''
      this.opt4_use = ''
    },
    clear6: function () {
      this.isActive2 = ''
    },
    clear7: function () {
      this.isActive3 = ''
    },
    active: function () {
      this.isActive3 = ''
      this.isActive2 = !this.isActive2
    },
    active2: function () {
      this.isActive2 = ''
      this.isActive3 = !this.isActive3
    }
  },
  computed: {
    taxedOpt1: function() {
      return this.incTax(this.opt1_price);
    },
    taxedOpt2: function() {
      return this.incTax(this.opt2_price);
    },
    taxedOpt3: function() {
      return this.incTax(this.opt3_price);
    },
    taxedOpt4: function() {
      return this.incTax(this.opt4_price);
    },
    taxedOpt5: function() {
      return this.incTax(this.opt5_price);
    },
    taxedOpt6: function() {
      return this.incTax(this.opt6_price);
    },
    taxedOptPrice: function() {
      // オプション料金
      var optPrice = 0;
      if (this.opt1_use) { optPrice += this.opt1_price; }
      if (this.opt2_use) { optPrice += this.opt2_price; }
      if (this.opt3_use) { optPrice += this.opt3_price; }
      return this.incTax(optPrice);
    },
    taxedBasePrice: function() {
      var addPrice = 0;
      if (this.opt4_use) { addPrice += this.opt4_price; }
      if (this.opt5_use) { addPrice += this.opt5_price; }
      if (this.opt6_use) { addPrice += this.opt6_price; }
      return this.incTax(addPrice);
    },
    taxedTotalPrice: function() {
      return (this.taxedBasePrice + this.taxedOptPrice);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.body {
  padding-bottom: 180px;
  margin: -8px;
  position: relative;
  
}

.header__content {
  background-color: aliceblue;
  z-index: 120;
  height: auto;
  border-bottom: none;
}

.header__content__area {
  width: 920px;
  margin: 0 auto;
  display: flex;
  justify-content: space-around;
}

.grade {
  display: flex;
  justify-content: space-between;
  padding-top: 36px;
  width: 928px;
  margin: 0 auto;
  margin-bottom: 140px;
}
.grade__left {
  margin-bottom: 30px;
  text-align: left;
  width: 700px;
}

.grade__left__logo {
  font-weight: bold;
  font-size: 20px;
  display: block;
  padding-bottom: 40px;
}

.grade__left__lank {
  font-weight: bold;
  margin-top: 10px;
  display: none;
}

.grade__left__price {
  margin-top: 30px;
  font-size: 20px;
}

.grade__left__price__span {
  font-weight: bold;
  font-size: 40px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.grade__right {
  width: calc(50% - 30px);
}

.grade__right__image {
  
}

.estimation {
  text-align: left;
  width: 928px;
  margin: 0 auto;
  border-top: solid 1px ;
  border-color: gainsboro;
  box-shadow: gray;
}

.estimation__top {
  font-weight: bold;
  font-size: 22px;
  margin-top: 20px;
}

.estimation__bottom {
font-size: 18px;
margin-top: 15px;
}

.color {
  width: 928px;
  margin: 0 auto;
  text-align: left;
  margin-top: 30px ;
  margin-bottom: 100px;
  border: 1px solid #d3d3d3;
  box-shadow: 1px 2px 3px #d3d3d3;
}

.color__head {
  
}

.color__head__top {
  font-weight: bold;
  font-size: 30px;
  background: gray;
  color: white;
  padding: 20px 0px 20px 80px;
}

.color__head__body {
  font-size: 18px;
  padding: 30px 0px 0px 40px;
  
}

.color__head__bottom {
  font-size: 18px;
  padding: 10px 0px 10px 40px;
  margin-bottom: 60px;
  border-bottom: 1px dotted #ccc;
}

.color__content {
  display: flex;
  justify-content: space-between;
  padding-bottom: 90px;
}

.color__content__left {
  padding-left: 40px;
  width: 48%;
}
.color__content__left__title {
  font-weight: bold;
  margin-bottom: 60px;
}

.color__content__left__body {
  margin-bottom: 120px;
}

.color__content__left__price {
  font-weight: bold;
}

.color__content__left__color--option {
  margin-bottom: 35px;
}
.color__content__left__color--select {

}

.color__content__right {
  width: 48%;
  padding-right: 40px;
}

.color__content__right__image--seat {
  display: block;
  margin: 0 auto;
}

.color__content__right__title {
  font-weight: bold;
  margin-bottom: 60px;
}
.color__content__right__body {
  margin-bottom: 120px;
}
.color__content__right__price {
  
}

.color__content__right__button {
  
  
}

.color__content__right__button--in {
  width: 50%;
  height: 50px;
  border-radius: 0;
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none;
  border: 0;
  border-radius: 0;
  background: white;
  border-bottom: 1px solid ;
  margin-top: 50px;
  display: inline-block;
  text-align: center;
  line-height: 50px;
}

.color__content__right__button--in:focus {
  outline: none;
  border-bottom: 2px solid red;
   background: #ccc;
}

.color__content__right__button--seat {
  display: inline-block;
  width: 50%;
  height: 50px;
  border-radius: 0;
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none;
  border: 0;
  border-radius: 0;
  background: white;
  border-bottom: 1px solid ;
  text-align: center;
  line-height: 50px;
}

.color__content__right__button--seat:focus {
  outline: none;
  border-bottom: 2px solid red;
   background: #ccc;
}

.color__content__right__color--option {
  font-weight: bold;
  margin-top: 50px;
}

.color__content__right__color--select {
  margin-top: 35px;
}

.white {
}

.black {
  margin-left: 57px;
}

.red {
  margin-left: 57px;
}
.black__seat {
  
}

.red__seat {
  margin-left: 57px;
}
.orange__seat {
  margin-left: 57px;
}

input.white {
  width: 1.5em;
  height: 1.5em;
  
}

input.black {
  width: 1.5em;
  height: 1.5em;
}

input.red {
  width: 1.5em;
  height: 1.5em;
}

input.orange__seat {
  width: 1.5em;
  height: 1.5em;
}

input.black__seat {
  width: 1.5em;
  height: 1.5em;
}

input.red__seat {
  width: 1.5em;
  height: 1.5em;
}

input[type='radio'].white:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color: rgb(241, 235, 235);
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}
input[type='radio'].black:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color: rgb(56, 52, 52);
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}
input[type='radio'].red:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color: red;
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}
input[type='radio'].red__seat:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color: red;
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}
input[type='radio'].black__seat:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color:black;
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}
input[type='radio'].orange__seat:after {
        width: 26px;
        height: 26px;
        border-radius: 15px;
        
        left: -1px;
        position: relative;
        background-color: orange;
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid rgb(161, 158, 158);
}

input[type='radio'].white:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}
input[type='radio'].black:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}
input[type='radio'].red:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}
input[type='radio'].orange__seat:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}
input[type='radio'].black__seat:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}
input[type='radio'].red__seat:checked:after {
    width: 28px;
    height: 28px;
    border-radius: 15px;
    top: -1px;
    left: -1px;
    position: relative;
    // background-color: #ffa500;
    content: '';
    display: inline-block;
    visibility: visible;
    border: 2px solid skyblue;
    
}

.grade__label {
  display: block; 
  float: left; 
  margin: 5px;
  width: 100px; 
  height: 20px; 
  padding-left: 5px; 
  padding-right: 5px; 
  color: #646060; 
  text-align: center; 
  line-height: 20px; 
  cursor: pointer; 
  border: 2px solid #006DD9;
  border-radius: 5px; 
}
input[type=radio].grade__input {
  display: none; 
  
}
input[type="radio"].grade__input:checked + .grade__label {
  background: #31A9EE;
  color: #ffffff; 
}

input[type=radio].interior {
    display: none;    
}
input[type="radio"].interior:checked + .color__content__right__button--in {
  outline: none;
  border-bottom: 2px solid red;
  background: #ccc;
}
input[type="radio"]:checked + .color__content__right__button--seat {
  outline: none;
  border-bottom: 2px solid red;
  background: #ccc;
}

.option__content {
  width: 928px;
  margin: 0 auto;
  border: 1px solid #d3d3d3;
  margin-top: 40px;
  background-color: #fff;
  box-shadow: 1px 2px 3px #d3d3d3;
  height: 100px;
}

.option__content__wheel {
  display: flex;
  justify-content: space-around;
  line-height: 50px;
  
}

.option__content__wheel__left {
  line-height: 100px; 
}

.option__content__wheel__right {
  padding-right: 170px;
}

.option__content__wheel__right--top {
  font-weight: bold;
  border-bottom:1px solid ;
}
.option__content__wheel__right--bottom {
  font-weight: bold;
}

.option__content__cold {
  display: flex;
  justify-content: space-around;
  line-height: 50px;
  
}

.option__content__cold__left {
  line-height: 100px; 
}

.option__content__cold__right {
  padding-right: 170px;
}

.option__content__cold__right--top {
  font-weight: bold;
  border-bottom:1px solid ;
}
.option__content__cold__right--bottom {
  font-weight: bold;
}

.total {
  border: 1px solid #d3d3d3;
  box-shadow: 1px 2px 3px #d3d3d3;
  margin-top: 24px;
  background-color: #fff;
  width: 928px;
  margin: 0 auto;
  margin-top: 100px;
  margin-bottom: 200px;
}

.total__price {
  display: flex;
  justify-content: space-around;
  border-bottom: 1px solid #d3d3d3;
  background: rgb(173, 171, 171);
}
.total__price__left { 
  height: 90px;
}
.total__price__left__title {
  line-height: 90px;
  font-weight: bold;
  font-size: 25px;
  color: #fff;
}
.total__price__right {
  display: flex;
}
.total__price__right__box {
  line-height: 90px;
  
  font-size: 25px;
  color: #fff;
  padding-right: 20px;
}
.total__price__right__fee {
  line-height: 90px;
  font-weight: bold;
  font-size: 25px;
  color: #fff;
  padding-right: 60px;
}

.total__car {
  display: flex;
  justify-content: space-around;
  border-bottom: 1px solid #d3d3d3;
  
}
.total__car__left { 
  height: 90px;
}
.total__car__left__title {
  line-height: 90px;
  font-weight: bold;
  font-size: 20px;
  
}
.total__car__right {
  display: flex;
}
.total__car__right__box {
  line-height: 90px;  
  font-size: 20px;  
  padding-right: 20px;
}
.total__car__right__fee {
  line-height: 90px;
  font-weight: bold;
  font-size: 20px;
  
  padding-right: 60px;
}

.total__option {
  display: flex;
  justify-content: space-around;
  border-bottom: 1px solid #d3d3d3;
  
}
.total__option__left { 
  height: 90px;
}
.total__option__left__title {
  line-height: 90px;
  font-weight: bold;
  font-size: 20px;
  
}
.total__option__right {
  display: flex;
}
.total__option__right__box {
  line-height: 90px;  
  font-size: 20px;  
  padding-right: 20px;
}
.total__option__right__fee {
  line-height: 90px;
  font-weight: bold;
  font-size: 20px;
  
  padding-right: 60px;
}

</style>
