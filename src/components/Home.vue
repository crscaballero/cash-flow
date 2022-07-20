<template>
	<Layout>
		<template #header>
			<Header />
		</template>
		<template #resume>
			<Resume
				:totalLabel="'Total savings'"
				:label="label"
				:totalAmount="100000"
				:amount="amount"
			>
				<template #graphic>
					<Graphic :amounts="amounts" />
				</template>
				<template #action>
					<Action />
				</template>
			</Resume>
		</template>
		<template #movements>
			<Movements :movements="movements" />
		</template>
	</Layout>
</template>
<script>
import Header from '@/components/Header.vue';
import Layout from '@/components/Layout.vue';
import Resume from '@/components/Resume/Index.vue';
import Movements from '@/components/Movements/Index.vue';
import Action from '@/components/Action.vue';
import Graphic from '@/components/Graphic.vue';

export default {
	components: {
		Header,
		Layout,
		Resume,
		Movements,
		Action,
		Graphic,
	},
	data() {
		return {
			label: null,
			amount: null,
			amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
			movements: [
				{
					id: 0,
					title: 'Movement',
					description: 'Salary deposit',
					amount: 1000,
				},
				{
					id: 1,
					title: 'Movement 1',
					description: 'Deposit of fees',
					amount: 500,
				},
				{
					id: 2,
					title: 'Movement 2',
					description: 'Food',
					amount: -100,
				},
				{
					id: 3,
					title: 'Movement 3',
					description: 'Tuition',
					amount: 1000,
				},
				{
					id: 4,
					title: 'Movement 4',
					description: 'Computer repair',
					amount: 1000,
				},
				{
					id: 5,
					title: 'Movement 5',
					description: 'Computer repair',
					amount: 1000,
				},
				{
					id: 6,
					title: 'Movement 6',
					description: 'Computer repair',
					amount: 1000,
				},
				{
					id: 7,
					title: 'Movement 7',
					description: 'Computer repair',
					amount: 1000,
				},
				{
					id: 8,
					title: 'Movement 8',
					description: 'Computer repair',
					amount: 1000,
				},
				{
					id: 9,
					title: 'Movement 9',
					description: 'Computer repair',
					amount: 1000,
				},
			],
		};
	},
};
</script>
