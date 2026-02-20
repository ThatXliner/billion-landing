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

<div class="page">

	<!-- ── NAV ───────────────────────────────────────────────── -->
	<nav class="nav">
		<span class="nav-wordmark">Billion</span>
		<a class="nav-cta" href="#waitlist">Get Early Access</a>
	</nav>

	<!-- ── HERO ──────────────────────────────────────────────── -->
	<section class="hero">
		<div class="hero-copy">
			<p class="eyebrow">AI Civic Intelligence</p>
			<h1 class="hero-headline">
				Know what government is doing before it changes your life.
			</h1>
			<p class="hero-sub">
				Billion turns bills, court cases, and executive actions into short videos and interactive
				explainers — clear, balanced, and linked to the source.
			</p>
			<div class="hero-actions">
				<a class="btn-primary" href="#waitlist">Get Early Access</a>
				<a class="btn-secondary" href="#approach">See How It Works</a>
			</div>
		</div>

		<div class="hero-preview" aria-label="Billion content preview">
			<div class="feed-card feed-card--bill">
				<div class="card-header">
					<span class="badge badge--bill">BILL</span>
					<span class="card-time">2h ago</span>
				</div>
				<h3 class="card-title">H.R. 4312: National Housing Stabilization Act</h3>
				<p class="card-desc">What changed in committee, who supports it, and what it means for your state.</p>
				<p class="card-meta">Congress.gov · Passed Committee</p>
			</div>

			<div class="feed-card feed-card--case">
				<div class="card-header">
					<span class="badge badge--case">CASE</span>
					<span class="card-time">5h ago</span>
				</div>
				<h3 class="card-title">U.S. v. Westfield Utilities</h3>
				<p class="card-desc">Majority and dissent logic, plain language, side by side.</p>
				<p class="card-meta">U.S. Court of Appeals, 9th Circuit</p>
			</div>

			<div class="feed-card feed-card--order feed-card--partial">
				<div class="card-header">
					<span class="badge badge--order">ORDER</span>
					<span class="card-time">8h ago</span>
				</div>
				<h3 class="card-title">E.O. 14192: Department of Government Efficiency</h3>
				<p class="card-desc">What it authorizes, which agencies are affected, and open legal challenges.</p>
			</div>

			<div class="preview-fade" aria-hidden="true"></div>
		</div>
	</section>

	<!-- ── PROBLEM ───────────────────────────────────────────── -->
	<section class="section section--problem" use:reveal>
		<div class="problem-grid">
			<div>
				<p class="eyebrow">The Problem</p>
				<h2 class="section-headline">
					Public information exists.<br />Public understanding doesn't.
				</h2>
			</div>
			<p class="problem-body">
				Most Americans hear about policy through headlines, not source material. Billion closes that
				gap — making institutional information readable, watchable, and worth opening.
			</p>
		</div>
	</section>

	<!-- ── APPROACH ──────────────────────────────────────────── -->
	<section class="section" id="approach" use:reveal>
		<h2 class="section-headline section-headline--centered">
			One civic feed.<br />Three source systems.
		</h2>

		<div class="approach-grid">
			<!-- Bill — primary, wider -->
			<div class="approach-card approach-card--bill approach-card--primary">
				<span class="badge badge--bill">BILL</span>
				<h3 class="approach-card-title">Congressional Legislation</h3>
				<p class="approach-card-body">
					Tracks sponsorship, status, and text changes. Generates explainers only when source
					content changes — not on a schedule.
				</p>
				<p class="approach-stat">4,392 bills tracked in the current Congress</p>
			</div>

			<div class="approach-card approach-card--order">
				<span class="badge badge--order">ORDER</span>
				<h3 class="approach-card-title">Executive Actions</h3>
				<p class="approach-card-body">
					Orders, memoranda, proclamations, and briefings pulled directly from official White House
					publications.
				</p>
			</div>

			<div class="approach-card approach-card--case">
				<span class="badge badge--case">CASE</span>
				<h3 class="approach-card-title">Federal Court Cases</h3>
				<p class="approach-card-body">
					Filings and decisions surfaced with plain-language analysis and timeline context.
				</p>
			</div>
		</div>
	</section>

	<!-- ── DUAL LENS ─────────────────────────────────────────── -->
	<section class="section" use:reveal>
		<p class="eyebrow eyebrow--centered">On every topic, two readings.</p>
		<h2 class="section-headline section-headline--centered">
			Multiple viewpoints,<br />equal visual weight.
		</h2>
		<p class="section-sub">
			Billion surfaces analysis from across the political spectrum — side by side, transparently
			labeled, never merged into a false middle.
		</p>

		<div class="lens-grid">
			<div class="lens-card lens-card--institutional">
				<p class="lens-label">Institutional Lens</p>
				<blockquote class="lens-quote">
					"Expanding federal housing mandates risks crowding out private investment and local zoning
					authority."
				</blockquote>
				<p class="lens-body">
					Frames policy around institutional stability, federalism, and legal precedent established
					by prior congresses.
				</p>
				<p class="lens-source">Re: H.R. 4312 · Institute for Housing Policy Research</p>
			</div>

			<div class="lens-card lens-card--impact">
				<p class="lens-label">Impact Lens</p>
				<blockquote class="lens-quote">
					"40 million Americans lack stable housing — federal intervention is the only mechanism at
					scale."
				</blockquote>
				<p class="lens-body">
					Frames policy around impact on households, local economies, and the civil liberties of
					renters and low-income communities.
				</p>
				<p class="lens-source">Re: H.R. 4312 · National Housing Justice Coalition</p>
			</div>
		</div>
	</section>

	<!-- ── BRADBURY ───────────────────────────────────────────── -->
	<section class="section section--bradbury" use:reveal>
		<h2 class="bradbury-headline">
			Every summary should lead to <em>deeper reading.</em>
		</h2>
		<p class="bradbury-body">
			We are not a summarization engine. Every piece of content Billion produces functions as an
			invitation — to the bill text, the filing, the full decision. If you finish reading and feel
			like you've got the gist, we've failed.
		</p>
		<a class="btn-primary" href="#waitlist">Explore the source</a>
	</section>

	<!-- ── WAITLIST ───────────────────────────────────────────── -->
	<section class="section section--waitlist" id="waitlist" use:reveal>
		{#if formStatus === 'success'}
			<div class="success-block">
				<div class="success-icon">
					<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
						<polyline points="20 6 9 17 4 12" />
					</svg>
				</div>
				<h2 class="success-heading">You're on the list.</h2>
				<p class="success-sub">We'll reach out when early access opens.</p>
			</div>
		{:else}
			<p class="eyebrow eyebrow--centered">Early Access</p>
			<h2 class="waitlist-headline">Be first when Billion opens.</h2>
			<p class="waitlist-sub">
				Join the waitlist for early access, product updates, and pilot program invites.
			</p>
			<form class="waitlist-form" onsubmit={handleSubmit}>
				<label for="email" class="sr-only">Email address</label>
				<input
					id="email"
					type="email"
					name="email"
					placeholder="you@example.com"
					required
					bind:value={email}
					disabled={formStatus === 'loading'}
					class="waitlist-input"
				/>
				<button
					type="submit"
					disabled={formStatus === 'loading'}
					class="btn-primary waitlist-btn"
				>
					{formStatus === 'loading' ? 'Joining…' : 'Join Waitlist'}
				</button>
			</form>
			{#if formStatus === 'error'}
				<p class="form-error">Something went wrong. Please try again.</p>
			{/if}
		{/if}
	</section>

	<!-- ── FOOTER ─────────────────────────────────────────────── -->
	<footer class="footer">
		<span class="footer-wordmark">Billion</span>
		<p class="footer-copy">© 2026 Billion. All rights reserved.</p>
	</footer>

</div>

<style>
	/* ── PAGE SHELL ─────────────────────────────────────────── */
	.page {
		min-height: 100vh;
		background: var(--color-deep-navy);
	}

	/* ── NAV ─────────────────────────────────────────────────── */
	.nav {
		display: flex;
		align-items: center;
		justify-content: space-between;
		max-width: 1120px;
		margin: 0 auto;
		padding: 28px 24px;
	}
	.nav-wordmark {
		font-family: var(--font-display);
		font-size: 22px;
		font-weight: 700;
		letter-spacing: -0.02em;
		color: #fff;
	}
	.nav-cta {
		font-family: var(--font-body);
		font-size: 15px;
		font-weight: 500;
		color: rgba(255, 255, 255, 0.6);
		text-decoration: none;
		transition: color 150ms;
	}
	.nav-cta:hover {
		color: #fff;
	}

	/* ── HERO ────────────────────────────────────────────────── */
	.hero {
		display: grid;
		grid-template-columns: 1fr;
		gap: 56px;
		max-width: 1120px;
		margin: 0 auto;
		padding: 64px 24px 96px;
		animation: fadeUp 0.6s cubic-bezier(0.25, 0.1, 0.25, 1) both;
	}
	@media (min-width: 960px) {
		.hero {
			grid-template-columns: 1.1fr 0.9fr;
			align-items: center;
			padding: 80px 24px 120px;
		}
	}

	.hero-copy {
		max-width: 580px;
	}
	.hero-headline {
		font-family: var(--font-display);
		font-size: clamp(2.2rem, 5vw, 3.75rem);
		font-weight: 700;
		line-height: 1.15;
		letter-spacing: -0.02em;
		margin: 0 0 24px;
		color: #fff;
	}
	.hero-sub {
		font-size: 18px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		max-width: 52ch;
		margin: 0 0 40px;
	}
	.hero-actions {
		display: flex;
		flex-wrap: wrap;
		gap: 16px;
		align-items: center;
	}

	/* ── FEED PREVIEW ─────────────────────────────────────────── */
	.hero-preview {
		position: relative;
		max-height: 480px;
		overflow: hidden;
		display: flex;
		flex-direction: column;
		gap: 12px;
		animation: fadeUp 0.6s cubic-bezier(0.25, 0.1, 0.25, 1) 0.15s both;
	}
	.preview-fade {
		position: absolute;
		inset: auto 0 0 0;
		height: 100px;
		background: linear-gradient(to top, var(--color-deep-navy), transparent);
		pointer-events: none;
	}

	.feed-card {
		background: var(--color-slate);
		border: 1px solid var(--color-border-subtle);
		border-radius: 14px;
		padding: 20px;
		border-left-width: 3px;
	}
	.feed-card--bill   { border-left-color: var(--color-bill); }
	.feed-card--case   { border-left-color: var(--color-case); }
	.feed-card--order  { border-left-color: var(--color-executive); }
	.feed-card--partial { opacity: 0.7; }

	.card-header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-bottom: 10px;
	}
	.card-time {
		font-size: 12px;
		color: var(--color-text-secondary);
		font-family: var(--font-body);
		font-weight: 500;
	}
	.card-title {
		font-family: var(--font-editorial);
		font-size: 1.1rem;
		font-weight: 700;
		line-height: 1.35;
		margin: 0 0 8px;
		color: #fff;
	}
	.card-desc {
		font-size: 14px;
		line-height: 1.5;
		color: var(--color-text-secondary);
		margin: 0 0 10px;
	}
	.card-meta {
		font-size: 12px;
		font-weight: 500;
		color: rgba(255, 255, 255, 0.3);
		margin: 0;
	}

	/* ── SECTION BASE ────────────────────────────────────────── */
	.section {
		max-width: 1120px;
		margin: 0 auto;
		padding: 80px 24px;
		border-top: 1px solid var(--color-border-subtle);
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
	@media (min-width: 960px) {
		.section {
			padding: 100px 24px;
		}
	}

	/* ── TYPOGRAPHY PRIMITIVES ───────────────────────────────── */
	.eyebrow {
		font-size: 12px;
		font-weight: 500;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		color: var(--color-text-secondary);
		margin: 0 0 14px;
	}
	.eyebrow--centered { text-align: center; }

	.section-headline {
		font-family: var(--font-display);
		font-size: clamp(1.8rem, 3.5vw, 2.75rem);
		font-weight: 700;
		line-height: 1.18;
		letter-spacing: -0.02em;
		color: #fff;
		margin: 0;
	}
	.section-headline--centered { text-align: center; }

	.section-sub {
		font-size: 18px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		max-width: 52ch;
		margin: 20px auto 0;
		text-align: center;
	}

	/* ── PROBLEM ─────────────────────────────────────────────── */
	.problem-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 32px;
	}
	@media (min-width: 720px) {
		.problem-grid {
			grid-template-columns: 1fr 1fr;
			align-items: start;
			gap: 64px;
		}
	}
	.problem-body {
		font-size: 18px;
		line-height: 1.65;
		color: rgba(255, 255, 255, 0.75);
		margin: 0;
		padding-top: 4px;
	}
	@media (min-width: 720px) {
		.problem-body { padding-top: 8px; }
	}

	/* ── APPROACH ────────────────────────────────────────────── */
	.approach-grid {
		margin-top: 56px;
		display: grid;
		grid-template-columns: 1fr;
		gap: 14px;
	}
	@media (min-width: 720px) {
		.approach-grid {
			grid-template-columns: 1.5fr 1fr 1fr;
		}
	}

	.approach-card {
		background: var(--color-slate);
		border: 1px solid var(--color-border-subtle);
		border-radius: 14px;
		padding: 28px;
		border-top-width: 2px;
	}
	.approach-card--bill  { border-top-color: var(--color-bill); }
	.approach-card--order { border-top-color: var(--color-executive); }
	.approach-card--case  { border-top-color: var(--color-case); }

	.approach-card-title {
		font-family: var(--font-editorial);
		font-size: 1.25rem;
		font-weight: 700;
		line-height: 1.3;
		color: #fff;
		margin: 14px 0 10px;
	}
	.approach-card-body {
		font-size: 15px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		margin: 0;
	}
	.approach-stat {
		font-size: 12px;
		font-weight: 500;
		color: var(--color-bill);
		margin: 16px 0 0;
		opacity: 0.85;
	}

	/* ── DUAL LENS ───────────────────────────────────────────── */
	.lens-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 14px;
		margin-top: 48px;
	}
	@media (min-width: 720px) {
		.lens-grid { grid-template-columns: 1fr 1fr; }
	}

	.lens-card {
		border: 1px solid var(--color-border-subtle);
		border-radius: 14px;
		padding: 32px;
		border-top-width: 2px;
		position: relative;
	}
	.lens-card--institutional {
		background: var(--color-slate);
		border-top-color: var(--color-executive);
	}
	.lens-card--impact {
		background: rgba(74, 124, 255, 0.05);
		border-top-color: var(--color-bill);
	}

	.lens-label {
		font-size: 11px;
		font-weight: 500;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		margin: 0 0 18px;
	}
	.lens-card--institutional .lens-label { color: var(--color-executive); }
	.lens-card--impact .lens-label { color: var(--color-bill); }

	.lens-quote {
		font-family: var(--font-editorial);
		font-size: 1.15rem;
		font-weight: 700;
		line-height: 1.45;
		color: #fff;
		margin: 0 0 16px;
		padding: 0;
		border: none;
	}
	.lens-body {
		font-size: 15px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		margin: 0 0 20px;
	}
	.lens-source {
		font-size: 12px;
		font-weight: 500;
		color: rgba(255, 255, 255, 0.25);
		margin: 0;
	}

	/* ── BRADBURY ─────────────────────────────────────────────── */
	.section--bradbury {
		text-align: center;
		padding-top: 100px;
		padding-bottom: 100px;
	}
	@media (min-width: 960px) {
		.section--bradbury {
			padding-top: 128px;
			padding-bottom: 128px;
		}
	}

	.bradbury-headline {
		font-family: var(--font-display);
		font-size: clamp(2rem, 4vw, 3.5rem);
		font-weight: 700;
		line-height: 1.2;
		letter-spacing: -0.02em;
		color: #fff;
		margin: 0 auto 28px;
		max-width: 18ch;
	}
	.bradbury-headline em {
		font-style: italic;
	}
	.bradbury-body {
		font-size: 18px;
		line-height: 1.7;
		color: var(--color-text-secondary);
		max-width: 48ch;
		margin: 0 auto 40px;
	}

	/* ── WAITLIST ─────────────────────────────────────────────── */
	.section--waitlist {
		text-align: center;
		padding-top: 100px;
		padding-bottom: 140px;
	}

	.waitlist-headline {
		font-family: var(--font-display);
		font-size: clamp(2rem, 4vw, 3.2rem);
		font-weight: 700;
		line-height: 1.2;
		letter-spacing: -0.02em;
		color: #fff;
		margin: 0 0 16px;
	}
	.waitlist-sub {
		font-size: 18px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		margin: 0 auto 40px;
		max-width: 44ch;
	}
	.waitlist-form {
		display: flex;
		flex-direction: column;
		gap: 10px;
		max-width: 480px;
		margin: 0 auto;
	}
	@media (min-width: 540px) {
		.waitlist-form { flex-direction: row; }
	}

	.waitlist-input {
		flex: 1;
		height: 52px;
		background: var(--color-slate);
		border: 1px solid rgba(255, 255, 255, 0.1);
		border-radius: 12px;
		padding: 0 18px;
		font-family: var(--font-body);
		font-size: 16px;
		color: #fff;
		transition: border-color 150ms;
	}
	.waitlist-input::placeholder { color: rgba(255, 255, 255, 0.3); }
	.waitlist-input:focus {
		outline: none;
		border-color: var(--color-border-focus);
	}
	.waitlist-input:disabled { opacity: 0.5; }

	.waitlist-btn { flex-shrink: 0; }

	.form-error {
		margin-top: 12px;
		font-size: 14px;
		color: var(--color-error);
	}

	/* Success */
	.success-block {
		animation: fadeUp 0.4s cubic-bezier(0.25, 0.1, 0.25, 1) both;
	}
	.success-icon {
		width: 52px;
		height: 52px;
		border-radius: 9999px;
		border: 1px solid var(--color-success);
		color: var(--color-success);
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0 auto 24px;
	}
	.success-heading {
		font-family: var(--font-display);
		font-size: clamp(1.8rem, 3vw, 2.8rem);
		font-weight: 700;
		letter-spacing: -0.02em;
		margin: 0 0 12px;
		color: #fff;
	}
	.success-sub {
		font-size: 18px;
		line-height: 1.6;
		color: var(--color-text-secondary);
		margin: 0;
	}

	/* ── BUTTONS ─────────────────────────────────────────────── */
	.btn-primary {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		height: 52px;
		padding: 0 28px;
		background: #fff;
		color: #000;
		font-family: var(--font-body);
		font-size: 16px;
		font-weight: 500;
		border-radius: 9999px;
		text-decoration: none;
		border: none;
		cursor: pointer;
		transition: opacity 150ms, transform 150ms;
		white-space: nowrap;
	}
	.btn-primary:active {
		transform: scale(0.98);
		opacity: 0.9;
	}
	.btn-primary:disabled {
		opacity: 0.5;
		cursor: not-allowed;
	}

	.btn-secondary {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		height: 52px;
		padding: 0 4px;
		color: rgba(255, 255, 255, 0.6);
		font-family: var(--font-body);
		font-size: 16px;
		font-weight: 500;
		text-decoration: none;
		transition: color 150ms;
	}
	.btn-secondary:hover { color: #fff; }

	/* ── BADGES ──────────────────────────────────────────────── */
	.badge {
		display: inline-flex;
		align-items: center;
		height: 24px;
		padding: 0 10px;
		border-radius: 6px;
		font-size: 11px;
		font-weight: 500;
		letter-spacing: 0.06em;
		text-transform: uppercase;
		color: #fff;
	}
	.badge--bill  { background: var(--color-bill); }
	.badge--case  { background: var(--color-case); }
	.badge--order { background: var(--color-executive); }

	/* ── FOOTER ──────────────────────────────────────────────── */
	.footer {
		display: flex;
		align-items: center;
		justify-content: space-between;
		max-width: 1120px;
		margin: 0 auto;
		padding: 32px 24px;
		border-top: 1px solid var(--color-border-subtle);
	}
	.footer-wordmark {
		font-family: var(--font-display);
		font-size: 18px;
		font-weight: 700;
		color: rgba(255, 255, 255, 0.4);
	}
	.footer-copy {
		font-size: 13px;
		color: rgba(255, 255, 255, 0.25);
		margin: 0;
	}

	/* ── UTILITY ─────────────────────────────────────────────── */
	.sr-only {
		position: absolute;
		width: 1px;
		height: 1px;
		padding: 0;
		margin: -1px;
		overflow: hidden;
		clip: rect(0, 0, 0, 0);
		white-space: nowrap;
		border-width: 0;
	}
</style>
