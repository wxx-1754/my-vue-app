<script setup lang="ts">
import {
  ArrowUpRight,
  Bell,
  BookOpenCheck,
  CalendarCheck,
  ChevronDown,
  ChevronRight,
  Crown,
  Heart,
  Home,
  Layers3,
  ListChecks,
  MoreHorizontal,
  PlusCircle,
  Settings,
  TrendingUp,
  Video,
} from 'lucide-vue-next'

const menuItems = [
  { label: '工作台', icon: Home, active: true },
  { label: '模拟面试', icon: Video, active: false },
  { label: '面试记录', icon: ListChecks, active: false },
  { label: '题库练习', icon: BookOpenCheck, active: false },
  { label: '我的收藏', icon: Heart, active: false },
]

const stats = [
  {
    label: '累计面试次数',
    value: '24',
    icon: CalendarCheck,
    trend: '较上周 +6',
  },
  {
    label: '平均得分',
    value: '85',
    suffix: '/100',
    icon: TrendingUp,
    trend: '较上周 +5.7',
  },
  {
    label: '已覆盖技术栈',
    value: '8',
    suffix: '个',
    icon: Layers3,
    tags: ['Vue3', 'Spring Boot', 'MySQL', 'Redis', '+4'],
  },
]

const histories = [
  { date: '2026-05-29 19:30', role: '前端工程师', score: 92, duration: '48 分钟', type: '技术面试' },
  { date: '2026-05-27 15:10', role: '后端开发工程师', score: 78, duration: '42 分钟', type: '技术面试' },
  { date: '2026-05-25 10:25', role: 'Java 开发工程师', score: 88, duration: '55 分钟', type: '技术面试' },
  { date: '2026-05-22 21:40', role: '全栈工程师', score: 81, duration: '50 分钟', type: '技术面试' },
  { date: '2026-05-20 09:15', role: '后端开发工程师', score: 74, duration: '40 分钟', type: '技术面试' },
]
</script>

