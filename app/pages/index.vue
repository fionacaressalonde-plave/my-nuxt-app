<script setup lang="ts">
const email = ref('')
const password = ref('')
const remember = ref(true)

function onLogin() {
  // TODO: connect this to your real login (API / auth) later
  console.log('Login attempt:', email.value, remember.value)
}

// Wheat stalks in the illustration (x = distance from the panel edge, h = height in px)
const wheatLeft = [
  { x: 53, h: 92 }, { x: 77, h: 102 }, { x: 101, h: 110 }, { x: 125, h: 92 },
  { x: 150, h: 102 }, { x: 174, h: 110 }, { x: 198, h: 92 },
]
const wheatRight = [
  { x: 124, h: 82 }, { x: 100, h: 92 }, { x: 75, h: 82 },
  { x: 51, h: 92 }, { x: 27, h: 82 }, { x: 3, h: 92 },
]
</script>

<template>
  <main class="flex min-h-screen bg-cream font-sans text-forest-900">
    <!-- Reusable wheat drawing (used below with <use>) -->
    <svg class="pointer-events-none absolute h-0 w-0" aria-hidden="true">
      <defs>
        <symbol id="wheat" viewBox="0 0 24 130">
          <line x1="12" y1="38" x2="12" y2="130" stroke="#e0a63a" stroke-width="2.4" stroke-linecap="round" />
          <g fill="#e8b23c">
            <path d="M12 30 C8 22 8 11 12 2 C16 11 16 22 12 30Z" />
            <g v-for="n in 4" :key="n" :transform="`translate(0 ${(n - 1) * 13})`">
              <path d="M11 41 C3 39 1 31 2 23 C9 25 12 32 11 41Z" />
              <path d="M13 41 C21 39 23 31 22 23 C15 25 12 32 13 41Z" />
            </g>
          </g>
        </symbol>
      </defs>
    </svg>

    <!-- LEFT: branding panel -->
    <section
      class="relative hidden overflow-hidden bg-linear-to-br from-forest-900 to-forest-600 px-[54px] pt-[46px] text-white lg:block lg:w-[53%]"
    >
      <!-- Logo -->
      <div class="flex items-center gap-3">
        <div class="flex h-[38px] w-[38px] items-center justify-center rounded-xl bg-leaf-400 text-forest-900">
          <svg class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M7 20h10" /><path d="M10 20c5.5-2.5.8-6.4 3-10" />
            <path d="M9.5 9.4c1.1.8 1.8 2.2 2.3 3.7-2 .4-3.5.4-4.8-.3-1.2-.6-2.3-1.9-3-4.2 2.8-.5 4.4 0 5.5.8z" />
            <path d="M14.1 6a7 7 0 0 0-1.1 4c1.9-.1 3.3-.6 4.3-1.4 1-1 1.6-2.2 1.7-3.6-1.8-.1-3.2.2-4.2 1z" />
          </svg>
        </div>
        <div>
          <div class="font-display text-lg leading-tight font-semibold">Farm Assist</div>
          <div class="text-[11px] text-leaf-300">Community Farm Assistance &amp; Subsidy Monitoring</div>
        </div>
      </div>

      <!-- Season pill -->
      <div class="mt-[78px] inline-flex items-center gap-2 rounded-full bg-forest-600 px-3.5 py-1.5 text-[10.5px] font-semibold tracking-wider text-leaf-300 uppercase">
        <svg class="h-3 w-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M7 20h10" /><path d="M10 20c5.5-2.5.8-6.4 3-10" />
          <path d="M9.5 9.4c1.1.8 1.8 2.2 2.3 3.7-2 .4-3.5.4-4.8-.3-1.2-.6-2.3-1.9-3-4.2 2.8-.5 4.4 0 5.5.8z" />
          <path d="M14.1 6a7 7 0 0 0-1.1 4c1.9-.1 3.3-.6 4.3-1.4 1-1 1.6-2.2 1.7-3.6-1.8-.1-3.2.2-4.2 1z" />
        </svg>
        Wet season 2026 · Municipal programs
      </div>

      <!-- Headline -->
      <h1 class="mt-5 max-w-[34rem] font-display text-[2.75rem] leading-[1.12] font-bold">
        Growing communities, one request at a time.
      </h1>
      <p class="mt-5 max-w-[26rem] text-[15px] leading-relaxed text-white/85">
        Request seeds, fertilizer, and equipment. Track every request from submission to release.
      </p>

      <!-- Feature list -->
      <ul class="mt-6 space-y-3 text-[15px]">
        <li class="flex items-center gap-3">
          <span class="flex h-[30px] w-[30px] items-center justify-center rounded-full bg-leaf-400 text-forest-900">
            <svg class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="8" y="2" width="8" height="4" rx="1" /><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2" />
              <path d="M12 11h4" /><path d="M12 16h4" /><path d="M8 11h.01" /><path d="M8 16h.01" />
            </svg>
          </span>
          Submit and track requests online
        </li>
        <li class="flex items-center gap-3">
          <span class="flex h-[30px] w-[30px] items-center justify-center rounded-full bg-leaf-400 text-forest-900">
            <svg class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M21 8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16Z" />
              <path d="m3.3 7 8.7 5 8.7-5" /><path d="M12 22V12" />
            </svg>
          </span>
          See real-time supply availability
        </li>
        <li class="flex items-center gap-3">
          <span class="flex h-[30px] w-[30px] items-center justify-center rounded-full bg-leaf-400 text-forest-900">
            <svg class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M14 18V6a2 2 0 0 0-2-2H4a2 2 0 0 0-2 2v11a1 1 0 0 0 1 1h2" /><path d="M15 18H9" />
              <path d="M19 18h2a1 1 0 0 0 1-1v-3.65a1 1 0 0 0-.22-.624l-3.48-4.35A1 1 0 0 0 17.52 8H14" />
              <circle cx="17" cy="18" r="2" /><circle cx="7" cy="18" r="2" />
            </svg>
          </span>
          Transparent distribution records
        </li>
      </ul>

      <!-- Scenery: sun, hills, wheat -->
      <div class="pointer-events-none absolute inset-x-0 bottom-0 h-[260px]" aria-hidden="true">
        <!-- Sun -->
        <div class="absolute right-[70px] bottom-[138px] flex h-[105px] w-[105px] items-center justify-center rounded-full bg-sun/25">
          <div class="h-[64px] w-[64px] rounded-full bg-sun"></div>
        </div>

        <!-- Hills -->
        <svg class="absolute inset-x-0 bottom-0 h-[160px] w-full" viewBox="0 0 600 160" preserveAspectRatio="none">
          <path d="M0 18 C120 -6 250 4 350 30 S520 40 600 -4 L600 160 L0 160Z" fill="#235c3d" />
          <path d="M0 62 C100 36 230 34 330 58 S510 76 600 52 L600 160 L0 160Z" fill="#2e8038" />
          <path d="M0 124 C110 96 260 88 380 104 S540 120 600 110 L600 160 L0 160Z" fill="#a8d44a" />
        </svg>

        <!-- Wheat -->
        <svg
          v-for="(w, i) in wheatLeft"
          :key="'l' + i"
          class="absolute bottom-0"
          :style="{ left: w.x + 'px', height: w.h + 'px', width: (w.h * 24) / 130 + 'px' }"
          viewBox="0 0 24 130"
          preserveAspectRatio="xMidYMax meet"
        >
          <use href="#wheat" />
        </svg>
        <svg
          v-for="(w, i) in wheatRight"
          :key="'r' + i"
          class="absolute bottom-0"
          :style="{ right: w.x + 'px', height: w.h + 'px', width: (w.h * 24) / 130 + 'px' }"
          viewBox="0 0 24 130"
          preserveAspectRatio="xMidYMax meet"
        >
          <use href="#wheat" />
        </svg>
      </div>
    </section>

    <!-- RIGHT: login card -->
    <section class="flex w-full items-center justify-center px-6 py-10 lg:w-[47%]">
      <div class="w-full max-w-[28rem] rounded-3xl border border-black/5 bg-white p-8 shadow-[0_12px_40px_rgba(14,51,32,0.10)]">
        <div class="flex h-[38px] w-[38px] items-center justify-center rounded-xl bg-[#e1f0dc] text-forest-500">
          <svg class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M7 20h10" /><path d="M10 20c5.5-2.5.8-6.4 3-10" />
            <path d="M9.5 9.4c1.1.8 1.8 2.2 2.3 3.7-2 .4-3.5.4-4.8-.3-1.2-.6-2.3-1.9-3-4.2 2.8-.5 4.4 0 5.5.8z" />
            <path d="M14.1 6a7 7 0 0 0-1.1 4c1.9-.1 3.3-.6 4.3-1.4 1-1 1.6-2.2 1.7-3.6-1.8-.1-3.2.2-4.2 1z" />
          </svg>
        </div>

        <h2 class="mt-5 font-display text-[1.75rem] leading-tight font-bold">Welcome back</h2>
        <p class="mt-1 text-[13px] text-slate-500">Use the account created for you by the staff.</p>

        <form class="mt-6 space-y-4" @submit.prevent="onLogin">
          <div>
            <label for="email" class="text-[13px] font-medium">Email</label>
            <div class="relative mt-2">
              <svg class="absolute top-1/2 left-3.5 h-4 w-4 -translate-y-1/2 text-slate-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="2" y="4" width="20" height="16" rx="2" /><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
              </svg>
              <input
                id="email"
                v-model="email"
                type="email"
                placeholder="name@example.com"
                class="w-full rounded-xl border border-slate-200 bg-white py-3 pr-4 pl-10 text-sm outline-none placeholder:text-slate-400 focus:border-forest-500 focus:ring-2 focus:ring-forest-500/20"
              />
            </div>
          </div>

          <div>
            <label for="password" class="text-[13px] font-medium">Password</label>
            <div class="relative mt-2">
              <svg class="absolute top-1/2 left-3.5 h-4 w-4 -translate-y-1/2 text-slate-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="3" y="11" width="18" height="11" rx="2" /><path d="M7 11V7a5 5 0 0 1 10 0v4" />
              </svg>
              <input
                id="password"
                v-model="password"
                type="password"
                placeholder="Enter your password"
                class="w-full rounded-xl border border-slate-200 bg-white py-3 pr-4 pl-10 text-sm outline-none placeholder:text-slate-400 focus:border-forest-500 focus:ring-2 focus:ring-forest-500/20"
              />
            </div>
          </div>

          <div class="flex items-center justify-between text-[13px]">
            <label class="flex cursor-pointer items-center gap-2">
              <input v-model="remember" type="checkbox" class="h-4 w-4 rounded accent-forest-500" />
              Keep me logged in
            </label>
            <a href="#" class="font-semibold text-forest-500 hover:underline">Need help?</a>
          </div>

          <button
            type="submit"
            class="w-full rounded-xl bg-forest-500 py-3 text-sm font-semibold text-white transition hover:bg-forest-600"
          >
            Log in
          </button>
        </form>

        <div class="mt-4 flex items-start gap-2 rounded-xl bg-cream px-3.5 py-3 text-xs text-stone-600">
          <svg class="mt-0.5 h-3.5 w-3.5 shrink-0 text-amber-800" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <circle cx="12" cy="12" r="10" /><path d="M12 16v-4" /><path d="M12 8h.01" />
          </svg>
          <span>No sign-up. Accounts are created by municipal agriculture staff.</span>
        </div>
      </div>
    </section>
  </main>
</template>