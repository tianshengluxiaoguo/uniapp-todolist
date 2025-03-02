<template>
	<view class="demo4">
		<view class="title">近期热梗</view>
		<view class="box">
			<!-- 上面的列表 -->
		   <view class="row"  v-for="(item, index) in text" :id="item.id">
			   <view class="text">
			   	{{ index+1 }}.{{ item.title }}
			   </view>
			   <view class="close" @click="removeBtn(index)">
			   	<icon type="clear" size="24"></icon>
			   </view>
		   </view>
		   <view class="number">共{{ text.length }}条梗</view>
		   <view class="search">
			  <input type="text"
			   placeholder='请输入热梗...'
			   v-model="isActive"
			   @confirm='pushBtn'
			   />
			  <button  size='mini' type='primary' :disabled="!isActive.length"
			  @click="pushBtn"
			  >发布</button>
		   </view>
		   
		</view>
	</view>
</template>

<script setup>
import { ref } from "vue"
const text = ref([
	{id:1, title: '刚满18岁'},
	{id:2, title: '宝宝饿了'},
	{id:3, title: '我最帅了'},
	{id:4, title: 'CPDD'},
])
const isActive = ref('')
const removeBtn = (index) => {
	text.value.splice(index, 1)
}
const pushBtn = () => {
	text.value.push({id:Date.now(), title:isActive.value})
	isActive.value = ''
}
</script>

<style lang="scss" scoped>
.demo4{
	 display: flex;
	 flex-direction: column;
	 background-color: #f9f9f9;
	 border-radius: 8px;
	 padding: 20px;
	 box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	 
	.title{
		margin: 20px 0;
		text-align: center;
		font-size: 22px;
		color: #333;
	}
	
	.box{
		display: flex;
		flex-direction: column;
		background-color: white;
		border-radius: 8px;
		width: 100%;
	    margin: 0 auto;
		
	}
	.row{
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 15px 0;
		border-bottom: 1px solid #c0c0c0;
	}
	.number{
		margin: 20px 0; 
		text-align: center;
		font-size: 16px;
	}
	.search{
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 10px 0;
		
		input{
			flex: 1;
			border: 1px solid #e0e0e0;
			font-size: 16px;
			padding: 10px;
		}
		
		button{
			padding: 10px 20px;
			margin-left: 5px;
		}
	}
}


</style>
