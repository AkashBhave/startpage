<script lang="ts">
		import { onMount } from "svelte";

	let time = new Date();

	$: hours = time.getHours();
	$: minutes = time.getMinutes();
	$: seconds = time.getSeconds();
	$: weekday = time.toLocaleDateString("en-US", { weekday: "long" });

	onMount(() => {
		const interval = setInterval(() => {
			time = new Date();
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<style>
		section {
				display: flex;
				flex-direction: column;
				align-items: center;
		}

		.separator {
				opacity: 0.6;
		}

		#time {
				display: flex;
				font-size: 2.5em;
				align-items: center;
				margin-bottom: 20px;
		}
		#time .meridiem {
				margin-left: 20px;
				font-size: 0.6em;
				opacity: 0.8;
		}
		@media screen and (max-height: 650px) {
				#time {
						margin-bottom: 10px;
				}
		}

		#weekday {
				font-size: 1em;
				margin-bottom: 25px;
				opacity: 0.8;
		}
		@media screen and (max-height: 650px) {
				#weekday {
						margin-bottom: 15px;
				}
		}

		#year {
				display: flex;
				font-size: 1.5em;
		}
</style>

<section>
		<div id="time">
				<span>{String(((hours + 11) % 12) + 1).padStart(2, '0')}</span>
				<span class="separator">:</span>
				<span>{String(minutes).padStart(2, '0')}</span>
				<span class="separator">:</span>
				<span>{String(seconds).padStart(2, '0')}</span>
				<span class="meridiem">{hours >= 12 ? 'p.m.' : 'a.m.'}</span>
		</div>
		<p id="weekday">{weekday}</p>
		<p id="year">
		<span>{time.getFullYear()}</span>
		<span class="separator">-</span>
		<span>{String(time.getMonth() + 1).padStart(2, '0')}</span>
		<span class="separator">-</span>
		<span>{String(time.getDate()).padStart(2, '0')}</span>
		</p>
</section>
