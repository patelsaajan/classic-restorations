<script setup lang="ts">
const socials = [
  { href: '#', name: 'Instagram', note: '— @classicrestorations' },
  { href: '#', name: 'YouTube', note: '— the workshop films' },
  { href: '#', name: 'TikTok', note: '— short cuts, big finds' },
  { href: '#', name: 'Facebook', note: '— for the long-time mates' },
]
</script>

<template>
  <footer class="border-t-4 border-red bg-ink-black px-8 pt-12 pb-7 text-tan">
    <div class="mx-auto max-w-[1320px]">
      <div
        class="grid gap-12 border-b border-cream/12 pb-8 md:grid-cols-[1.4fr_1fr_1fr]"
      >
        <!-- Brand -->
        <div>
          <div class="font-display text-[36px] leading-none text-cream uppercase">
            Classic <span class="text-red">Restorations</span>
          </div>
          <p class="mt-2.5 max-w-[360px] font-body text-[14.5px] leading-[1.5] text-tan italic">
            A London workshop bringing classic cars back to the road — one at a time, the way they
            should be done.
          </p>
        </div>

        <!-- Socials -->
        <div>
          <div class="mb-3.5 font-ui text-[11px] font-semibold tracking-[0.25em] text-red">
            FOLLOW THE BUILD
          </div>
          <div class="flex flex-col gap-2.5 font-body text-[14.5px]">
            <a
              v-for="social in socials"
              :key="social.name"
              :href="social.href"
              class="flex items-center gap-2.5 text-cream no-underline"
            >
              <span class="inline-block h-2 w-2 bg-red" />
              {{ social.name }}
              <span class="text-[12.5px] text-mud italic">{{ social.note }}</span>
            </a>
          </div>
        </div>

        <!-- Contact -->
        <div>
          <div class="mb-3.5 font-ui text-[11px] font-semibold tracking-[0.25em] text-red">
            GET IN TOUCH
          </div>
          <address class="font-body text-[14.5px] leading-[1.7] text-cream not-italic">
            hello@classicrestorations.co.uk<br />
            <span class="text-tan">London, UK</span><br />
            <span class="text-tan italic">By appointment only</span>
          </address>
        </div>
      </div>

      <div
        class="flex items-center justify-between pt-5.5 font-ui text-[11px] font-medium tracking-[0.2em] text-mud uppercase"
      >
        <div>© 2026 Classic Restorations Ltd · All rights reserved</div>
        <div>Built in London · One car at a time</div>
      </div>
    </div>
  </footer>
</template>