<template>
  <main class="h-screen overflow-hidden bg-[#070d19] text-slate-300">
    <aside
      class="fixed inset-y-0 left-0 z-30 flex w-[240px] flex-col border-r border-slate-800/90 bg-[#050b14]/95 px-4 py-5 shadow-[18px_0_80px_rgba(0,0,0,0.32)] backdrop-blur-xl"
    >
      <a href="#" class="flex items-center gap-4 px-2" aria-label="AI Interviewer 工作台">
        <svg class="dashboard-logo size-16 shrink-0" viewBox="0 0 72 72" role="img" aria-label="AI Interviewer 标志">
          <defs>
            <linearGradient id="dashboardLogoStroke" x1="9" x2="60" y1="8" y2="64" gradientUnits="userSpaceOnUse">
              <stop stop-color="#60A5FA" />
              <stop offset="0.55" stop-color="#3B82F6" />
              <stop offset="1" stop-color="#2563EB" />
            </linearGradient>
          </defs>
          <path
            d="M36 6 60 19.5v28L47.5 54.5 53 66 36 57.5 12 47.5v-28L36 6Z"
            fill="#071326"
            stroke="url(#dashboardLogoStroke)"
            stroke-linejoin="round"
            stroke-width="4"
          />
          <text x="36" y="42" fill="#F8FAFC" font-size="22" font-weight="900" text-anchor="middle">AI</text>
        </svg>
        <div class="min-w-0">
          <p class="whitespace-nowrap text-lg font-black text-white">AI Interviewer</p>
          <p class="mt-1 text-sm tracking-[0.18em] text-slate-400">AI 面试陪练</p>
        </div>
      </a>

      <nav class="mt-8 space-y-2">
        <a
          v-for="item in menuItems"
          :key="item.label"
          href="#"
          class="group relative flex h-[50px] items-center gap-4 rounded-xl px-5 text-base font-bold transition"
          :class="
            item.active
              ? 'border border-blue-500/25 bg-blue-600/20 text-blue-300 shadow-[0_14px_40px_rgba(37,99,235,0.22)]'
              : 'text-slate-400 hover:bg-slate-900/70 hover:text-slate-100'
          "
        >
          <span
            v-if="item.active"
            class="absolute left-0 top-1/2 h-8 w-1 -translate-y-1/2 rounded-r-full bg-blue-400 shadow-[0_0_18px_rgba(59,130,246,0.85)]"
          ></span>
          <component :is="item.icon" class="size-6" stroke-width="2.2" />
          {{ item.label }}
        </a>
      </nav>

      <div class="absolute inset-x-4 bottom-5 space-y-3">
        <a href="#" class="flex h-11 items-center gap-4 rounded-xl px-4 text-base font-bold text-slate-400 transition hover:bg-slate-900/70 hover:text-slate-100">
          <Settings class="size-6" />
          偏好设置
        </a>

        <button
          class="flex w-full items-center gap-3 rounded-xl border border-amber-400/35 bg-[linear-gradient(135deg,rgba(251,191,36,0.14),rgba(15,23,42,0.7)_52%,rgba(180,83,9,0.12))] p-3 text-left shadow-[0_18px_42px_rgba(245,158,11,0.08)] transition hover:border-amber-300/60"
          type="button"
        >
          <span class="grid size-10 place-items-center rounded-xl bg-amber-400/10 text-amber-300">
            <Crown class="size-6" />
          </span>
          <span class="min-w-0 flex-1">
            <span class="block text-base font-black text-amber-300">升级专业版</span>
            <span class="mt-1 block text-sm text-slate-500">解锁更多高级功能</span>
          </span>
          <ChevronRight class="size-5 text-amber-300" />
        </button>

        <button
          class="flex w-full items-center gap-3 rounded-xl border border-slate-800 bg-slate-900/55 p-3 text-left transition hover:border-blue-500/40 hover:bg-slate-900"
          type="button"
        >
          <span class="grid size-12 shrink-0 place-items-center rounded-full bg-gradient-to-br from-slate-100 to-blue-200 text-base font-black text-slate-900">
            A
          </span>
          <span class="min-w-0 flex-1">
            <span class="block text-base font-black text-white">Alex</span>
            <span class="mt-0.5 block text-sm font-semibold text-blue-400">Free 版</span>
          </span>
          <ChevronDown class="size-5 text-slate-400" />
        </button>
      </div>
    </aside>

    <section class="h-screen min-w-0 pl-[240px]">
      <header
        class="flex h-16 items-center justify-end border-b border-slate-800/80 bg-[#070d19]/82 px-8 backdrop-blur-xl"
      >
        <div class="flex items-center gap-4">
          <button
            type="button"
            class="relative grid size-11 place-items-center rounded-xl border border-slate-800 bg-slate-950/50 text-slate-300 transition hover:border-blue-500/45 hover:text-blue-300"
            aria-label="通知"
          >
            <Bell class="size-5" />
            <span class="absolute right-3 top-2 size-2 rounded-full bg-blue-500 shadow-[0_0_12px_rgba(59,130,246,0.9)]"></span>
          </button>
          <button type="button" class="flex items-center gap-3 rounded-xl px-2 py-1 transition hover:bg-slate-900/70">
            <span class="grid size-10 place-items-center rounded-full bg-gradient-to-br from-slate-100 to-blue-200 text-sm font-black text-slate-900">
              A
            </span>
            <span class="hidden text-base font-black text-white sm:inline">Alex</span>
            <ChevronDown class="hidden size-5 text-slate-400 sm:block" />
          </button>
        </div>
      </header>

      <div class="flex h-[calc(100vh-64px)] flex-col gap-7 overflow-hidden px-6 py-5">
        <section>
          <h1 class="text-[28px] font-black leading-tight tracking-normal text-white">欢迎回来，开始今天的面试练习</h1>
          <p class="mt-2 text-sm font-medium text-slate-400">坚持练习，不断进步，拿下心仪 Offer！</p>
        </section>

        <section class="grid grid-cols-3 gap-4">
          <article
            v-for="item in stats"
            :key="item.label"
            class="dashboard-card flex h-[116px] min-w-0 items-center gap-4 overflow-hidden rounded-2xl border border-slate-800 bg-slate-900/36 p-4"
          >
            <div class="grid size-14 shrink-0 place-items-center rounded-2xl border border-blue-500/30 bg-blue-600/12 text-blue-400 shadow-[0_16px_42px_rgba(37,99,235,0.16)]">
              <component :is="item.icon" class="size-7" stroke-width="2.2" />
            </div>
            <div class="min-w-0 flex-1">
              <p class="truncate text-sm font-bold text-slate-200">{{ item.label }}</p>
              <div class="mt-2 flex items-end gap-1.5">
                <span class="text-[40px] font-black leading-none text-white">{{ item.value }}</span>
                <span v-if="item.suffix" class="pb-1 text-base font-medium text-slate-500">{{ item.suffix }}</span>
              </div>
              <div v-if="item.tags" class="mt-2 flex flex-nowrap gap-1 overflow-hidden">
                <span
                  v-for="tag in item.tags"
                  :key="tag"
                  class="shrink-0 rounded-full border border-slate-700 bg-slate-950/35 px-2 py-0.5 text-[11px] font-semibold text-slate-200"
                >
                  {{ tag }}
                </span>
              </div>
              <p v-else class="mt-2 flex items-center gap-1.5 text-sm font-bold text-slate-400">
                {{ item.trend }}
                <ArrowUpRight class="size-4 text-blue-400" />
              </p>
            </div>
          </article>
        </section>

        <section
          class="dashboard-grid relative h-[124px] overflow-hidden rounded-2xl border border-blue-500/35 bg-[linear-gradient(105deg,rgba(14,165,233,0.12),rgba(15,23,42,0.55)_40%,rgba(37,99,235,0.24))] px-7 py-5 shadow-[0_24px_80px_rgba(2,6,23,0.45)]"
        >
          <div class="relative z-10 flex h-full items-center justify-between gap-6">
            <div class="flex items-center gap-5">
              <div class="ai-orb shrink-0">
                <div class="ai-orb-core">AI</div>
              </div>
              <div>
                <h2 class="text-[28px] font-black tracking-normal text-white">新建模拟面试</h2>
                <p class="mt-2 text-base font-medium text-slate-400">选择岗位与面试类型，AI 为你定制专属面试体验</p>
              </div>
            </div>
            <button
              type="button"
              class="flex h-14 items-center justify-center gap-2 rounded-xl bg-blue-600 px-7 text-base font-black text-white shadow-[0_20px_55px_rgba(37,99,235,0.34)] transition hover:bg-blue-500 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-300"
            >
              <PlusCircle class="size-5" />
              新建模拟面试
            </button>
          </div>
        </section>

        <section class="overflow-hidden rounded-2xl border border-slate-800 bg-slate-900/34 shadow-[0_24px_80px_rgba(2,6,23,0.34)]">
          <div class="flex items-center justify-between border-b border-slate-800 px-6 py-2.5">
            <h2 class="text-lg font-black text-white">最近面试记录</h2>
            <a href="#" class="flex items-center gap-1 text-sm font-black text-blue-400 transition hover:text-blue-300">
              查看全部 >
            </a>
          </div>
          <div>
            <table class="w-full text-left">
              <thead>
                <tr class="border-b border-slate-800 text-sm font-bold text-slate-500">
                  <th class="px-6 py-2">日期</th>
                  <th class="px-6 py-2">岗位</th>
                  <th class="px-6 py-2">得分</th>
                  <th class="px-6 py-2">时长</th>
                  <th class="px-6 py-2">面试类型</th>
                  <th class="px-6 py-2 text-right">操作</th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="history in histories"
                  :key="`${history.date}-${history.role}`"
                  class="border-b border-slate-800/80 text-sm text-slate-300 last:border-b-0 hover:bg-slate-800/24"
                >
                  <td class="whitespace-nowrap px-6 py-2">{{ history.date }}</td>
                  <td class="whitespace-nowrap px-6 py-2 font-semibold text-slate-200">{{ history.role }}</td>
                  <td class="whitespace-nowrap px-6 py-2">
                    <span :class="history.score >= 80 ? 'text-blue-400' : 'text-slate-300'" class="text-lg font-black">
                      {{ history.score }}
                    </span>
                    <span class="ml-1 text-sm text-slate-500">/100</span>
                  </td>
                  <td class="whitespace-nowrap px-6 py-2">{{ history.duration }}</td>
                  <td class="whitespace-nowrap px-6 py-2">
                    <span class="inline-flex items-center gap-3">
                      <span class="size-2 rounded-full bg-emerald-400"></span>
                      {{ history.type }}
                    </span>
                  </td>
                  <td class="whitespace-nowrap px-6 py-2">
                    <div class="flex items-center justify-end gap-2">
                      <button
                        type="button"
                        class="rounded-lg border border-slate-700 px-3 py-1 text-sm font-bold text-slate-300 transition hover:border-blue-500/45 hover:text-blue-300"
                      >
                        查看报告
                      </button>
                      <button
                        type="button"
                        class="grid size-8 place-items-center rounded-lg text-slate-500 transition hover:bg-slate-800 hover:text-slate-200"
                        aria-label="更多操作"
                      >
                        <MoreHorizontal class="size-5" />
                      </button>
                    </div>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </section>
      </div>
    </section>
  </main>
