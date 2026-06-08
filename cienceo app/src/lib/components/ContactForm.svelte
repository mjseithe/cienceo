<script lang="ts">
	interface FormData {
		name: string;
		email: string;
		company: string;
		message: string;
	}

	let formData = $state<FormData>({
		name: '',
		email: '',
		company: '',
		message: ''
	});

	let submitting = $state(false);
	let submitted = $state(false);
	let errors = $state<Partial<Record<keyof FormData, string>>>({});

	function validate(): boolean {
		const newErrors: Partial<Record<keyof FormData, string>> = {};

		if (!formData.name.trim()) {
			newErrors.name = 'Name is required';
		}

		if (!formData.email.trim()) {
			newErrors.email = 'Email is required';
		} else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
			newErrors.email = 'Please enter a valid email';
		}

		if (!formData.message.trim()) {
			newErrors.message = 'Message is required';
		}

		errors = newErrors;
		return Object.keys(newErrors).length === 0;
	}

	async function handleSubmit() {
		if (!validate()) return;

		submitting = true;

		// Simulate API call - replace with actual endpoint
		try {
			await new Promise(resolve => setTimeout(resolve, 1500));
			// TODO: Replace with actual API call
			// const response = await fetch('/api/contact', {
			// 	method: 'POST',
			// 	headers: { 'Content-Type': 'application/json' },
			// 	body: JSON.stringify(formData)
			// });

			submitted = true;
			formData = { name: '', email: '', company: '', message: '' };

			// Reset success message after 5 seconds
			setTimeout(() => {
				submitted = false;
			}, 5000);
		} catch (error) {
			console.error('Form submission error:', error);
		} finally {
			submitting = false;
		}
	}
</script>

<div class="bg-white rounded-2xl shadow-lg p-8 md:p-10">
	{#if submitted}
		<div class="bg-green-50 border border-green-200 rounded-xl p-6 text-center">
			<svg class="w-12 h-12 text-green-500 mx-auto mb-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
			</svg>
			<h4 class="text-lg font-semibold text-green-800 mb-1">Message Sent!</h4>
			<p class="text-green-600 text-sm">Thank you for reaching out. I'll get back to you within 24 hours.</p>
		</div>
	{:else}
		<form onsubmit={(e) => { e.preventDefault(); handleSubmit(); }} class="space-y-6">
			<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
				<!-- Name -->
				<div>
					<label for="name" class="block text-sm font-medium text-gray-700 mb-2">
						Name <span class="text-red-500">*</span>
					</label>
					<input
						id="name"
						type="text"
						bind:value={formData.name}
						class="w-full px-4 py-3 border rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors {{
							errors.name ? 'border-red-500' : 'border-gray-300'
						}}"
						placeholder="Your full name"
						required
					/>
					{#if errors.name}
						<p class="mt-1 text-sm text-red-500">{errors.name}</p>
					{/if}
				</div>

				<!-- Email -->
				<div>
					<label for="email" class="block text-sm font-medium text-gray-700 mb-2">
						Email <span class="text-red-500">*</span>
					</label>
					<input
						id="email"
						type="email"
						bind:value={formData.email}
						class="w-full px-4 py-3 border rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors {{
							errors.email ? 'border-red-500' : 'border-gray-300'
						}}"
						placeholder="your@email.com"
						required
					/>
					{#if errors.email}
						<p class="mt-1 text-sm text-red-500">{errors.email}</p>
					{/if}
				</div>
			</div>

			<!-- Company -->
			<div>
				<label for="company" class="block text-sm font-medium text-gray-700 mb-2">
					Company <span class="text-gray-400">(optional)</span>
				</label>
				<input
					id="company"
					type="text"
					bind:value={formData.company}
					class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors"
					placeholder="Your company name"
				/>
			</div>

			<!-- Message -->
			<div>
				<label for="message" class="block text-sm font-medium text-gray-700 mb-2">
					Message <span class="text-red-500">*</span>
				</label>
				<textarea
					id="message"
					bind:value={formData.message}
					rows="5"
					class="w-full px-4 py-3 border rounded-lg focus:ring-2 focus:ring-primary focus:border-primary transition-colors resize-none {{
						errors.message ? 'border-red-500' : 'border-gray-300'
					}}"
					placeholder="Tell me about your challenges and how I can help..."
					required
				></textarea>
				{#if errors.message}
					<p class="mt-1 text-sm text-red-500">{errors.message}</p>
				{/if}
			</div>

			<!-- Submit Button -->
			<button
				type="submit"
				disabled={submitting}
				class="w-full md:w-auto px-8 py-3 bg-primary text-white font-semibold rounded-lg hover:bg-primary-light transition-all duration-200 disabled:opacity-50 disabled:cursor-not-allowed focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2"
			>
				{#if submitting}
					<span class="flex items-center justify-center gap-2">
						<svg class="animate-spin h-5 w-5" viewBox="0 0 24 24">
							<circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4" fill="none" />
							<path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z" />
						</svg>
						Sending...
					</span>
				{:else}
					Send Message
				{/if}
			</button>
		</form>
	{/if}
</div>
