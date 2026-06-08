<script lang="ts">
	import ContactForm from './ContactForm.svelte';
</script>

<section id="contact" class="py-24 bg-gray-50">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
			<!-- Left Column - Info -->
			<div>
				<span class="inline-block px-4 py-1.5 bg-primary/10 text-primary text-sm font-semibold rounded-full mb-4">
					Get in Touch
				</span>
				<h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-6">
					Let's Start a Conversation
				</h2>
				<p class="text-xl text-gray-600 mb-8 leading-relaxed">
					Whether you're facing a specific challenge or exploring strategic opportunities, I'd welcome the chance to discuss how I can help.
				</p>

				<!-- Contact Info -->
				<div class="space-y-6 mb-8">
					<div class="flex items-start gap-4">
						<div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center flex-shrink-0">
							<svg class="w-6 h-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
							</svg>
						</div>
						<div>
							<h4 class="font-semibold text-gray-900 mb-1">Email</h4>
							<p class="text-gray-600">hello@strategicadvisor.com</p>
						</div>
					</div>

					<div class="flex items-start gap-4">
						<div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center flex-shrink-0">
							<svg class="w-6 h-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
							</svg>
						</div>
						<div>
							<h4 class="font-semibold text-gray-900 mb-1">Location</h4>
							<p class="text-gray-600">San Francisco, CA (Remote Available)</p>
						</div>
					</div>

					<div class="flex items-start gap-4">
						<div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center flex-shrink-0">
							<svg class="w-6 h-6 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
							</svg>
						</div>
						<div>
							<h4 class="font-semibold text-gray-900 mb-1">Availability</h4>
							<p class="text-gray-600">Monday - Friday, 9am - 6pm PST</p>
						</div>
					</div>
				</div>

				<!-- Social Links -->
				<div>
					<h4 class="font-semibold text-gray-900 mb-4">Connect on LinkedIn</h4>
					<a
						href="https://linkedin.com"
						target="_blank"
						rel="noopener noreferrer"
						class="inline-flex items-center gap-2 px-6 py-3 bg-[#0077B5] text-white font-semibold rounded-lg hover:bg-[#005a87] transition-colors"
					>
						<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
							<path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z" />
						</svg>
						View Profile
					</a>
				</div>
			</div>

			<!-- Right Column - Form -->
			<div>
				<ContactForm />
			</div>
		</div>
	</div>
</section>
