<template>
  <div id="app">
  	<v-header :seller="seller"></v-header>
  	<div class="tab border-1px">
  		<div class="tab-item">
  			<router-link to="/goods" tag="div">商品</router-link>
  		</div>
  		<div class="tab-item">
  			<router-link to="/ratings" tag="div">评论</router-link>
  		</div>
  		<div class="tab-item">
  			<router-link to="/seller" tag="div">商家</router-link>
  		</div>
  	</div>
    <router-view></router-view>
  </div>
</template>

<script>
	import header from 'components/header/header'
	import Axios from 'axios'
	
	export default{
		data(){
			return {
				seller : {}
			}
		},
		created(){
			//var _this = this;
			Axios.get('/api/seller')
			  .then((res) =>{
			  	if(res.data.errorno === 0){
			  		this.seller=res.data.data;
			  		console.log(this.seller);
			  	}			    
			  })
		},
		components:{
			'v-header' : header
		}
	}
</script>

<style>
	.tab{
		display: flex;
		width: 100%;
		height: 40px;
		line-height: 40px;
		position: relative;
	}

	.tab::after{
		content: '';
		display: block;;
		width: 100%;
		border-bottom: 1px solid rgba(7,17,27,0.1);
		position: absolute;
		left: 0;
		bottom: 0;
	}

	.tab .tab-item{
		flex: 1;
		text-align: center;
	}
</style>
