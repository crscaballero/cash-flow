<template>
	<header>
		<img
			src="@/assets/cashflow-icon.svg"
			class=""
			alt="Logo"
			@click="reload"
		/>
		<h1><span>Cash</span>Flow</h1>
		<span></span>
	</header>
</template>
<script>
export default {
	methods: {
		reload() {
			location.reload();
		},
	},
};
</script>
<style scoped>
header {
	display: flex;
	justify-content: space-around;
	align-items: center;
	width: 100vw;
}
img,
span {
	width: 48px;
}
h1 {
	color: var(--brand-blue);
}
h1 span {
	color: var(--brand-green);
}
img {
	cursor: pointer;
}
</style>
