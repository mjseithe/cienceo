<script lang="ts">
	import { createEventTimer } from 'svelte';
</script>

<footer class="bg-primary-dark text-white">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
		<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
			<!-- Brand -->
			<div>
				<h3 class="text-2xl font-bold mb-4">
					<span class="text-white">Cien</span><span class="text-accent">ceo</span>
				</h3>
				<p class="text-gray-300 text-sm leading-relaxed">
					Strategic advisor and mentor to technology company CEOs. Helping leaders navigate growth, transformation, and innovation.
				</p>
			</div>

			<!-- Quick Links -->
			<div>
				<h4 class="text-lg font-semibold mb-4 text-accent">Quick Links</h4>
				<ul class="space-y-2">
					{#each ['Background', 'Practice Area', 'Testimonials', 'Contact'] as link}
						<li>
							<a
								href="#{link.toLowerCase().replace(' ', '-')}"
								onclick={(e) => {
									e.preventDefault();
									document.getElementById(link.toLowerCase().replace(' ', '-'))?.scrollIntoView({ behavior: 'smooth' });
								}}
								class="text-gray-300 hover:text-accent transition-colors text-sm"
							>
								{link}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Contact Info -->
			<div>
				<h4 class="text-lg font-semibold mb-4 text-accent">Get in Touch</h4>
				<ul class="space-y-3 text-sm text-gray-300">
					<li class="flex items-center gap-2">
						<svg class="w-5 h-5 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
						</svg>
						<span>hello@cienceo.com</span>
					</li>
					<li class="flex items-center gap-2">
						<svg class="w-5 h-5 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
						</svg>
						<span>San Francisco, CA</span>
					</li>
				</ul>
				<!-- Social Links -->
				<div class="flex gap-4 mt-6">
					<a href="#" class="text-gray-300 hover:text-accent transition-colors" aria-label="LinkedIn">
						<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
							<path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
						</svg>
					</a>
					<a href="#" class="text-gray-300 hover:text-accent transition-colors" aria-label="Twitter">
						<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
							<path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
						</svg>
					</a>
				</div>
			</div>
		</div>

		<!-- Bottom Bar -->
		<div class="border-t border-gray-700 mt-8 pt-8 text-center text-sm text-gray-400">
			<p>&copy; {new Date().getFullYear()} Cienceo. All rights reserved.</p>
		</div>
	</div>
</footer>
