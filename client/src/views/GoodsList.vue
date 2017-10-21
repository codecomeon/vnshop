<template>
  <div>
    <nav-header></nav-header>
    <nav-bread>首页</nav-bread>
    <div class="accessory-result-page accessory-page">
      <div class="container">
        <div class="filter-nav">
          <span class="sortby">Sort by:</span>
          <a href="javascript:void(0)" class="default cur">Default</a>
          <a href="javascript:void(0)" class="price">Price <svg class="icon icon-arrow-short"><use xlink:href="#icon-arrow-short"></use></svg></a>
          <a href="javascript:void(0)" class="filterby stopPop">Filter by</a>
        </div>
        <div class="accessory-result">
          <!-- filter -->
          <div class="filter stopPop" id="filter">
            <dl class="filter-price">
              <dt>Price:</dt>
              <dd><a href="javascript:void(0)">All</a></dd>
              <dd>
                <a href="javascript:void(0)">0 - 100</a>
              </dd>
              <dd>
                <a href="javascript:void(0)">100 - 500</a>
              </dd>
              <dd>
                <a href="javascript:void(0)">500 - 1000</a>
              </dd>
              <dd>
                <a href="javascript:void(0)">1000 - 2000</a>
              </dd>
            </dl>
          </div>

          <!-- search result accessories list -->
          <div class="accessory-list-wrap">
            <div class="accessory-list col-4">
              <ul>
                <li v-for="(item,index) in list" :key="index">
                  <div class="pic">
                    <a href="#"><img :src="'/static/img/'+item.productImage" alt=""></a>
                  </div>
                  <div class="main">
                    <div class="name">{{item.productName}}</div>
                    <div class="price">{{item.salePrice}}</div>
                    <div class="btn-area">
                      <a href="javascript:;" class="btn btn--m">加入购物车</a>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
    <vn-footer></vn-footer>
    <!--<footer class="footer">-->
      <!--<div class="footer__wrap">-->
      <!--<div class="footer__secondary">-->
        <!--<div class="footer__inner">-->
          <!--<div class="footer__region">-->
            <!--<span>Region</span>-->
            <!--<select class="footer__region__select">-->
              <!--<option value="en-US">USA</option>-->
              <!--<option value="zh-CN">China</option>-->
              <!--<option value="in">India</option>-->
            <!--</select>-->
          <!--</div>-->
          <!--<div class="footer__secondary__nav">-->
            <!--<span>Copyright © 2017 Shudong All Rights Reserved.</span>-->
            <!--<a href="http://us.lemall.com/us/aboutUs.html">-->
              <!--About Us-->
            <!--</a>-->
            <!--<a href="http://us.lemall.com/us/termsofUse.html">-->
              <!--Terms &amp; Conditions-->
            <!--</a>-->
            <!--<a href="http://us.lemall.com/us/privacyPolicy.html">-->
              <!--Privacy Policy-->
            <!--</a>-->
          <!--</div>-->
        <!--</div>-->
      <!--</div>-->
    <!--</div>-->
    <!--</footer>-->
  </div>
</template>

<script>
  import NavHeader from '@/components/Header'
  import NavBread from '@/components/Bread'
  import vnFooter from '@/components/Footer'
  import '@/static/css/index.css'
  import axios from 'axios'

  export default {
    data(){
      return {
        list:{}
      }
    },
    components:{
      NavHeader,
      NavBread,
      vnFooter
    },
    created(){
      this.getData();
    },
    methods:{
      getData(){
//        axios.get('/goods')
        axios.get('http://www.easy-mock.com/mock/59e9c6dca1f84452245c6e93/goods')
          .then((res)=>{
            this.list=res.data.data;
          });
      }
    }
  }
</script>
