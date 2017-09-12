<template>
	<div class="header">
		<div class="content-wrapper">
			<div class="avatar">
				<img width="64" height="64" :src="seller.avatar">
			</div>
			<div class="content">
				<div class="title">
					<span class="brand"></span>
					<span class="name">{{seller.name}}</span>
				</div>
				<div class="description">
					{{seller.description}}/{{seller.deliveryTime}}分钟送达
				</div>
				<div v-if="seller.supports" class="support">
					<span class="icon" :class="classMap[seller.supports[0].type]"></span>
					<span class="text">
						{{seller.supports[0].description}}
					</span>
				</div>
			</div>
			<div v-if="seller.supports" class="support-count">
				<span class="count">{{seller.supports.length}}个</span>
				<i class="arrow-right"></i>
			</div>
		</div>

		<div class="bulletin-wrapper">
			<span class="bulletin-title"></span>
			<span class="bulletin-text">{{seller.bulletin}}</span>
			<i class="bullet-arrow-right"></i>
		</div>

		<div class="background">
			<img :src="seller.avatar" width="100%" height="100%">
		</div>
	</div>
</template>
<script type="text/javascript">
	export default{
		props:{
			seller:{
				type:Object
			}
		},
		created(){
			this.classMap = ["decrease","discount","guarantee","invoice","special"];
		}
	}
</script>

<style type="text/css" lang="less">
   @import "../../common/less/style.less";
</style>

<style type="text/css">
	.header{
		color: #fff;
		position: relative;
		background: rgba(7,17,27,0.5);
	}

	.content-wrapper{
		padding: 24px 12px 18px 24px;
		font-size: 0;
		position: relative;
	}

	.avatar{
		display: inline-block;
		vertical-align: top;
		border-radius: 2px;
	}

	.content{
		display: inline-block;
		font-size: 14px;
		margin-left: 16px;
	}

	.title{
		margin: 2px 0 8px 0;
	}

	.title .brand{
		display: inline-block;
		width: 30px;
		height: 18px;
		background:url(./brand@2x.png);
		background-size: 30px 18px;
		background-repeat: no-repeat;
		vertical-align: top;
	}

	.name{
		margin-left: 6px;
		font-size: 16px;
		line-height: 18px;
		font-weight: bold;
	}

	.description{
		margin-bottom: 10px;
		line-height: 12px;
		font-size: 12px;
	}

	.support .icon{
		display: inline-block;
		width: 12px;
		height: 12px;
		margin-right: 4px;
		background-size: 12px 12px;
		background-repeat: no-repeat;
		vertical-align: top;
	}

	.support .decrease{
		background-image: url(./decrease_1@2x.png);
	}

	.support .discount{
		background-image: url(./discount_1@2x.png);
	}

	.support .guarantee{
		background-image: url(./guarantee_1@2x.png);
	}

	.support .invoice{
		background-image: url(./invoice_1@2x.png);
	}

	.support .special{
		background-image: url(./special_1@2x.png);
	}

	.support .text{
		line-height: 12px;
		font-size: 12px;
	}

	.support-count{
		position: absolute;
		right: 12px;
		bottom: 14px;
		padding: 0 8px;
		height: 24px;
		line-height: 24px;
		border-radius: 14px;
		background:rgba(0,0,0,0.2);
		text-align: center;
	}

	.support-count .arrow-right::before{
		content: '\009B';
	}

	.support-count .arrow-right{
		font-size: 10px;	
		line-height: 24px;
		padding: 2px;
		padding-left: 5px;
	}

	.count{
		font-size: 10px;
		vertical-align: top;
	}

	.bulletin-wrapper{
		height: 28px;
		line-height: 28px;
		padding: 0 22px 0 22px;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		background: rgba(7,17,27,0.2);
	}

	.bulletin-title{
		display: inline-block;
		width: 22px;
		height: 12px;
		background-image: url(./bulletin@2x.png);
		background-size: 22px 12px;
		background-repeat: no-repeat;
	}

	.bulletin-text{
		font-size:10px;
		margin:0 4px;
		vertical-align: top; 
	}

	.bullet-arrow-right{
		position: absolute;
		font-size: 10px;
		right: 12px;
		top: 8px;
	}

	.bullet-arrow-right::before{
		content: '\009B';
		font-size: 20px;
		position: absolute;
		top: 94px;
	}

	.background{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: -1;
		filter: blur(10px);
	}
</style>