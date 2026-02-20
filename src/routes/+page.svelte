<script lang="ts">
	import ApproachSection from '$lib/components/landing/ApproachSection.svelte';
	import BradburySection from '$lib/components/landing/BradburySection.svelte';
	import DualLensSection from '$lib/components/landing/DualLensSection.svelte';
	import HeroSection from '$lib/components/landing/HeroSection.svelte';
	import ProblemSection from '$lib/components/landing/ProblemSection.svelte';
	import WaitlistSection from '$lib/components/landing/WaitlistSection.svelte';
</script>

<svelte:head>
	<title>Billion | Understand What Government Is Doing</title>
	<meta
		name="description"
		content="Billion makes bills, court cases, and executive actions understandable through short-form civic content that leads you to the source."
	/>
</svelte:head>

<main
	class="min-h-screen bg-[radial-gradient(circle_at_20%_8%,rgba(74,124,255,0.16),transparent_32%),linear-gradient(180deg,var(--color-deep-navy)_0%,var(--color-slate)_100%)] px-4 pb-20 pt-12"
>
	<HeroSection />
	<ProblemSection />
	<ApproachSection />
	<DualLensSection />
	<BradburySection />
	<WaitlistSection />
</main>
