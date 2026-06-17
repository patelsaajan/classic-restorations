<script setup lang="ts">
// Hero: centered magazine title + an oversized "polaroid" framed photo
// carrying four numbered hotspots. Tapping a hotspot pins its card open;
// hovering also reveals it. Hotspot 2 opens by default so the
// interaction reads at a glance.
interface Hotspot {
  id: number
  kicker: string
  title: string
  body: string
  /** position of the dot on the photo */
  dot: string
  /** position + side styling of the annotation card */
  card: string
  /** card text alignment */
  align: string
  /** staggered pulse-ring delay (literal class so Tailwind can see it) */
  delay: string
}

const hotspots: Hotspot[] = [
  {
    id: 1,
    kicker: '01 · HEADLAMP',
    title: 'Found in Kent',
    body: 'Original glass. Took four months and a long drive on a Sunday. Worth every mile.',
    dot: 'left-[16%] top-[32%]',
    card: 'top-0 left-13 w-72 border-l-3 border-red',
    align: 'text-left',
    delay: 'motion-safe:[animation-delay:0s]',
  },
  {
    id: 2,
    kicker: '02 · BODY',
    title: 'Stripped to bare metal',
    body: 'Three months of welding before primer. You can still see where the hammer kissed it — if you know where to look.',
    dot: 'left-[48%] top-[52%]',
    card: 'bottom-13 -left-45 w-72 border-l-3 border-red',
    align: 'text-left',
    delay: 'motion-safe:[animation-delay:0.3s]',
  },
  {
    id: 3,
    kicker: '03 · PAINT',
    title: 'Mixed three times',
    body: 'Sam is particular. The colour had to match a photograph from 1963. It does now.',
    dot: 'left-[76%] top-[38%]',
    card: 'top-0 right-13 w-72 border-r-3 border-red',
    align: 'text-right',
    delay: 'motion-safe:[animation-delay:0.6s]',
  },
  {
    id: 4,
    kicker: '04 · WHEELS',
    title: 'All 60 spokes',
    body: 'Rebuilt one at a time. The original spokes are still on her — we just put them back where they belonged.',
    dot: 'left-[35%] top-[78%]',
    card: 'bottom-13 left-13 w-72 border-l-3 border-red',
    align: 'text-left',
    delay: 'motion-safe:[animation-delay:0.9s]',
  },
]

const activeId = ref(2)

function toggle(id: number) {
  activeId.value = activeId.value === id ? 0 : id
}
</script>

<template>
  <section id="work" class="bg-cream px-8 pt-14 pb-6">
    <div class="mx-auto max-w-330">
      <!-- Title block -->
      <div class="mx-auto mb-9 max-w-275 text-center">
        <div class="mb-4.5 inline-flex items-center gap-3">
          <span class="h-[1.5px] w-9 bg-red" />
          <span class="font-ui text-[11px] font-semibold tracking-[0.35em] text-red">
            THE WORKSHOP · NO. 01
          </span>
          <span class="h-[1.5px] w-9 bg-red" />
        </div>

        <h1
          class="m-0 font-display text-[clamp(72px,11vw,168px)] leading-[0.88] tracking-[-0.005em] uppercase"
        >
          Classic<br />
          <span class="relative inline-block">
            <span class="inline-block bg-red px-4.5 pb-1.5 text-cream">Restorations</span>
          </span>
        </h1>

        <p
          class="mx-auto mt-5.5 max-w-155 font-body text-[22px] text-coffee italic text-pretty"
        >
          One car, one workshop, one set of hands. We're bringing classics back to the road — and
          we'd like you with us from the start.
        </p>
        <p class="mt-4 font-type text-xs tracking-[0.2em] text-mud">↓ TAP THE PHOTO ↓</p>
      </div>

      <!-- Polaroid frame -->
      <div
        class="relative mx-auto max-w-310 border border-ink/8 bg-white px-7 pt-7 pb-16 shadow-[0_30px_60px_-20px_rgba(26,19,17,0.35),0_8px_16px_-8px_rgba(26,19,17,0.2)]"
      >
        <!-- tape -->
        <div
          class="absolute -top-3.5 left-20 h-7 w-27.5 -rotate-3 border border-red/25 bg-red/18"
        />
        <div
          class="absolute -top-3.5 right-20 h-7 w-27.5 rotate-2 border border-red/25 bg-red/18"
        />

        <!-- Image area -->
        <div class="stripes relative aspect-16/9.5 overflow-hidden bg-[#d4cfc4]">
          <!-- centre placeholder label -->
          <div class="absolute inset-0 flex flex-col items-center justify-center gap-1.5">
            <div
              class="border-[1.5px] border-ink bg-cream/90 px-5.5 py-3.5 font-type text-xs tracking-[0.25em] text-ink"
            >
              [ HERO CAR PHOTO ]
            </div>
            <div class="bg-cream/90 px-3 py-1 font-body text-[13px] text-coffee italic">
              full restoration, three-quarter view
            </div>
          </div>

          <!-- Hotspots -->
          <button
            v-for="spot in hotspots"
            :key="spot.id"
            type="button"
            class="group absolute cursor-pointer border-0 bg-transparent p-0"
            :class="spot.dot"
            :aria-expanded="activeId === spot.id"
            :aria-label="`${spot.title} — restoration note`"
            @click="toggle(spot.id)"
          >
            <span class="relative block h-9 w-9">
              <span
                class="absolute inset-0 rounded-full border-2 border-red motion-safe:animate-[pulse-ring_2.2s_ease-out_infinite]"
                :class="spot.delay"
              />
              <span
                class="relative flex h-9 w-9 items-center justify-center rounded-full border-2 border-cream font-ui text-[15px] font-bold shadow-[0_4px_12px_rgba(0,0,0,0.4)] transition-[transform,background] duration-200 group-hover:scale-[1.15] group-hover:bg-red group-hover:text-white"
                :class="
                  activeId === spot.id
                    ? 'scale-[1.15] bg-red text-white'
                    : 'bg-ink text-cream'
                "
              >
                {{ spot.id }}
              </span>
            </span>

            <span
              class="absolute z-10 bg-white px-4 pt-3.5 pb-4 shadow-[0_12px_28px_rgba(26,19,17,0.35)] transition-[opacity,transform] duration-200 group-hover:translate-y-0 group-hover:scale-100 group-hover:opacity-100"
              :class="[
                spot.card,
                spot.align,
                activeId === spot.id
                  ? 'translate-y-0 scale-100 opacity-100'
                  : 'pointer-events-none translate-y-2 scale-[0.96] opacity-0',
              ]"
            >
              <span class="block font-ui text-[11px] font-semibold tracking-[0.2em] text-red">
                {{ spot.kicker }}
              </span>
              <span class="my-1.5 block font-display text-[22px] leading-none uppercase">
                {{ spot.title }}
              </span>
              <span class="block font-body text-[13.5px] leading-normal text-ink-soft">
                {{ spot.body }}
              </span>
            </span>
          </button>
        </div>

        <!-- caption -->
        <p class="mt-5.5 text-center font-hand text-[26px] font-medium text-ink">
          "she runs better now than she did in '63"
          <span class="mt-1 block font-ui text-[11px] font-medium tracking-[0.3em] text-mud">
            — SAM, ON THE FIRST FINISHED PIECE
          </span>
        </p>
      </div>
    </div>
  </section>
</template>
