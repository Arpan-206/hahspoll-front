<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';
	let error;
	let poll;
	let pollData;
	let optpercents = [];
	onMount(async () => {
		const res = await fetch(
			'https://24yl4zi1hh.execute-api.us-east-1.amazonaws.com/get/' + $page.params.id
		);
		if (res.ok) {
			poll = await res.json();
			poll = poll.poll;
		} else {
			error = res.status;
		}
	});
	async function vote(e) {
		const res = await fetch('https://24yl4zi1hh.execute-api.us-east-1.amazonaws.com/vote', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({
				poll_id: $page.params.id,
				vote: parseInt(e.target.value)
			})
		});
		if (res.ok) {
			pollData = await res.json();
			pollData = pollData.poll;
			let btns = document.querySelectorAll('button');
			btns.forEach((btn) => {
				btn.disabled = true;
			});
			let prgs = document.querySelectorAll('progress');
			let i = 1;
			prgs.forEach((prg) => {
				prg.classList.remove('invisible');
				optpercents.push((pollData['option' + i] / pollData.responses) * 100);
                optpercents = optpercents;
                prg.value = optpercents[i - 1];
				i++;
			});
            let vardivs = document.querySelectorAll('.vardiv');
            let j = 1;
            vardivs.forEach((vardiv) => {
                vardiv.classList.remove('invisible');
                j++;
            });
		} else {
			error = res.status;
		}
	}
</script>

<svelte:head>
    <title>{poll ? poll.question : 'Loading...'}</title>
    <meta name="description" content="Hashpoll Poll" />
</svelte:head>

{#if !poll}
	<h1>
		<article aria-busy="true" />
		Loading poll
	</h1>
	<p>If it doesn't load in 2-5 seconds then an error has occured.</p>
{:else}
	<h2>{poll.question}</h2>
	<button on:click={vote} value={1} id="option1" class="outline box-teal op-btn"
		>{poll.option1}<div class="grid">
            <div><progress id="prog1" class="invisible" value="0" max="100" /></div>
            <div class="invisible vardiv"><b>{parseInt(optpercents[0])}%</b></div>
          </div></button
	>
    <button on:click={vote} value={2} id="option1" class="outline box-teal op-btn"
		>{poll.option2}<div class="grid">
            <div><progress id="prog2" class="invisible" value="0" max="100" /></div>
            <div class="invisible vardiv"><b>{parseInt(optpercents[1])}%</b></div>
          </div></button
	>
    <button on:click={vote} value={3} id="option1" class="outline box-teal op-btn"
		>{poll.option3}<div class="grid">
            <div><progress id="prog3" class="invisible" value="0" max="100" /></div>
            <div class="invisible vardiv"><b>{parseInt(optpercents[2])}%</b></div>
          </div></button
	>
    <button on:click={vote} value={4} id="option1" class="outline box-teal op-btn"
		>{poll.option4}<div class="grid">
            <div><progress id="prog4" class="invisible" value="0" max="100" /></div>
            <div class="invisible vardiv"><b>{parseInt(optpercents[3])}%</b></div>
          </div></button
	>
{/if}