<script lang="ts">
	import { Bar } from 'svelte-chartjs';
	import { Chart, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

	Chart.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

	let data = {
		labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
		datasets: [
			{
				label: '% of Votes',
				data: [12, 19, 3, 5, 2, 3],
				backgroundColor: [
					'rgba(255, 134,159,0.4)',
					'rgba(98,  182, 239,0.4)',
					'rgba(255, 218, 128,0.4)',
					'rgba(113, 205, 205,0.4)',
					'rgba(170, 128, 252,0.4)',
					'rgba(255, 177, 101,0.4)'
				],
				borderWidth: 2,
				borderColor: [
					'rgba(255, 134, 159, 1)',
					'rgba(98,  182, 239, 1)',
					'rgba(255, 218, 128, 1)',
					'rgba(113, 205, 205, 1)',
					'rgba(170, 128, 252, 1)',
					'rgba(255, 177, 101, 1)'
				]
			}
		]
	};

	let options = {
		responsive: true,
		scales: {
			xAxes: [
				{
					barPercentage: 1,
					gridLines: {
						display: true,
						color: 'rgba(0, 0, 0, 0.1)'
					}
				}
			],
			yAxes: [
				{
					gridLines: {
						display: true,
						color: 'rgba(0, 0, 0, 0.1)'
					},
					ticks: {
						beginAtZero: true
					}
				}
			]
		}
	};
</script>

<div class="h-[350px] w-full">
	<Bar {data} {options} />
</div>
