<script lang="ts">
	let email = $state('');
	let formStatus = $state<'idle' | 'loading' | 'success' | 'error'>('idle');

	function reveal(node: HTMLElement) {
		const observer = new IntersectionObserver(
			([entry]) => {
				if (entry.isIntersecting) {
					node.classList.add('visible');
					observer.disconnect();
				}
			},
			{ threshold: 0.1, rootMargin: '0px 0px -40px 0px' }
		);
		observer.observe(node);
		return { destroy: () => observer.disconnect() };
	}

	async function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		formStatus = 'loading';
		await new Promise((r) => setTimeout(r, 900));
		formStatus = 'success';
	}
</script>

<svelte:head>
	<title>Billion — Understand What Government Is Doing</title>
	<meta
		name="description"
		content="Billion makes bills, court cases, and executive actions understandable through short-form civic content that leads you back to the source."
	/>
</svelte:head>

<div class="min-h-screen bg-deep-navy">

	<!-- ── NAV ───────────────────────────────────────────────── -->
	<nav class="flex items-center justify-between max-w-[1120px] mx-auto px-6 py-5">
		<span class="font-display text-[22px] font-bold tracking-[-0.02em] text-white">Billion</span>
		<a
			class="font-body text-[15px] font-medium text-white/60 no-underline transition-colors duration-150 hover:text-white"
			href="#waitlist"
		>Get Early Access</a>
	</nav>

	<!-- ── HERO ──────────────────────────────────────────────── -->
	<section
		class="grid grid-cols-1 gap-10 max-w-[1120px] mx-auto px-6 pt-12 pb-18 animate-[fadeUp_0.6s_cubic-bezier(0.25,0.1,0.25,1)_both] md:grid-cols-[1.1fr_0.9fr] md:items-center md:pt-14 md:pb-20"
	>
		<div class="max-w-[580px]">
			<p class="text-[12px] font-medium tracking-[0.1em] uppercase text-general mb-[14px]">AI Civic Intelligence</p>
			<h1 class="font-display text-[clamp(2.2rem,5vw,3.75rem)] font-bold leading-[1.15] tracking-[-0.02em] mb-6 text-white">
				Know what government is doing before it changes your life.
			</h1>
			<p class="text-[18px] leading-[1.6] text-general max-w-[52ch] mb-7">
				Bills, court cases, and executive actions — explained clearly, linked to the source.
			</p>
			<div class="flex flex-wrap gap-4 items-center">
				<a
					class="inline-flex items-center justify-center h-[52px] px-7 bg-white text-black font-body text-[16px] font-medium rounded-full no-underline border-none cursor-pointer transition-[opacity,transform] duration-150 whitespace-nowrap active:scale-[0.98] active:opacity-90 disabled:opacity-50 disabled:cursor-not-allowed"
					href="#waitlist"
				>Get Early Access</a>
				<a
					class="inline-flex items-center justify-center h-[52px] px-1 text-white/60 font-body text-[16px] font-medium no-underline transition-colors duration-150 hover:text-white"
					href="#approach"
				>See How It Works</a>
			</div>
		</div>

		<div
			class="relative max-h-[480px] overflow-hidden flex flex-col gap-3 animate-[fadeUp_0.6s_cubic-bezier(0.25,0.1,0.25,1)_0.15s_both]"
			aria-label="Billion content preview"
		>
			<div class="bg-slate border border-border-subtle border-l-[3px] border-l-bill rounded-[14px] p-5">
				<div class="flex items-center justify-between mb-[10px]">
					<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-bill">BILL</span>
					<span class="text-[12px] text-general font-body font-medium">2h ago</span>
				</div>
				<h3 class="font-editorial text-[1.1rem] font-normal leading-[1.35] mb-2 text-white">H.R. 4312: National Housing Stabilization Act</h3>
				<p class="text-[14px] leading-[1.5] text-general mb-[10px]">What changed in committee, who supports it, and what it means for your state.</p>
				<p class="text-[12px] font-medium text-white/30 m-0">Congress.gov · Passed Committee</p>
			</div>

			<div class="bg-slate border border-border-subtle border-l-[3px] border-l-case rounded-[14px] p-5">
				<div class="flex items-center justify-between mb-[10px]">
					<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-case">CASE</span>
					<span class="text-[12px] text-general font-body font-medium">5h ago</span>
				</div>
				<h3 class="font-editorial text-[1.1rem] font-normal leading-[1.35] mb-2 text-white">U.S. v. Westfield Utilities</h3>
				<p class="text-[14px] leading-[1.5] text-general mb-[10px]">Majority and dissent logic, plain language, side by side.</p>
				<p class="text-[12px] font-medium text-white/30 m-0">U.S. Court of Appeals, 9th Circuit</p>
			</div>

			<div class="bg-slate border border-border-subtle border-l-[3px] border-l-executive rounded-[14px] p-5 opacity-70">
				<div class="flex items-center justify-between mb-[10px]">
					<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-executive">ORDER</span>
					<span class="text-[12px] text-general font-body font-medium">8h ago</span>
				</div>
				<h3 class="font-editorial text-[1.1rem] font-normal leading-[1.35] mb-2 text-white">E.O. 14192: Department of Government Efficiency</h3>
				<p class="text-[14px] leading-[1.5] text-general mb-[10px]">What it authorizes, which agencies are affected, and open legal challenges.</p>
			</div>

			<div
				class="absolute inset-x-0 bottom-0 h-[100px] bg-gradient-to-t from-deep-navy to-transparent pointer-events-none"
				aria-hidden="true"
			></div>
		</div>
	</section>

	<!-- ── PROBLEM ───────────────────────────────────────────── -->
	<section class="section max-w-[1120px] mx-auto px-6 py-14 border-t border-border-subtle md:py-18" use:reveal>
		<div class="grid grid-cols-1 gap-8 md:grid-cols-2 md:items-start md:gap-16">
			<div>
				<p class="text-[12px] font-medium tracking-[0.1em] uppercase text-general mb-[14px]">The Problem</p>
				<h2 class="font-display text-[clamp(1.8rem,3.5vw,2.75rem)] font-normal leading-[1.18] tracking-[-0.01em] text-white m-0">
					Public information exists.<br />Public understanding doesn't.
				</h2>
			</div>
			<p class="text-[18px] leading-[1.65] text-white/75 m-0 pt-1 md:pt-2">
				Most people hear about policy through headlines, not source material. Billion closes that gap.
			</p>
		</div>
	</section>

	<!-- ── APPROACH ──────────────────────────────────────────── -->
	<section class="section max-w-[1120px] mx-auto px-6 py-14 border-t border-border-subtle md:py-18" id="approach" use:reveal>
		<h2 class="font-display text-[clamp(1.8rem,3.5vw,2.75rem)] font-normal leading-[1.18] tracking-[-0.01em] text-white m-0 text-center">
			One civic feed.<br />Three source systems.
		</h2>

		<div class="mt-10 grid grid-cols-1 gap-[14px] md:grid-cols-[1.5fr_1fr_1fr]">
			<div class="bg-slate border border-border-subtle border-t-[2px] border-t-bill rounded-[14px] p-7">
				<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-bill">BILL</span>
				<h3 class="font-editorial text-[1.25rem] font-bold leading-[1.3] text-white mt-[14px] mb-[10px]">Congressional Legislation</h3>
				<p class="text-[15px] leading-[1.6] text-general m-0">
					Tracks sponsorship, status, and text changes. Explainers generate when source content changes — not on a schedule.
				</p>
				<p class="text-[12px] font-medium text-bill mt-4 mb-0 opacity-85">4,392 bills tracked in the current Congress</p>
			</div>

			<div class="bg-slate border border-border-subtle border-t-[2px] border-t-executive rounded-[14px] p-7">
				<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-executive">ORDER</span>
				<h3 class="font-editorial text-[1.25rem] font-bold leading-[1.3] text-white mt-[14px] mb-[10px]">Executive Actions</h3>
				<p class="text-[15px] leading-[1.6] text-general m-0">
					Orders, memoranda, and proclamations pulled directly from official White House publications.
				</p>
			</div>

			<div class="bg-slate border border-border-subtle border-t-[2px] border-t-case rounded-[14px] p-7">
				<span class="inline-flex items-center h-6 px-[10px] rounded-[6px] text-[11px] font-medium tracking-[0.06em] uppercase text-white bg-case">CASE</span>
				<h3 class="font-editorial text-[1.25rem] font-bold leading-[1.3] text-white mt-[14px] mb-[10px]">Federal Court Cases</h3>
				<p class="text-[15px] leading-[1.6] text-general m-0">
					Filings and decisions surfaced with plain-language analysis and timeline context.
				</p>
			</div>
		</div>
	</section>

	<!-- ── DUAL LENS ─────────────────────────────────────────── -->
	<section class="section max-w-[1120px] mx-auto px-6 py-14 border-t border-border-subtle md:py-18" use:reveal>
		<h2 class="font-display text-[clamp(1.8rem,3.5vw,2.75rem)] font-normal leading-[1.18] tracking-[-0.01em] text-white m-0 text-center">
			Two readings.<br />Every topic.
		</h2>
		<p class="text-[18px] leading-[1.6] text-general max-w-[52ch] mt-[14px] mb-0 mx-auto text-center">
    		Billion surfaces analysis from across the political spectrum — side by side, transparently
    		labeled, never merged into a false middle.
		</p>

		<div class="grid grid-cols-1 gap-[14px] mt-8 md:grid-cols-2">
			<div class="bg-slate border border-border-subtle border-t-[2px] border-t-executive rounded-[14px] p-8 relative">
				<p class="text-[11px] font-medium tracking-[0.1em] uppercase text-executive mb-[18px] m-0">Institutional Lens</p>
				<blockquote class="font-editorial text-[1.15rem] font-normal leading-[1.45] text-white mb-4 p-0 border-none m-0">
					"Expanding federal housing mandates risks crowding out private investment and local zoning
					authority."
				</blockquote>
				<p class="text-[15px] leading-[1.6] text-general mb-5 m-0">
				Frames policy around institutional stability, federalism, and legal precedent established
				by prior congresses.
				</p>
				<p class="text-[12px] font-medium text-white/25 m-0">Re: H.R. 4312 · Institute for Housing Policy Research</p>
			</div>

			<div class="bg-[rgba(74,124,255,0.05)] border border-border-subtle border-t-[2px] border-t-bill rounded-[14px] p-8 relative">
				<p class="text-[11px] font-medium tracking-[0.1em] uppercase text-bill mb-[18px] m-0">Impact Lens</p>
				<blockquote class="font-editorial text-[1.15rem] font-normal leading-[1.45] text-white mb-4 p-0 border-none m-0">
					"40 million Americans lack stable housing — federal intervention is the only mechanism at
					scale."
				</blockquote>
				<p class="text-[15px] leading-[1.6] text-general mb-5 m-0">
				Frames policy around impact on households, local economies, and the civil liberties of
				renters and low-income communities.
				</p>
				<p class="text-[12px] font-medium text-white/25 m-0">Re: H.R. 4312 · National Housing Justice Coalition</p>
			</div>
		</div>
	</section>

	<!-- ── BRADBURY ───────────────────────────────────────────── -->
	<section class="section max-w-[1120px] mx-auto px-6 py-14 border-t border-border-subtle text-center md:py-18" use:reveal>
		<h2 class="font-display text-[clamp(2rem,4vw,3.5rem)] font-normal leading-[1.2] tracking-[-0.01em] text-white mx-auto mb-5 max-w-[18ch]">
			Every summary should lead to <em class="italic">deeper reading.</em>
		</h2>
		<p class="text-[18px] leading-[1.7] text-general max-w-[48ch] mx-auto mb-7">
		We are not a summarization engine.<br/><br/>Every piece of content Billion produces functions as an
		invitation — to the bill text, the filing, the full decision. If you finish reading and feel
		like you've got the gist, we've failed.
		</p>
		<a
			class="inline-flex items-center justify-center h-[52px] px-7 bg-white text-black font-body text-[16px] font-medium rounded-full no-underline border-none cursor-pointer transition-[opacity,transform] duration-150 whitespace-nowrap active:scale-[0.98] active:opacity-90"
			href="#waitlist"
		>Explore the source</a>
	</section>

	<!-- ── WAITLIST ───────────────────────────────────────────── -->
	<section class="section max-w-[1120px] mx-auto px-6 py-14 border-t border-border-subtle text-center md:py-18" id="waitlist" use:reveal>
		{#if formStatus === 'success'}
			<div class="animate-[fadeUp_0.4s_cubic-bezier(0.25,0.1,0.25,1)_both]">
				<div class="w-[52px] h-[52px] rounded-full border border-success text-success flex items-center justify-center mx-auto mb-6">
					<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
						<polyline points="20 6 9 17 4 12" />
					</svg>
				</div>
				<h2 class="font-display text-[clamp(1.8rem,3vw,2.8rem)] font-bold tracking-[-0.02em] mb-3 text-white">You're on the list.</h2>
				<p class="text-[18px] leading-[1.6] text-general m-0">We'll reach out when early access opens.</p>
			</div>
		{:else}
			<p class="text-[12px] font-medium tracking-[0.1em] uppercase text-general mb-[14px] text-center">Early Access</p>
			<h2 class="font-display text-[clamp(2rem,4vw,3.2rem)] font-bold leading-[1.2] tracking-[-0.02em] text-white mb-4">Be first when Billion opens.</h2>
			<p class="text-[18px] leading-[1.6] text-general mx-auto mb-7 max-w-[44ch]">
				Early access, updates, and pilot invites.
			</p>
			<form class="flex flex-col gap-[10px] max-w-[480px] mx-auto sm:flex-row" onsubmit={handleSubmit}>
				<label for="email" class="absolute w-px h-px p-0 -m-px overflow-hidden [clip:rect(0,0,0,0)] whitespace-nowrap border-0">Email address</label>
				<input
					id="email"
					type="email"
					name="email"
					placeholder="you@example.com"
					required
					bind:value={email}
					disabled={formStatus === 'loading'}
					class="flex-1 h-[52px] bg-slate border border-white/10 rounded-[12px] px-[18px] font-body text-[16px] text-white transition-[border-color] duration-150 placeholder:text-white/30 focus:outline-none focus:border-border-focus disabled:opacity-50"
				/>
				<button
					type="submit"
					disabled={formStatus === 'loading'}
					class="shrink-0 inline-flex items-center justify-center h-[52px] px-7 bg-white text-black font-body text-[16px] font-medium rounded-full border-none cursor-pointer transition-[opacity,transform] duration-150 whitespace-nowrap active:scale-[0.98] active:opacity-90 disabled:opacity-50 disabled:cursor-not-allowed"
				>
					{formStatus === 'loading' ? 'Joining…' : 'Join Waitlist'}
				</button>
			</form>
			{#if formStatus === 'error'}
				<p class="mt-3 text-[14px] text-error">Something went wrong. Please try again.</p>
			{/if}
		{/if}
	</section>

	<!-- ── FOOTER ─────────────────────────────────────────────── -->
	<footer class="flex items-center justify-between max-w-[1120px] mx-auto px-6 py-8 border-t border-border-subtle">
		<span class="font-display text-[18px] font-bold text-white/40">Billion</span>
		<p class="text-[13px] text-white/25 m-0">© 2026 Billion. All rights reserved.</p>
	</footer>

</div>

<style>
	/* Reveal animation — driven by JS adding .visible class */
	:global(.section) {
		opacity: 0;
		transform: translateY(20px);
		transition:
			opacity 0.6s cubic-bezier(0.25, 0.1, 0.25, 1),
			transform 0.6s cubic-bezier(0.25, 0.1, 0.25, 1);
	}
	:global(.section.visible) {
		opacity: 1;
		transform: translateY(0);
	}
</style>
