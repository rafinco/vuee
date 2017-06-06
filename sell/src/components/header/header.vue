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
  			<div class="description">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
  			<div v-if="seller.supports" class="support">
  				<span class="icon" :class="classMap[seller.supports[0].type]"></span>
  				<span class="text">{{seller.supports[0].description}}</span>
  			</div>
  		</div>
  		<div v-if="seller.supports" class="support-count">
  			<span class="count">{{seller.supports.length}}个</span>
  			<i class="icon-keyboard_arrow_right"></i>
  		</div>
  	</div>
  	<div class="bulletin-wrapper"></div>
  </div>
</template>

<script>
	export default {
		props:{
			seller:{
				type: Object
			}
		},
		created(){
			this.classMap = ["decrease","discount","special","invoice","guarantee"]
		}
	};
</script>

<style>

	@import '../../common/css/icon.css';

	.header{
		color: #fff;
		background:#ccc;
	}
	.content-wrapper{
		padding: 24px 12px 18px 24px;
		font-size: 0;
		position: relative;
	}
	.avatar{
		display: inline-block;
		vertical-align: top;
	}
	.content{
		display: inline-block;
		margin-left: 16px;
	}
	.title{
		margin: 2px 0 8px 0;
	}
	.brand{
		width: 30px;
		height: 18px;
		display: inline-block;
		background-image: url(brand@2x.png);
		background-size: 30px 18px;
		background-repeat: no-repeat;
		vertical-align: top;
	}
	.name{
		margin-left: 6px;
		font-size: 16px;
		line-height: 18px;
		font-weight: 700;
		display: inline-block;
	}
	.description{
		margin-bottom: 10px;
		line-height: 12px;
		font-size: 12px;
	}
	.icon{
		display: inline-block;
		width: 12px;
		height: 12px;
		background-size: 12px 12px;
		background-repeat: no-repeat;
		margin-right: 4px;
		vertical-align: top;
	}
	.icon.decrease{
		background-image: url(decrease_1@2x.png);
	}
	.icon.discount{
		background-image: url(discount_1@2x.png);
	}
	.icon.guarantee{
		background-image: url(guarantee_1@2x.png);
	}
	.icon.invoice{
		background-image: url(invoice_1@2x.png);
	}
	.icon.special{
		background-image: url(special_1@2x.png);
	}
	.text{
		font-size: 10px;
		line-height: 12px;
	}
	.support-count{
		position: absolute;
		right: 12px;
		bottom: 18px;
		padding: 0 8px;
		height: 24px;
		line-height: 24px;
		border-radius: 14px;
		background:rgba(0,0,0,0.2);
		text-align: center;
	}
	.count{
		font-size: 10px;
	}
	.icon-keyboard_arrow_right{
		font-size: 10px;
	}
</style>
