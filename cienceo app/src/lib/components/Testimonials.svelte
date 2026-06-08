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

	const testimonials = [
		{
			quote: "Working with this advisor transformed our strategic approach. The insights gained helped us navigate a complex market transition and emerge stronger than ever.",
			name: "Sarah Chen",
			title: "CEO, TechVentures Inc.",
			image: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=100&h=100&fit=crop&crop=face"
		},
		{
			quote: "The depth of experience and strategic thinking brought to the table was invaluable. Our board was immediately impressed with the clarity and actionable recommendations.",
			name: "Michael Rodriguez",
			title: "CTO, Global Systems Corp",
			image: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=100&h=100&fit=crop&crop=face"
		},
		{
			quote: "During our most critical transformation period, the guidance provided was nothing short of exceptional. A true partner in our success.",
			name: "Emily Watson",
			title: "Founder & CEO, InnovateTech",
			image: "https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=100&h=100&fit=crop&crop=face"
		}
	];
</script>

<section id="testimonials" class="py-24 bg-white">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div bind:this={ref} class:opacity-100 class:{{ 'opacity-0': !isVisible }} class:transition class:duration-700>
			<!-- Section Header -->
			<div class="text-center mb-16">
				<span class="inline-block px-4 py-1.5 bg-primary/10 text-primary text-sm font-semibold rounded-full mb-4">
					Testimonials
				</span>
				<h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
					Trusted by Technology Leaders
				</h2>
				<p class="text-xl text-gray-600 max-w-3xl mx-auto">
					Hear from CEOs and executives who have partnered on their most critical strategic initiatives.
				</p>
			</div>

			<!-- Testimonials Grid -->
			<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
				{#each testimonials as testimonial, index}
					<div
						class="bg-gray-50 rounded-xl p-8 relative"
						class:opacity-100 class:{{ 'opacity-0 translate-y-8': !isVisible }}
						class:transition class:duration-700
						style="animation-delay: {index * 150}ms"
					>
						<!-- Quote Icon -->
						<div class="absolute -top-4 left-8">
							<div class="w-8 h-8 bg-accent rounded-lg flex items-center justify-center">
								<svg class="w-5 h-5 text-white" fill="currentColor" viewBox="0 0 24 24">
									<path d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h3.983v10h-9.983z" />
								</svg>
							</div>
						</div>

						<!-- Quote -->
						<p class="text-gray-700 mb-6 pt-4 leading-relaxed">"{testimonial.quote}"</p>

						<!-- Author -->
						<div class="flex items-center gap-4">
							<img
								src={testimonial.image}
								alt={testimonial.name}
								class="w-12 h-12 rounded-full object-cover"
								loading="lazy"
							/>
							<div>
								<p class="font-semibold text-gray-900">{testimonial.name}</p>
								<p class="text-sm text-gray-600">{testimonial.title}</p>
							</div>
						</div>
					</div>
				{/each}
			</div>

			<!-- Trust Badges -->
			<div class="mt-16 pt-12 border-t border-gray-200">
				<p class="text-center text-sm text-gray-500 mb-8 uppercase tracking-wider">Recognized by</p>
				<div class="flex flex-wrap justify-center items-center gap-12 opacity-60">
					<div class="text-2xl font-bold text-gray-400">Forbes</div>
					<div class="text-2xl font-bold text-gray-400">TechCrunch</div>
					<div class="text-2xl font-bold text-gray-400">Harvard Business Review</div>
					<div class="text-2xl font-bold text-gray-400">MIT Technology Review</div>
				</div>
			</div>
		</div>
	</div>
</section>
