<script setup lang="ts">
// About Sam — the man behind the workshop. Magazine "chapter" framing.
const stats = [
  { value: '30', unit: 'yrs', label: 'Driving London' },
  { value: '1M', unit: '+mi', label: 'On one cab' },
  { value: '1', unit: '/1', label: 'Car at a time' },
]
</script>

<template>
  <section id="sam" class="bg-cream px-8 pt-24 pb-20">
    <div class="mx-auto max-w-295">
      <div class="mb-8 flex items-center justify-between gap-6">
        <div class="flex items-center gap-3.5">
          <span class="h-[1.5px] w-10 bg-red" />
          <span class="font-ui text-[11px] font-semibold tracking-[0.35em] text-red">
            CHAPTER ONE · THE MAN BEHIND IT
          </span>
        </div>
        <span class="font-type text-[11px] tracking-[0.2em] text-mud">PG. 03</span>
      </div>

      <div class="grid items-start gap-16 md:grid-cols-[1fr_1.3fr]">

        <!-- Portrait + footnote -->
        <div>
          <figure
            class="relative m-0 bg-white px-5 pt-5 pb-8 shadow-[0_24px_40px_-20px_rgba(26,19,17,0.35)]"
          >
            <div
              class="absolute -top-3 left-1/2 h-5.5 w-30 -translate-x-1/2 -rotate-2 border border-red/25 bg-red/18"
            />
            <div class="stripes-dark relative aspect-4/5 bg-ink-soft">
              <div class="absolute inset-0 flex flex-col items-center justify-center gap-2">
                <div
                  class="border-[1.5px] border-ink bg-cream/95 px-4 py-2.5 font-type text-[11px] tracking-[0.25em] text-ink"
                >
                  [ PORTRAIT OF SAM ]
                </div>
                <div class="bg-cream/95 px-3 py-1 font-body text-xs text-coffee italic">
                  in the workshop, hands on a bonnet
                </div>
              </div>
            </div>
            <figcaption class="mt-3.5 text-center font-hand text-2xl font-medium text-ink">
              Sam, somewhere south of the river
            </figcaption>
          </figure>

          <aside class="mt-7 border-l-4 border-red bg-ink px-6 py-5.5 text-cream">
            <div class="font-ui text-[11px] font-semibold tracking-[0.3em] text-red">FOOTNOTE</div>
            <p class="mt-2 font-body text-[15.5px] leading-normal italic">
              The million-mile cab is currently on display. We've been told it's the only one of its
              kind still in one piece. We'd like to keep it that way.
            </p>
          </aside>
        </div>

                <!-- Copy -->
        <div>
          <h2 class="m-0 mb-2 font-display text-[clamp(56px,8vw,104px)] leading-[0.9] uppercase">
            Meet<br />
            <span class="inline-block bg-ink px-3.5 pt-0.5 pb-2 text-cream">Sam.</span>
          </h2>

          <p
            class="my-6 max-w-140 font-body text-[22px] leading-[1.35] text-ink-soft italic text-pretty"
          >
            He's driven more London streets than most maps remember.
          </p>

          <div class="max-w-140 space-y-4 font-body text-[16.5px] leading-[1.7] text-ink-soft text-pretty">
            <p class="m-0">
              Sam spent <strong>30 years</strong> behind the wheel of a London black cab. He knows
              the city inside out — every shortcut, every backstreet, every greasy spoon that's been
              there since before the congestion charge.
            </p>
            <p class="m-0">
              One of his old cabs is on display in a museum with <strong>over a million miles</strong>
              on the clock. Same engine. Same gearbox. He's not the kind of man who gives up on a car
              when it's still got road in it.
            </p>
            <p class="m-0">
              Between restorations he also helps run a car wash — which means he knows paint, chrome,
              leather and dirt the way most people know their own front door. The outside gets the
              same care as the inside. The inside gets the same care as the engine.
            </p>
          </div>

          <!-- Stats -->
          <dl class="mt-10 grid max-w-140 grid-cols-3 gap-6 border-t-2 border-ink pt-5">
            <div v-for="stat in stats" :key="stat.label">
              <dd class="m-0 font-display text-[56px] leading-none text-red">
                {{ stat.value }}<span class="text-[22px] text-ink">{{ stat.unit }}</span>
              </dd>
              <dt class="mt-1.5 font-ui text-[11px] font-medium tracking-[0.2em] text-mud uppercase">
                {{ stat.label }}
              </dt>
            </div>
          </dl>
        </div>
      </div>
    </div>
  </section>
</template>
