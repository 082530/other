<template>
  <div class="page1">
    <div class="le">
      <div>
        <p class="nav">
          <span v-for="(text,key) in nav_text" :class="nav_state==key?'act_nav':''" @click="lick(key)">{{text}}</span>
        </p>
      </div>
      <div v-if="nav_state==0" class="list1">
        <table>
          <thead>
          <tr>
            <td>商品名称</td>
            <td>数量</td>
            <td>金额</td>
            <td>操作</td>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(item,key) in shopping">
            <td>{{item.shop}}</td>
            <td>{{item.num}}</td>
            <td>{{item.price}}元</td>
            <td><span @click="remove(key)">删除</span><span @click="add(key)">添加</span></td>
          </tr>
          </tbody>
          <tfoot>
          <tr>
            <td colspan="4">数量：<span>{{len}}份</span>共计：<span>{{total}}元</span></td>
          </tr>
          </tfoot>
        </table>
        <p>
          <button @click="shopping=[]">清空</button>
          <button>结算</button>
        </p>
      </div>
      <div v-if="nav_state==1">
        <p>这是下单页面</p>
      </div>
      <div v-if="nav_state==2">
        <p>这是结算页面</p>
      </div>
    </div>
    <div class="ri">
      <div>
        <p>常用商品</p>
        <div class="shop_list">
          <span v-for="(shop,key) in shop_list" @click="buy(key)">{{shop.shop}}<span>￥{{shop.price}}元</span></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorl',
  data () {
    return {
      nav_state: 0,
      nav_text: ['点餐', '下单', '结算'],
      shop_list: [
        {'num': 1, 'shop': '香辣鸡腿堡', 'price': 11},
        {'num': 1, 'shop': '香辣鸡腿', 'price': 12},
        {'num': 1, 'shop': '香辣鸡', 'price': 13},
        {'num': 1, 'shop': '鸡腿堡', 'price': 14},
        {'num': 1, 'shop': '香鸡腿堡', 'price': 15},
        {'num': 1, 'shop': '香腿堡', 'price': 16},
        {'num': 1, 'shop': '香鸡腿', 'price': 17},
        {'num': 1, 'shop': '辣鸡腿堡', 'price': 20},
        {'num': 1, 'shop': '辣鸡腿', 'price': 10},
        {'num': 1, 'shop': '辣鸡', 'price': 8},
        {'num': 1, 'shop': '香辣鸡腿', 'price': 5},
        {'num': 1, 'shop': '辣鸡堡', 'price': 6}
      ],
      shopping: [],
      total: 0,
      len: 0
    }
  },
  methods: {
    lick: function (i) {
      this.nav_state = i;
    },
    buy: function (i) {
      let w=1;
      for (let ii = 0,length = this.shopping.length; ii < length; ii++) {
        if (this.shopping[ii].shop == this.shop_list[i].shop){
          this.shopping[ii].num++;
          w=0;
        }
      }
      if (!this.shopping.length || w) {
        this.shopping.push(this.shop_list[i]);
      }

    },
    remove: function (i) {
      let n=this.shopping[i].num;
      if(n<2)this.shopping.splice(i, 1);
      else this.shopping[i].num--

    },
    add: function (i) {
      this.shopping[i].num++;
    }
  },
  updated: function () {
    let price = 0;
    let len = 0;
    for (let i = 0, length = this.shopping.length; i < length; i++) {
      price += parseFloat(this.shopping[i].price*this.shopping[i].num)
      len += parseInt(this.shopping[i].num)
    } ;
    this.total = price;
    this.len = len
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "../assets/page1.css";
</style>
