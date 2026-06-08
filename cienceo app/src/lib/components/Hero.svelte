<script lang="ts">
	import { onMount } from 'svelte';

	let heroRef: HTMLDivElement;
	let isVisible = $state(false);

	onMount(() => {
		isVisible = true;
	});
</script>

<section id="home" class="relative min-h-screen flex items-center overflow-hidden">
	<!-- Background -->
	<div class="absolute inset-0 bg-gradient-to-br from-primary via-primary-dark to-primary-light"></div>

	<!-- Decorative Elements -->
	<div class="absolute inset-0 overflow-hidden">
		<div class="absolute -top-40 -right-40 w-96 h-96 bg-accent/10 rounded-full blur-3xl"></div>
		<div class="absolute -bottom-40 -left-40 w-96 h-96 bg-primary-light/20 rounded-full blur-3xl"></div>
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-accent/5 rounded-full blur-3xl"></div>
	</div>

	<!-- Grid Pattern Overlay -->
	<div class="absolute inset-0 opacity-10">
		<div class="absolute inset-0" style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); background-size: 40px 40px;"></div>
	</div>

	<!-- Content -->
	<div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-32">
		<div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
			<!-- Left Column - Text -->
			<div
				class="animate-fade-in transition duration-1000 {isVisible
					? 'opacity-100 translate-y-0'
					: 'opacity-0 translate-y-10'}"
			>
				<div class="inline-flex items-center gap-2 px-4 py-2 bg-white/10 backdrop-blur-sm rounded-full mb-6 border border-white/20">
					<span class="w-2 h-2 bg-accent rounded-full animate-pulse"></span>
					<span class="text-white/90 text-sm font-medium">Available for new engagements</span>
				</div>

				<h1 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white leading-tight mb-6">
					Strategic Advisor
					<br />
					<span class="text-accent">to Technology and Fintech CEOs</span>
				</h1>

				<p class="text-xl text-gray-200 mb-8 leading-relaxed max-w-xl">
					Helping technology company leaders navigate growth, transformation, and innovation with proven strategies from 20+ years of experience.
				</p>

				<div class="flex flex-col sm:flex-row gap-4">
					<a
						href="#contact"
						onclick={(e) => {
							e.preventDefault();
							document.getElementById('contact')?.scrollIntoView({ behavior: 'smooth' });
						}}
						class="inline-flex items-center justify-center px-8 py-4 bg-accent text-primary-dark font-semibold rounded-lg hover:bg-accent-light transition-all duration-200 shadow-lg hover:shadow-xl transform hover:-translate-y-0.5"
					>
						Schedule a Call
						<svg class="ml-2 w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
						</svg>
					</a>
					<a
						href="#background"
						onclick={(e) => {
							e.preventDefault();
							document.getElementById('background')?.scrollIntoView({ behavior: 'smooth' });
						}}
						class="inline-flex items-center justify-center px-8 py-4 bg-white/10 backdrop-blur-sm text-white font-semibold rounded-lg border border-white/20 hover:bg-white/20 transition-all duration-200"
					>
						Learn More
					</a>
				</div>

				<!-- Stats -->
				<div class="grid grid-cols-3 gap-6 mt-12 pt-8 border-t border-white/10">
					<div>
						<div class="text-3xl font-bold text-accent">20+</div>
						<div class="text-sm text-gray-300 mt-1">Years Experience</div>
					</div>
					<div>
						<div class="text-3xl font-bold text-accent">50+</div>
						<div class="text-sm text-gray-300 mt-1">CEOs Advised</div>
					</div>
					<div>
						<div class="text-3xl font-bold text-accent">$10B+</div>
						<div class="text-sm text-gray-300 mt-1">Revenue Influenced</div>
					</div>
				</div>
			</div>

			<!-- Right Column - Image/Visual -->
			<div
				class="animate-fade-in transition duration-1000 delay-200 {isVisible
					? 'opacity-100 translate-x-0'
					: 'opacity-0 translate-x-10'}"
			>
				<div class="relative">
					<!-- Main Image Container -->
					<div class="relative rounded-2xl overflow-hidden shadow-2xl">
						<img
							src="/david-sikora.jpg"
							alt="David Sikora"
							class="w-full h-auto object-cover"
							loading="eager"
						/>
						<!-- Gradient Overlay -->
						<div class="absolute inset-0 bg-gradient-to-t from-primary/60 via-transparent to-transparent"></div>
					</div>

					<!-- Floating Card -->
					<div class="absolute -bottom-6 -left-6 bg-white rounded-xl shadow-xl p-4 max-w-xs">
						<div class="flex items-start gap-3">
							<div class="flex-shrink-0 w-10 h-10 bg-accent/10 rounded-lg flex items-center justify-center">
								<svg class="w-5 h-5 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
								</svg>
							</div>
							<div>
								<p class="text-sm font-semibold text-gray-900">Trusted Advisor</p>
								<p class="text-xs text-gray-500 mt-0.5">To Fortune 500 CEOs</p>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Scroll Indicator -->
	<div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
		<a
			href="#background"
			onclick={(e) => {
				e.preventDefault();
				document.getElementById('background')?.scrollIntoView({ behavior: 'smooth' });
			}}
			class="text-white/60 hover:text-white transition-colors"
		>
			<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
			</svg>
		</a>
	</div>
</section>

<style>
	@keyframes fade-in {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.animate-fade-in {
		animation: fade-in 1s ease-out;
	}

	.delay-200 {
		animation-delay: 200ms;
	}
</style>
