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
</script>

<section id="background" class="py-24 bg-white">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div bind:this={ref} class="transition duration-700 {isVisible ? 'opacity-100' : 'opacity-0'}">
			<!-- Section Header -->
			<div class="text-center mb-16">
				<span class="inline-block px-4 py-1.5 bg-primary/10 text-primary text-sm font-semibold rounded-full mb-4">
					Background
				</span>
				<h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
					From Tech Leader to Strategic Advisor
				</h2>
				<p class="text-xl text-gray-600 max-w-3xl mx-auto">
					With over two decades of experience building and scaling technology companies, I bring deep operational expertise to every engagement.
				</p>
			</div>

			<!-- Timeline -->
			<div class="relative">
				<!-- Timeline Line -->
				<div class="hidden md:block absolute left-1/2 transform -translate-x-1/2 h-full w-0.5 bg-gray-200"></div>

				<!-- Timeline Items -->
				<div class="space-y-12">
					<!-- Item 1 -->
					<div class="relative flex flex-col md:flex-row items-center">
						<div class="md:w-1/2 md:pr-12 md:text-right mb-4 md:mb-0">
							<h3 class="text-xl font-bold text-gray-900 mb-2">VP of Engineering</h3>
							<p class="text-primary font-semibold mb-2">TechCorp Global</p>
							<p class="text-gray-600 text-sm">Led engineering organization of 500+ people. Scaled platform to serve 100M+ users. Drove digital transformation initiatives across the enterprise.</p>
						</div>
						<div class="absolute left-1/2 transform -translate-x-1/2 w-4 h-4 bg-accent rounded-full border-4 border-white shadow-lg hidden md:block"></div>
						<div class="md:w-1/2 md:pl-12">
							<span class="inline-block px-3 py-1 bg-gray-100 text-gray-600 text-sm rounded">2015 - 2020</span>
						</div>
					</div>

					<!-- Item 2 -->
					<div class="relative flex flex-col md:flex-row items-center">
						<div class="md:w-1/2 md:pr-12 md:text-right mb-4 md:mb-0 order-1 md:order-1">
							<span class="inline-block px-3 py-1 bg-gray-100 text-gray-600 text-sm rounded">2010 - 2015</span>
						</div>
						<div class="absolute left-1/2 transform -translate-x-1/2 w-4 h-4 bg-accent rounded-full border-4 border-white shadow-lg hidden md:block"></div>
						<div class="md:w-1/2 md:pl-12 order-2 md:order-2">
							<h3 class="text-xl font-bold text-gray-900 mb-2">CTO & Co-Founder</h3>
							<p class="text-primary font-semibold mb-2">StartupXYZ</p>
							<p class="text-gray-600 text-sm">Built and scaled a B2B SaaS platform from zero to $50M ARR. Led team from 5 to 150 engineers. Successfully exited through acquisition.</p>
						</div>
					</div>

					<!-- Item 3 -->
					<div class="relative flex flex-col md:flex-row items-center">
						<div class="md:w-1/2 md:pr-12 md:text-right mb-4 md:mb-0">
							<h3 class="text-xl font-bold text-gray-900 mb-2">Board Advisor</h3>
							<p class="text-primary font-semibold mb-2">Multiple Organizations</p>
							<p class="text-gray-600 text-sm">Serving on boards of 8+ technology companies. Providing strategic guidance on growth, product development, and market expansion.</p>
						</div>
						<div class="absolute left-1/2 transform -translate-x-1/2 w-4 h-4 bg-accent rounded-full border-4 border-white shadow-lg hidden md:block"></div>
						<div class="md:w-1/2 md:pl-12">
							<span class="inline-block px-3 py-1 bg-gray-100 text-gray-600 text-sm rounded">2020 - Present</span>
						</div>
					</div>
				</div>
			</div>

			<!-- Key Achievements -->
			<div class="mt-20 grid grid-cols-1 md:grid-cols-3 gap-8">
				<div class="bg-gray-50 rounded-xl p-6 text-center hover:shadow-lg transition-shadow">
					<div class="w-16 h-16 bg-primary/10 rounded-xl flex items-center justify-center mx-auto mb-4">
						<svg class="w-8 h-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
						</svg>
					</div>
					<h4 class="text-lg font-semibold text-gray-900 mb-2">Revenue Growth</h4>
					<p class="text-gray-600 text-sm">Helped portfolio companies achieve average 3x revenue growth within 24 months</p>
				</div>

				<div class="bg-gray-50 rounded-xl p-6 text-center hover:shadow-lg transition-shadow">
					<div class="w-16 h-16 bg-primary/10 rounded-xl flex items-center justify-center mx-auto mb-4">
						<svg class="w-8 h-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
						</svg>
					</div>
					<h4 class="text-lg font-semibold text-gray-900 mb-2">Team Building</h4>
					<p class="text-gray-600 text-sm">Built and mentored 1000+ engineers and technology leaders across organizations</p>
				</div>

				<div class="bg-gray-50 rounded-xl p-6 text-center hover:shadow-lg transition-shadow">
					<div class="w-16 h-16 bg-primary/10 rounded-xl flex items-center justify-center mx-auto mb-4">
						<svg class="w-8 h-8 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
						</svg>
					</div>
					<h4 class="text-lg font-semibold text-gray-900 mb-2">Innovation</h4>
					<p class="text-gray-600 text-sm">Pioneered adoption of AI, cloud, and emerging technologies across multiple industries</p>
				</div>
			</div>
		</div>
	</div>
</section>