</template>

<style scoped>
.dashboard-logo {
  overflow: visible;
  filter: drop-shadow(0 0 20px rgba(37, 99, 235, 0.55));
}

.dashboard-card {
  background:
    radial-gradient(circle at 12% 20%, rgba(37, 99, 235, 0.16), transparent 34%),
    rgba(15, 23, 42, 0.38);
}

.dashboard-grid::before {
  position: absolute;
  inset: 0;
  pointer-events: none;
  content: '';
  background-image:
    linear-gradient(rgba(59, 130, 246, 0.12) 1px, transparent 1px),
    linear-gradient(90deg, rgba(59, 130, 246, 0.12) 1px, transparent 1px);
  background-size: 34px 34px;
  mask-image: linear-gradient(90deg, black 0 40%, transparent 70%);
  opacity: 0.5;
}

.ai-orb {
  position: relative;
  display: grid;
  width: 112px;
  height: 72px;
  place-items: center;
}

.ai-orb::before {
  position: absolute;
  inset: auto 0 2px;
  height: 30px;
  content: '';
  border: 1px solid rgba(59, 130, 246, 0.7);
  border-radius: 999px;
  box-shadow:
    0 0 28px rgba(37, 99, 235, 0.42),
    inset 0 0 24px rgba(37, 99, 235, 0.28);
}

.ai-orb-core {
  position: relative;
  display: grid;
  width: 54px;
  height: 62px;
  place-items: center;
  clip-path: polygon(50% 0, 94% 25%, 94% 75%, 50% 100%, 6% 75%, 6% 25%);
  background: linear-gradient(135deg, #60a5fa, #2563eb 62%, #1d4ed8);
  color: white;
  font-size: 1.45rem;
  font-weight: 900;
  box-shadow:
    inset 0 0 24px rgba(191, 219, 254, 0.52),
    0 0 42px rgba(37, 99, 235, 0.8);
}
</style>
