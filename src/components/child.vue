<template>
  <div class="dialog" v-show='isShow'>
  	<div class='dialog-mask'></div>
  	<div class='dialog-box'>
  		<div class="title">
	  		<slot name='title'>标题</slot>
	  		
  		</div>
  		<div class='dialog-content'>
  			<p>来支持你选中的商品吧</p>
  			<ul>
  				<li v-for='item in list'>
  					<slot :item=item></slot>
  				</li>
  			</ul>
  		</div>
  		<a href="javascript:void(0);" class='close' @click='closeDiag();'>X</a>
  	</div>

 </div>
</template>

<script>
export default {
  props: {
    isShow:{
    	type:Boolean
    },
    list:{}
  },
  methods:{
  	closeDiag:function(){
  		this.$emit('closeFun');
  	}
  	
  }
}
</script>
<style scoped lang='less'>
.dialog{

	.dialog-mask{
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: #000;
		opacity: .6;
		z-index: 20;
	}
	.dialog-box{
		width: 200px;
		position: fixed;;
		top: 30%;
		left:50%;
		margin-left:-100px;
		background:#fff;
		border-radius:10px;
		box-sizing: border-box;
		z-index: 21;
		.title{

		    border-top-left-radius: 8px;
		    border-top-right-radius: 8px;
		    line-height: 30px;
			position:relative;
			background: #ecc11a;
			text-align: center;
			p{
				font-size:14px;
			}
		}
		.dialog-content{
			
			p{
				text-align: left;
			    color: #999;
			    text-indent:10px;  
			    line-height: 24px;
			}
			ul{
				padding:0px 0 15px;
				li{

					line-height: 30px;
					border-bottom:1px solid #ccc;
					&:last-child{
						border-bottom:0;
					}
				}				
			}
		}
	.close{
				position:absolute;
				left:50%;
				bottom:-8px;
				width:20px;
				height: 20px;
				line-height: 20px;
				margin-left:-10px;
				border-radius:50%;
				color:#000;
				background:#ecc11a;
			}
	}
}
</style>