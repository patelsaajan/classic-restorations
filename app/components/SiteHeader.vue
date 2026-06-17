<script setup lang="ts">
// Magazine masthead nav. Links use an animated underline that wipes in
// from the left on hover (the ::after trick from the original comp).
const links = [
  { href: '#work', label: 'The Garage', accent: false },
  { href: '#sam', label: 'Meet Sam', accent: false },
  { href: '#waitlist', label: 'Join the List', accent: true },
]
</script>

<template>
  <header class="bg-ink text-cream">
    <div
      class="mx-auto flex max-w-330 items-center justify-between border-b border-cream/15 px-8 py-3.5"
    >
      <div class="flex items-baseline gap-3.5">
        <div class="bg-red px-2 py-1 font-ui text-[11px] font-bold tracking-[0.12em] text-white">
          EST. 2026
        </div>
        <div class="font-type text-[11px] tracking-[0.25em] text-tan">LONDON · UK</div>
      </div>

      <nav class="flex gap-8 font-ui text-[13px] font-medium uppercase tracking-[0.18em]">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="relative no-underline after:absolute after:left-0 after:right-full after:-bottom-1 after:h-[1.5px] after:bg-red after:transition-[right] after:duration-200 after:content-[''] hover:after:right-0"
          :class="link.accent ? 'text-red' : 'text-cream'"
        >
          {{ link.label }}
        </a>
      </nav>
    </div>
  </header>
</template>
