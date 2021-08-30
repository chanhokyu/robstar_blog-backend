<template>
	<div class="login-container">
		<h1>509博客登录</h1>
		<v-form class="form" ref="form" v-model="valid" lazy-validation>
			<v-text-field v-model="account" :counter="15" :rules="nameRules" label="account" required></v-text-field>
			<v-text-field v-model="password" :counter="15" :rules="emailRules" type="password" label="password" required></v-text-field>
			<v-btn
				:disabled="!valid"
				color="success"
				class="mr-4"
				@click="validate"
			>
				登录
			</v-btn>
			<v-btn
				color="error"
				class="mr-4"
				@click="reset"
			>
				重置
			</v-btn>
		</v-form>
		<v-footer
			dark
			padless
		>
			<v-card
			flat
			tile
			class="indigo lighten-1 white--text text-center"
			>
			<v-card-text>
				<v-btn
				v-for="icon in icons"
				:key="icon"
				class="mx-4 white--text"
				icon
				>
				<v-icon size="24px">
					{{ icon }}
				</v-icon>
				</v-btn>
			</v-card-text>

			<v-card-text class="white--text pt-0">
				this is our first blog, please give us support.
			</v-card-text>

			<v-divider></v-divider>

			<v-card-text class="white--text">
				{{ new Date().getFullYear() }} — <strong>Jesus</strong>
			</v-card-text>
			</v-card>
		</v-footer>
	</div>
</template>

<script>
  import Vue from 'vue'

  export default Vue.extend({
    name: 'Login',
    data: () => ({
		valid: true,
		icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
		account: '',
		nameRules: [
			v => !!v || '请输入账号咯',
			v => (v && v.length <= 15 && v.length > 5) || '账号要大于5位，小于15位啊',
		],
		email: '',
		emailRules: [
			v => !!v || '请输入密码哇',
			v => (v && v.length <= 15 && v.length > 5) || '密码也要大于5位，小于15位啊',
		],
    }),
	methods: {
		validate () {
			this.$refs.form.validate()
		},
		reset () {
			this.$refs.form.reset()
		},
    },
  })
</script>

<style scoped>
.login-container {
	margin-top: 200px;
	text-align: center
}
.form {
	padding-top: 50px;
	width: 500px;
	margin: 0 auto
}
.bottom {
	margin-top: 300px
}
.v-footer {
	display: block;
	position: absolute;
	bottom: 0;
	width: 100%
}
</style>
