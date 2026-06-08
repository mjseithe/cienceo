<script lang="ts">
	import { onMount } from 'svelte';

	const navItems = [
		{ label: 'Home', href: '#home' },
		{ label: 'Background', href: '#background' },
		{ label: 'Practice Area', href: '#practice-area' },
		{ label: 'Testimonials', href: '#testimonials' },
		{ label: 'Contact', href: '#contact' }
	];

	let mobileMenuOpen = $state(false);
	let activeSection = $state('home');

	function toggleMobileMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}

	function closeMobileMenu() {
		mobileMenuOpen = false;
	}

	function scrollToSection(id: string) {
		const element = document.getElementById(id);
		if (element) {
			element.scrollIntoView({ behavior: 'smooth' });
		}
		closeMobileMenu();
	}

	function updateActiveSection() {
		const sections = navItems.map((item) => item.href.replace('#', ''));
		const scrollPosition = window.scrollY + 100;

		for (let i = sections.length - 1; i >= 0; i--) {
			const section = document.getElementById(sections[i]);
			if (section && section.offsetTop <= scrollPosition) {
				activeSection = sections[i];
				break;
			}
		}
	}

	onMount(() => {
		window.addEventListener('scroll', updateActiveSection);
		return () => window.removeEventListener('scroll', updateActiveSection);
	});
</script>

<nav class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-sm shadow-sm border-b border-gray-100">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex items-center justify-between h-16">
			<!-- Logo -->
			<div class="flex-shrink-0">
				<a
					href="#home"
					onclick={(e) => {
						e.preventDefault();
						scrollToSection('home');
					}}
					class="flex items-center gap-2"
				>
					<span class="text-2xl font-bold text-primary">Cien</span>
					<span class="text-2xl font-bold text-accent">ceo</span>
				</a>
			</div>

			<!-- Desktop Navigation -->
			<div class="hidden md:flex items-center gap-1">
				{#each navItems as item}
					{@const sectionId = item.href.replace('#', '')}
					<button
						onclick={() => scrollToSection(sectionId)}
						class="px-4 py-2 rounded-md text-sm font-medium transition-colors duration-200 {activeSection === sectionId
							? 'bg-primary text-white'
							: 'text-gray-700 hover:text-primary hover:bg-gray-50'}"
					>
						{item.label}
					</button>
				{/each}
			</div>

			<!-- Mobile Menu Button -->
			<div class="md:hidden">
				<button
					onclick={toggleMobileMenu}
					class="inline-flex items-center justify-center p-2 rounded-md text-gray-700 hover:text-primary hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-primary transition-colors"
					aria-expanded={mobileMenuOpen}
					aria-label="Toggle mobile menu"
				>
					{#if mobileMenuOpen}
						<svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
						</svg>
					{:else}
						<svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
						</svg>
					{/if}
				</button>
			</div>
		</div>
	</div>

	<!-- Mobile Menu -->
	<!-- svelte-ignore a11y_click_events_have_key_events -->
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		class="fixed inset-0 z-50 md:hidden {mobileMenuOpen ? 'opacity-100 visible' : 'opacity-0 invisible'}"
		onclick={closeMobileMenu}
	>
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			class="fixed right-0 top-0 bottom-0 w-64 bg-white shadow-xl p-4 transform transition-transform duration-300 ease-in-out {mobileMenuOpen
				? 'translate-x-0'
				: 'translate-x-full'}"
			onclick={(e) => e.stopPropagation()}
		>
			<div class="flex flex-col gap-1 mt-16">
				{#each navItems as item}
					{@const sectionId = item.href.replace('#', '')}
					<button
						onclick={() => scrollToSection(sectionId)}
						class="px-4 py-3 rounded-lg text-base font-medium transition-all duration-200 text-left {activeSection === sectionId
							? 'bg-primary text-white'
							: 'text-gray-700 hover:bg-gray-100 hover:text-primary'}"
					>
						{item.label}
					</button>
				{/each}
			</div>
		</div>
	</div>
</nav>
