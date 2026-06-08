<script lang="ts">
	import { createEffect } from 'svelte';

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

	// Track active section on scroll
	function updateActiveSection() {
		const sections = navItems.map(item => item.href.replace('#', ''));
		const scrollPosition = window.scrollY + 100;

		for (let i = sections.length - 1; i >= 0; i--) {
			const section = document.getElementById(sections[i]);
			if (section && section.offsetTop <= scrollPosition) {
				activeSection = sections[i];
				break;
			}
		}
	}

	createEffect(() => {
		window.addEventListener('scroll', updateActiveSection);
		return () => window.removeEventListener('scroll', updateActiveSection);
	});
</script>

<nav class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-sm shadow-sm border-b border-gray-100">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex items-center justify-between h-16">
			<!-- Logo -->
			<div class="flex-shrink-0">
				<a href="#home" onclick={(e) => { e.preventDefault(); scrollToSection('home'); }} class="flex items-center gap-2">
					<span class="text-2xl font-bold text-primary">Cien</span>
					<span class="text-2xl font-bold text-accent">ceo</span>
				</a>
			</div>

			<!-- Desktop Navigation -->
			<div class="hidden md:flex items-center gap-1">
				{#each navItems as item}
					<button
						onclick={() => scrollToSection(item.href.replace('#', ''))}
						class:px-4
						class:py-2
						class:rounded-md
						class:text-sm
						class:font-medium
						class:transition-colors
						class:duration-200
						class:bg-primary={activeSection === item.href.replace('#', '')}
						class:text-white={activeSection === item.href.replace('#', '')}
						class:text-gray-700={activeSection !== item.href.replace('#', '')}
						class:hover:text-primary={activeSection !== item.href.replace('#', '')}
						class:hover:bg-gray-50={activeSection !== item.href.replace('#', '')}
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
	<div
		class:list={["fixed", "inset-0", "z-50", "md:hidden", {
			'opacity-100 visible': mobileMenuOpen,
			'opacity-0 invisible': !mobileMenuOpen
		}]}
		onclick={closeMobileMenu}
	>
		<div
			class:fixed
			class:right-0
			class:top-0
			class:bottom-0
			class:w-64
			class:bg-white
			class:shadow-xl
			class:p-4
			class:transform
			class:transition-transform
			class:duration-300
			class:ease-in-out
			class:translate-x-0={mobileMenuOpen}
			class:translate-x-full={!mobileMenuOpen}
			onclick={(e) => e.stopPropagation()}
		>
			<div class="flex flex-col gap-1 mt-16">
				{#each navItems as item}
					<button
						onclick={() => scrollToSection(item.href.replace('#', ''))}
						class:px-4
						class:py-3
						class:rounded-lg
						class:text-base
						class:font-medium
						class:transition-all
						class:duration-200
						class:text-left
						class:bg-primary={activeSection === item.href.replace('#', '')}
						class:text-white={activeSection === item.href.replace('#', '')}
						class:text-gray-700={activeSection !== item.href.replace('#', '')}
						class:hover:bg-gray-100={activeSection !== item.href.replace('#', '')}
						class:hover:text-primary={activeSection !== item.href.replace('#', '')}
					>
						{item.label}
					</button>
				{/each}
			</div>
		</div>
	</div>
</nav>
