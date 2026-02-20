<section class="mx-auto grid w-full max-w-7xl grid-cols-1 items-end gap-8 py-8 lg:grid-cols-[1fr_auto]" id="waitlist">
	<div>
		<p class="mb-2 text-[13px] font-medium uppercase tracking-[0.08em] text-[var(--color-text-secondary)]">
			Launch
		</p>
		<h2 class="m-0 [font-family:var(--font-display)] text-[1.7rem] leading-[1.2] font-bold lg:text-[2.4rem]">
			Be first when Billion opens.
		</h2>
		<p class="mt-2 text-[18px] leading-[1.5] text-[var(--color-text-secondary)]">
			Join the waitlist for early access, product updates, and pilot program invites.
		</p>
	</div>
	<form
		class="grid grid-cols-1 gap-2 sm:grid-cols-[minmax(260px,320px)_auto]"
		action="#"
		method="post"
		onsubmit={(event) => event.preventDefault()}
	>
		<label for="email" class="sr-only">Email address</label>
		<input
			id="email"
			type="email"
			name="email"
			placeholder="you@domain.com"
			required
			class="h-[50px] rounded-[12px] border border-white/10 bg-[var(--color-slate)] px-4 text-[16px] text-white placeholder:text-[var(--color-text-secondary)]"
		/>
		<button
			type="submit"
			class="inline-flex h-[50px] items-center justify-center rounded-[9999px] bg-white px-6 text-[16px] font-medium text-black transition duration-150 ease-[cubic-bezier(0.25,0.1,0.25,1)] active:scale-[0.98] active:opacity-90"
		>
			Join Waitlist
		</button>
	</form>
</section>
