<template>
	<view>
	<u-form
		labelPosition="left"
		labelWidth="140rpx"
		:model=model1
		:rules="rules"
		ref="form1"
		labelAlign="center"
	>
		<u-form-item
		label="用户名:"
		ref="item1"
		prop="userInfo.name"
		borderBottom
		>
			<u-input
				border="surround"
				placeholder="请输入用户名"
				v-model="model1.userInfo.name"
			></u-input>
		</u-form-item>
		
		<u-form-item
		label="密码:"
	  prop="userInfo.password"
		>
			<u-input
				placeholder="请输入密码"
				border="surround"
				type="password"
				v-model="model1.userInfo.password"
			></u-input>
		</u-form-item>
		<u-form-item
		label="手机号码:"
		prop="userInfo.number"
		>
			<u-input
				placeholder="请输入手机号"
				border="surround"
				type="number"
				v-model="model1.userInfo.number"
			></u-input>
		</u-form-item>
		<u-form-item
		label="性别:"
		@click="showSex = true;"
		>
			<u-input
				v-model="model1.userInfo.sex"
				disabled
				disabledColor="#ffffff"
				placeholder="请选择性别"
				border="none"
			></u-input>
			<u-icon
									slot="right"
									name="arrow-right"
							></u-icon>
		</u-form-item>
	</u-form>
		<u-action-sheet
					:show="showSex"
					:actions="actions"
					title="请选择性别"
					@close="showSex = false"
					@select="sexSelect"
			>
			</u-action-sheet>
	</view>
</template>

<script>
export default {
	methods:{
		onReady() {
				//如果需要兼容微信小程序，并且校验规则中含有方法等，只能通过setRules方法设置规则。
		    	this.$refs.form1.setRules(this.rules)

		    },
				sexSelect(e) {
							this.model1.userInfo.sex = e.name
							this.$refs.form1.validateField('userInfo.sex')
						},
	},
data(){
	return {
		showSex: false,
		model1:{
			userInfo:{
				name:'uView UI',
				sex:'',
				number:'',
				password:''
			}
		},
			actions: [{
						name: '男',
						},
						{
							name: '女',
						},
					],
		rules:{
				'userInfo.name': [
					{
								type: 'string',
								required: true,
								message: '请填写用户名',
								trigger: ['blur', 'change'],
								
							},
				],
				
							'userInfo.sex': {
								type: 'string',
								max: 1,
								required: true,
								message: '请选择男或女',
								trigger: ['blur', 'change']
							},
							'userInfo.password': [
								{
								type: 'string',
								required: true,
								message: '请填写密码',
								trigger: ['change','blur'],
							},
							 {
								 type: 'string',
								 validator:(rule,value,cb)=>{
									  let res = /(?=.*[a-z_])(?=.*\d)(?=.*[^a-z0-9_])[\S]/i
										if(res.test(value)==false){
											return false
										}else{
											return true
										}
										console.log(rule);
										console.log(value);
										console.log(cb(111));
								 },
								 message:'密码必须包含英语数字并携带特殊符号',
								 trigger: ['change','blur'],
								 // pattern:/(?=.*[a-z_])(?=.*\d)(?=.*[^a-z0-9_])[\S]/i, message: "提示信息测试",trigger: ["blur", "change"]
							 }
							],
							'userInfo.number':[
								{
									type: 'number',
									required: true,
									message: '请填写手机号',
									trigger: ['change','blur'],
								},
								{
									type: 'number',
									validator:(rule,value,cb)=>{
										return this.$u.test.mobile(value)
											
									},
										message: '请输入正确的手机号',
										trigger: ['change','blur'],
								}
							]
							
		}
	}
}
};
</script>

<style lang="scss" scoped>
	view{
		text{
			color: red;
		}
	}

</style>
