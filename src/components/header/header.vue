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
		</div>
		<div class="bulletin-wrapper"></div>
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
<style type="text/css">
	.header{
		color: white;
		background-color: black;
	}
	.content-wrapper{
		padding: 24px 12px 18px 24px;
		font-size: 0;
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
</style>