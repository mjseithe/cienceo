<script lang="ts">
	import { onMount } from 'svelte';

	let ref: HTMLDivElement;
	let isVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						isVisible = true;
					}
				});
			},
			{ threshold: 0.2 }
		);

		if (ref) observer.observe(ref);
		return () => observer.disconnect();
	});

	const practiceAreas = [
		{
			icon: 'M13 7h8m0 0v8m0-8l-8 8-4-4-6 6',
			title: 'Growth Strategy',
			description: 'Scaling operations, entering new markets, and driving sustainable revenue growth for technology companies.'
		},
		{
			icon: 'M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.262 3.25 1.26 4.512-.001',
			title: 'Digital Transformation',
			description: 'Leading organizational change, technology modernization, and cultural transformation initiatives.'
		},
		{
			icon: 'M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z',
			title: 'Product Strategy',
			description: 'Defining product roadmaps, go-to-market strategies, and portfolio optimization for competitive advantage.'
		},
		{
			icon: 'M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0z',
			title: 'Leadership Development',
			description: 'Building high-performing executive teams, succession planning, and leadership coaching programs.'
		},
		{
			icon: 'M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z',
			title: 'M&A Advisory',
			description: 'Strategic advisory for mergers, acquisitions, and divestitures in the technology sector.'
		},
		{
			icon: 'M13 10V3L4 14h7v7l9-11h-7z',
			title: 'Technology Innovation',
			description: 'Evaluating and implementing emerging technologies including AI, cloud, and blockchain solutions.'
		}
	];
</script>

<section id="practice-area" class="py-24 bg-gray-50">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div bind:this={ref} class:opacity-100 class:{{ 'opacity-0': !isVisible }} class:transition class:duration-700>
			<!-- Section Header -->
			<div class="text-center mb-16">
				<span class="inline-block px-4 py-1.5 bg-primary/10 text-primary text-sm font-semibold rounded-full mb-4">
					Practice Area
				</span>
				<h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
					How I Can Help You
				</h2>
				<p class="text-xl text-gray-600 max-w-3xl mx-auto">
					Comprehensive strategic advisory services tailored to the unique challenges facing technology company leaders.
				</p>
			</div>

			<!-- Practice Areas Grid -->
			<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
				{#each practiceAreas as area, index}
					<div
						class="bg-white rounded-xl p-6 shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100 hover:border-primary/20 group"
						class:opacity-100 class:{{ 'opacity-0 translate-y-8': !isVisible }}
						class:transition class:duration-700
						style="animation-delay: {index * 100}ms"
					>
						<div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center mb-4 group-hover:bg-primary group-hover:text-white transition-colors">
							<svg class="w-6 h-6 text-primary group-hover:text-white transition-colors" fill="none" viewBox="0 0 24 24" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="{area.icon}" />
							</svg>
						</div>
						<h3 class="text-xl font-semibold text-gray-900 mb-2">{area.title}</h3>
						<p class="text-gray-600 text-sm leading-relaxed">{area.description}</p>
					</div>
				{/each}
			</div>

			<!-- CTA -->
			<div class="mt-16 text-center">
				<p class="text-gray-600 mb-6">Not sure where to start? Let's have a conversation about your challenges.</p>
				<a
					href="#contact"
					onclick={(e) => {
						e.preventDefault();
						document.getElementById('contact')?.scrollIntoView({ behavior: 'smooth' });
					}}
					class="inline-flex items-center px-6 py-3 bg-primary text-white font-semibold rounded-lg hover:bg-primary-light transition-colors"
				>
					Schedule a Consultation
					<svg class="ml-2 w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
					</svg>
				</a>
			</div>
		</div>
	</div>
</section>
