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
					<Action @create="create" />
				</template>
			</Resume>
		</template>
		<template #movements>
			<Movements :movements="movements" @remove="remove" />
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
			movements: [
				{
					id: 0,
					title: 'Movement 1',
					description: 'Lorem ipsum dolor sit amet',
					amount: 100,
					time: new Date('07-01-2022'),
				},
				{
					id: 1,
					title: 'Movement 2',
					description: 'Lorem ipsum dolor sit amet',
					amount: 200,
					time: new Date('07-01-2022'),
				},
				{
					id: 2,
					title: 'Movement 3',
					description: 'Lorem ipsum dolor sit amet',
					amount: 500,
					time: new Date('07-01-2022'),
				},
				{
					id: 3,
					title: 'Movement 4',
					description: 'Lorem ipsum dolor sit amet',
					amount: 200,
					time: new Date('07-01-2022'),
				},
				{
					id: 4,
					title: 'Movement 5',
					description: 'Lorem ipsum dolor sit amet',
					amount: -400,
					time: new Date('07-01-2022'),
				},
				{
					id: 5,
					title: 'Movement 6',
					description: 'Lorem ipsum dolor sit amet',
					amount: -600,
					time: new Date('07-01-2022'),
				},
				{
					id: 6,
					title: 'Movement 7',
					description: 'Lorem ipsum dolor sit amet',
					amount: -300,
					time: new Date('07-01-2022'),
				},
				{
					id: 7,
					title: 'Movement 8',
					description: 'Lorem ipsum dolor sit amet',
					amount: 100,
					time: new Date('07-01-2022'),
				},
				{
					id: 8,
					title: 'Movement 9',
					description: 'Lorem ipsum dolor sit amet',
					amount: 300,
					time: new Date('07-01-2022'),
				},
				{
					id: 9,
					title: 'Movement 10',
					description: 'Lorem ipsum dolor sit amet',
					amount: 500,
					time: new Date('01-01-2022'),
				},
			],
		};
	},
	computed: {
		amounts() {
			const lastDays = this.movements
				.filter(m => {
					const today = new Date();
					const oldDate = today.setDate(today.getDate() - 30);
					return m.time >= oldDate;
				})
				.map(m => m.amount);
			return lastDays.map((m, i) => {
				const lastMovements = lastDays.slice(0, i);
				return lastMovements.reduce((sum, movement) => {
					return sum + movement;
				}, 0);
			});
		},
	},
	mounted() {
		const movements = JSON.parse(localStorage.getItem('movements'));
		if (Array.isArray(movements)) {
			this.movements = movements?.map(m => {
				return { ...m, time: new Date(m.time) };
			});
		}
	},
	methods: {
		create(movement) {
			this.movements.push(movement);
			this.save();
		},
		remove(id) {
			const index = this.movements.findIndex(m => m.id === id);
			this.movements.splice(index, 1);
			this.save();
		},
		save() {
			localStorage.setItem('movements', JSON.stringify(this.movements));
		},
	},
};
</script>
