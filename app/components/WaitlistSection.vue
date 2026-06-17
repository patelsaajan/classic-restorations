<script setup lang="ts">
const perks = ['First booking access', 'Founder pricing']

const state = reactive({
  name: '',
  email: '',
  car: '',
})

const inputUi = {
  base: 'border-[1.5px] border-ink bg-white px-3.5 py-3 font-body text-[15px] text-ink focus:border-red focus:outline-none rounded-none transition-none',
}

const fieldUi = {
  label: 'mb-1.5 font-ui text-[10px] font-medium tracking-[0.2em] text-mud',
  container: '',
}

function onSubmit() {
  // placeholder — hook up to a real waitlist backend
}
</script>

<template>
  <section id="waitlist" class="relative mt-20 bg-red px-8 pt-20 pb-22 text-cream">
    <div
      class="absolute inset-x-0 -top-px h-3.5 bg-linear-to-b from-ink/12 to-transparent"
    />

    <div
      class="mx-auto grid max-w-275 items-center gap-16 md:grid-cols-[1fr_1.1fr]"
    >
      <!-- Pitch -->
      <div>
        <div
          class="inline-flex items-center gap-2.5 border-[1.5px] border-cream px-3 py-1 font-ui text-[11px] font-semibold tracking-[0.25em]"
        >
          <span class="h-2 w-2 rounded-full bg-cream motion-safe:animate-[drift_3s_ease-in-out_infinite]" />
          PRE-LAUNCH WAITLIST
        </div>

        <h2
          class="mt-4.5 mb-3.5 font-display text-[clamp(48px,7vw,88px)] leading-[0.9] uppercase"
        >
          Be first<br />in line.
        </h2>

        <p class="mb-4.5 max-w-115 font-body text-lg leading-normal text-red-soft">
          We're not open yet. When we do open, we're taking on
          <strong class="bg-black/18 px-1">one car at a time</strong> — and our first slots will go
          to people on this list. No newsletter, no spam. A short note when we're ready for you, and
          the chance to book a consultation before anyone else.
        </p>

        <ul
          class="flex list-none gap-7 p-0 font-ui text-xs font-medium tracking-[0.15em] text-red-soft uppercase"
        >
          <li v-for="perk in perks" :key="perk" class="flex items-center gap-2">
            <span class="h-[1.5px] w-4.5 bg-cream" />
            {{ perk }}
          </li>
        </ul>
      </div>

      <!-- Form card -->
      <div
        class="relative bg-cream px-10 pt-9 pb-10 text-ink shadow-[0_24px_48px_-16px_rgba(0,0,0,0.35)]"
      >

        <div class="font-ui text-[11px] font-semibold tracking-[0.25em] text-red">
          REGISTER YOUR INTEREST
        </div>
        <div class="mt-1.5 mb-5.5 font-display text-[32px] leading-none uppercase">
          Reserve a spot
        </div>

        <UForm :state="state" class="flex flex-col gap-3.5" @submit="onSubmit">
          <UFormField name="name" label="NAME" :ui="fieldUi">
            <UInput
              v-model="state.name"
              type="text"
              placeholder="Sam Phillips"
              required
              variant="none"
              fixed
              class="w-full"
              :ui="inputUi"
            />
          </UFormField>

          <UFormField name="email" label="EMAIL" :ui="fieldUi">
            <UInput
              v-model="state.email"
              type="email"
              placeholder="sam@example.co.uk"
              required
              variant="none"
              fixed
              class="w-full"
              :ui="inputUi"
            />
          </UFormField>

          <UFormField name="car" :ui="fieldUi">
            <template #label>
              THE CAR YOU'D BRING US <span class="text-red">(OPTIONAL)</span>
            </template>
            <UTextarea
              v-model="state.car"
              :rows="3"
              placeholder="e.g. '63 Jaguar Mk2 — needs a full body strip"
              variant="none"
              fixed
              class="w-full"
              :ui="inputUi"
            />
          </UFormField>

          <button
            type="submit"
            class="mt-2 flex cursor-pointer items-center justify-center gap-2.5 border-[1.5px] border-ink bg-red px-4.5 py-4 font-ui text-sm font-bold tracking-[0.25em] text-white uppercase transition-colors duration-200 hover:bg-ink hover:text-cream"
          >
            <span>Hold my spot</span>
            <span class="font-display">→</span>
          </button>

          <p class="text-center font-body text-[12.5px] text-mud italic">
            No marketing, no resale. Just one note when the doors open.
          </p>
        </UForm>
      </div>
    </div>
  </section>
</template>
