<script setup lang="ts">
import { computed, ref, watch } from 'vue'
import { RouterLink, useRouter } from 'vue-router'
import {
  BookOpenCheck,
  BrainCircuit,
  Briefcase,
  Check,
  ChevronDown,
  ChevronLeft,
  ChevronRight,
  Crown,
  FileBadge,
  Heart,
  Home,
  ListChecks,
  Network,
  Settings,
  Target,
  Video,
} from 'lucide-vue-next'

const router = useRouter()

const menuItems = [
  { label: '工作台', icon: Home, to: '/dashboard', active: false },
  { label: '模拟面试', icon: Video, to: '/interview-config', active: true },
  { label: '面试记录', icon: ListChecks, to: '#', active: false },
  { label: '题库练习', icon: BookOpenCheck, to: '#', active: false },
  { label: '我的收藏', icon: Heart, to: '#', active: false },
]

const features = [
  { label: '智能生成贴合岗位的面试题目', icon: BrainCircuit },
  { label: '覆盖技术深度与广度', icon: Network },
  { label: '真实场景，提升面试通过率', icon: Target },
]

const roleStackOptions: Record<string, string[]> = {
  后端: ['Java', 'Spring Boot', 'MySQL', 'Redis', 'Docker', 'Kafka'],
  前端: ['Vue3', 'React', 'TypeScript', 'Vite', 'Tailwind CSS', 'Node.js'],
  全栈: ['Vue3', 'Node.js', 'Spring Boot', 'MySQL', 'Redis', 'Docker'],
  'Java 开发': ['Java', 'Spring Boot', 'MyBatis', 'MySQL', 'Redis', 'JVM'],
}

const defaultSelectedStacks: Record<string, string[]> = {
  后端: ['Spring Boot', 'MySQL', 'Redis'],
  前端: ['Vue3', 'TypeScript', 'Vite'],
  全栈: ['Vue3', 'Node.js', 'MySQL'],
  'Java 开发': ['Java', 'Spring Boot', 'MySQL'],
}

const jobRole = ref('后端')
const selectedStacks = ref([...(defaultSelectedStacks[jobRole.value] ?? [])])
const difficulty = ref('中级')

const techStacks = computed(() => roleStackOptions[jobRole.value] ?? roleStackOptions['后端'])
const difficulties = ['初级', '中级', '高级']

watch(jobRole, (role) => {
  selectedStacks.value = [...(defaultSelectedStacks[role] ?? [])]
})

const toggleStack = (stack: string) => {
  selectedStacks.value = selectedStacks.value.includes(stack)
    ? selectedStacks.value.filter((item) => item !== stack)
    : [...selectedStacks.value, stack]
}

const isStackSelected = (stack: string) => selectedStacks.value.includes(stack)

const cancelConfig = () => {
  router.push('/dashboard')
}

const startInterview = () => {
  console.log({
    jobRole: jobRole.value,
    techStacks: selectedStacks.value,
    difficulty: difficulty.value,
  })
}
</script>

<template>
  <main class="config-shell h-screen overflow-hidden bg-[#050b14] text-slate-200">
    <aside
      class="fixed inset-y-0 left-0 z-30 hidden w-[240px] flex-col border-r border-slate-800/90 bg-[#050b14]/95 px-4 py-5 shadow-[18px_0_80px_rgba(0,0,0,0.32)] backdrop-blur-xl xl:flex"
    >
      <RouterLink to="/dashboard" class="flex items-center gap-4 px-2" aria-label="AI Interviewer 工作台">
        <svg class="config-logo size-16 shrink-0" viewBox="0 0 72 72" role="img" aria-label="AI Interviewer 标志">
          <defs>
            <linearGradient id="configLogoStroke" x1="9" x2="60" y1="8" y2="64" gradientUnits="userSpaceOnUse">
              <stop stop-color="#60A5FA" />
              <stop offset="0.55" stop-color="#3B82F6" />
              <stop offset="1" stop-color="#2563EB" />
            </linearGradient>
          </defs>
          <path
            d="M36 6 60 19.5v28L47.5 54.5 53 66 36 57.5 12 47.5v-28L36 6Z"
            fill="#071326"
            stroke="url(#configLogoStroke)"
            stroke-linejoin="round"
            stroke-width="4"
          />
          <text x="36" y="42" fill="#F8FAFC" font-size="22" font-weight="900" text-anchor="middle">AI</text>
        </svg>
        <div class="min-w-0">
          <p class="whitespace-nowrap text-lg font-black text-white">AI Interviewer</p>
          <p class="mt-1 text-sm tracking-[0.18em] text-slate-400">AI 面试陪练</p>
        </div>
      </RouterLink>

      <nav class="mt-8 space-y-2">
        <template v-for="item in menuItems" :key="item.label">
          <RouterLink
            v-if="item.to !== '#'"
            :to="item.to"
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
          </RouterLink>
          <a
            v-else
            href="#"
            class="group relative flex h-[50px] items-center gap-4 rounded-xl px-5 text-base font-bold text-slate-400 transition hover:bg-slate-900/70 hover:text-slate-100"
          >
            <component :is="item.icon" class="size-6" stroke-width="2.2" />
            {{ item.label }}
          </a>
        </template>
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

    <section class="relative h-screen min-w-0 overflow-y-auto px-5 pb-8 pt-7 sm:px-8 xl:pl-[280px] xl:pr-12">
      <header class="relative z-10 mx-auto flex max-w-[1400px] items-center">
        <RouterLink
          to="/dashboard"
          class="group inline-flex items-center gap-2.5 text-slate-300 transition hover:text-blue-300"
          title="返回工作台"
        >
          <span
            class="grid size-8 place-items-center rounded-full border border-slate-700/75 bg-slate-950/35 text-slate-400 shadow-[0_0_24px_rgba(15,23,42,0.9)] transition group-hover:border-blue-500/60 group-hover:text-blue-300"
          >
            <ChevronLeft class="size-4.5" stroke-width="2.4" />
          </span>
          <span class="text-lg font-extrabold tracking-normal text-slate-100">面试配置</span>
        </RouterLink>
      </header>

      <div class="config-content-grid relative z-10 mx-auto grid max-w-[1400px] gap-0 md:grid-cols-[minmax(250px,0.36fr)_minmax(420px,0.64fr)] xl:grid-cols-[minmax(340px,0.36fr)_minmax(620px,0.64fr)]">
        <section
          class="config-panel relative min-h-[500px] overflow-hidden rounded-2xl border border-slate-700/65 bg-slate-950/25 px-5 py-6 shadow-[0_24px_90px_rgba(0,0,0,0.32)] sm:px-6 xl:min-h-[540px] xl:px-8 xl:py-7"
        >
          <div class="absolute inset-x-0 top-0 h-px bg-gradient-to-r from-transparent via-blue-400/55 to-transparent"></div>
          <div class="holo-stage mx-auto">
            <div class="holo-ring"></div>
            <div class="holo-card">
              <FileBadge class="size-20 text-blue-400" stroke-width="1.45" />
              <span class="holo-check">
                <Check class="size-5" stroke-width="3" />
              </span>
            </div>
            <div class="holo-plinth"></div>
          </div>

          <div class="mt-7 max-w-[520px] xl:mt-8">
            <h1 class="text-[20px] font-extrabold leading-tight tracking-normal text-slate-100 xl:text-[26px]">个性化定制专属面试</h1>
            <p class="mt-3 text-sm font-medium leading-7 text-slate-400">
              根据岗位、技术栈和难度智能生成面试题目，让 AI 面试官更懂你的目标与背景。
            </p>
          </div>

          <div class="mt-7 space-y-4">
            <div v-for="feature in features" :key="feature.label" class="flex items-center gap-4">
              <span class="grid size-8 shrink-0 place-items-center rounded-xl border border-blue-500/25 bg-blue-500/10 text-blue-400 shadow-[0_0_24px_rgba(37,99,235,0.14)]">
                <component :is="feature.icon" class="size-4.5" stroke-width="2.2" />
              </span>
              <span class="text-sm font-bold text-slate-300">{{ feature.label }}</span>
            </div>
          </div>
        </section>

        <form
          class="config-form-card relative z-20 min-h-[500px] rounded-2xl border border-slate-700 bg-slate-800/85 px-6 py-8 shadow-[inset_0_1px_0_rgba(255,255,255,0.04),0_30px_100px_rgba(0,0,0,0.42)] backdrop-blur-2xl sm:px-8 lg:px-10 xl:min-h-[540px] xl:px-11"
          @submit.prevent="startInterview"
        >
          <div class="text-center">
            <h2 class="text-[28px] font-black tracking-normal text-white sm:text-[34px]">新建模拟面试</h2>
            <p class="mt-4 text-base font-medium text-slate-400">完成配置后即可开始你的 AI 面试陪练</p>
          </div>

          <div class="config-form-body">
            <label class="config-field">
              <span class="config-field-label">面试岗位</span>
              <span class="config-field-control flex items-center gap-4 rounded-xl border border-slate-700 bg-slate-950/28 px-5 text-slate-100 transition focus-within:border-blue-500/75 focus-within:ring-2 focus-within:ring-blue-500/25">
                <Briefcase class="size-5 shrink-0 text-blue-400" stroke-width="2.1" />
                <select
                  v-model="jobRole"
                  class="h-full flex-1 appearance-none bg-transparent text-base font-bold text-slate-100 outline-none"
                  aria-label="面试岗位"
                >
                  <option class="bg-slate-900 text-slate-100" value="后端">后端</option>
                  <option class="bg-slate-900 text-slate-100" value="前端">前端</option>
                  <option class="bg-slate-900 text-slate-100" value="全栈">全栈</option>
                  <option class="bg-slate-900 text-slate-100" value="Java 开发">Java 开发</option>
                </select>
                <ChevronDown class="size-5 shrink-0 text-slate-500" />
              </span>
            </label>

            <section class="config-field">
              <h3 class="config-field-label">
                技术栈
                <span class="font-bold text-slate-400">（可多选）</span>
              </h3>
              <div class="config-tech-tags flex flex-wrap">
                <button
                  v-for="stack in techStacks"
                  :key="stack"
                  type="button"
                  class="config-tech-tag inline-flex items-center justify-center rounded-xl border font-bold transition duration-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-300"
                  :class="
                    isStackSelected(stack)
                      ? 'border-blue-400/65 bg-blue-600 text-white shadow-[0_12px_34px_rgba(37,99,235,0.24)]'
                      : 'border-slate-700 bg-transparent text-slate-300 hover:border-blue-500/45 hover:bg-slate-900/50 hover:text-slate-100'
                  "
                  :aria-pressed="isStackSelected(stack)"
                  @click="toggleStack(stack)"
                >
                  <span
                    class="grid size-6 place-items-center rounded-full border transition"
                    :class="
                      isStackSelected(stack)
                        ? 'border-blue-200/35 bg-blue-500 text-white'
                        : 'border-slate-600 bg-slate-950/20 text-transparent'
                    "
                  >
                    <Check class="size-4" stroke-width="3" />
                  </span>
                  {{ stack }}
                </button>
              </div>
            </section>

            <section class="config-field">
              <h3 class="config-field-label">难度选择</h3>
              <div class="config-difficulty-group grid overflow-hidden rounded-xl border border-slate-700 bg-slate-950/18 sm:grid-cols-3">
                <label
                  v-for="level in difficulties"
                  :key="level"
                  class="group flex h-14 cursor-pointer items-center justify-center gap-3 border-slate-700 px-5 transition hover:bg-slate-900/45 sm:border-r sm:last:border-r-0"
                  :class="difficulty === level ? 'text-white' : 'text-slate-400'"
                >
                  <input v-model="difficulty" class="sr-only" type="radio" name="difficulty" :value="level" />
                  <span
                    class="grid size-6 place-items-center rounded-full border transition"
                    :class="
                      difficulty === level
                        ? 'border-blue-500 bg-blue-500/10 shadow-[0_0_18px_rgba(59,130,246,0.42)]'
                        : 'border-slate-600 bg-slate-950/30 group-hover:border-slate-500'
                    "
                  >
                    <span v-if="difficulty === level" class="size-3 rounded-full bg-blue-500"></span>
                  </span>
                  <span class="text-base font-bold" :class="difficulty === level ? 'text-white' : 'text-slate-400'">
                    {{ level }}
                  </span>
                </label>
              </div>
            </section>
          </div>

          <div class="mt-11 border-t border-slate-700/75 pt-8">
            <div class="flex flex-col justify-end gap-4 sm:flex-row">
              <button
                type="button"
                class="h-14 rounded-xl border border-slate-700 bg-slate-900/35 px-10 text-base font-black text-slate-100 transition hover:border-slate-500 hover:bg-slate-800"
                @click="cancelConfig"
              >
                取消
              </button>
              <button
                type="submit"
                class="h-14 rounded-xl bg-blue-600 px-12 text-base font-black text-white shadow-[0_20px_55px_rgba(37,99,235,0.36)] transition hover:bg-blue-500 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-300"
              >
                开始面试
              </button>
            </div>
          </div>
        </form>
      </div>
    </section>
  </main>
</template>

<style scoped>
.config-shell {
  background:
    radial-gradient(circle at 78% 12%, rgba(37, 99, 235, 0.16), transparent 26%),
    radial-gradient(circle at 28% 18%, rgba(14, 165, 233, 0.1), transparent 28%),
    linear-gradient(145deg, #020617 0%, #07101f 48%, #020617 100%);
}

.config-shell::before {
  position: fixed;
  inset: 0;
  pointer-events: none;
  content: '';
  background-image:
    linear-gradient(rgba(59, 130, 246, 0.055) 1px, transparent 1px),
    linear-gradient(90deg, rgba(59, 130, 246, 0.055) 1px, transparent 1px);
  background-size: 48px 48px;
  mask-image: linear-gradient(180deg, transparent, black 16%, black 82%, transparent);
}

.config-logo {
  overflow: visible;
  filter: drop-shadow(0 0 20px rgba(37, 99, 235, 0.55));
}

.config-content-grid {
  margin-top: 44px;
}

.config-panel {
  z-index: 10;
  background:
    radial-gradient(circle at 50% 18%, rgba(37, 99, 235, 0.14), transparent 36%),
    linear-gradient(180deg, rgba(15, 23, 42, 0.48), rgba(2, 6, 23, 0.28));
}

.config-panel::before {
  position: absolute;
  inset: 0;
  pointer-events: none;
  content: '';
  background-image:
    linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px),
    linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px);
  background-position: center bottom;
  background-size: 38px 38px;
  mask-image: linear-gradient(180deg, transparent 8%, black 45%, transparent 92%);
  opacity: 0.55;
}

.holo-stage {
  position: relative;
  display: grid;
  width: min(100%, 320px);
  height: 260px;
  place-items: center;
}

.holo-ring {
  position: absolute;
  bottom: 22px;
  width: 220px;
  height: 76px;
  border: 1px solid rgba(59, 130, 246, 0.72);
  border-radius: 50%;
  box-shadow:
    0 0 42px rgba(37, 99, 235, 0.44),
    inset 0 0 34px rgba(37, 99, 235, 0.34);
}

.holo-ring::before,
.holo-ring::after {
  position: absolute;
  inset: 10px 22px;
  content: '';
  border: 1px solid rgba(14, 165, 233, 0.48);
  border-radius: inherit;
}

.holo-ring::after {
  inset: 23px 52px;
  background: radial-gradient(circle, rgba(59, 130, 246, 0.46), transparent 62%);
  filter: blur(2px);
}

.holo-card {
  position: relative;
  display: grid;
  width: 132px;
  height: 162px;
  place-items: center;
  border: 1px solid rgba(59, 130, 246, 0.78);
  border-radius: 22px;
  background:
    linear-gradient(155deg, rgba(37, 99, 235, 0.38), rgba(15, 23, 42, 0.78) 58%),
    rgba(15, 23, 42, 0.7);
  box-shadow:
    0 0 50px rgba(37, 99, 235, 0.52),
    inset 0 0 42px rgba(37, 99, 235, 0.18);
  transform: perspective(760px) rotateX(9deg) rotateY(-12deg) translateY(-18px);
}

.holo-card::after {
  position: absolute;
  inset: 16px;
  content: '';
  border-radius: 16px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.16), transparent 38%);
  pointer-events: none;
}

.holo-check {
  position: absolute;
  top: 12px;
  right: -18px;
  display: grid;
  width: 44px;
  height: 44px;
  place-items: center;
  border-radius: 999px;
  background: linear-gradient(135deg, #38bdf8, #2563eb);
  color: white;
  box-shadow: 0 0 32px rgba(56, 189, 248, 0.72);
}

.holo-plinth {
  position: absolute;
  bottom: 54px;
  width: 1px;
  height: 100px;
  background: linear-gradient(180deg, rgba(125, 211, 252, 0.95), rgba(37, 99, 235, 0));
  box-shadow: 0 0 28px rgba(59, 130, 246, 0.95);
}

.config-form-card {
  margin-left: -16px;
  background:
    radial-gradient(circle at 50% 0%, rgba(59, 130, 246, 0.09), transparent 34%),
    rgba(30, 41, 59, 0.88);
}

@media (min-width: 1280px) {
  .config-form-card {
    margin-left: -28px;
  }
}

.config-form-body {
  display: flex;
  flex-direction: column;
  gap: 28px;
  margin-top: 42px;
}

.config-field {
  display: block;
}

.config-field-label {
  display: block;
  color: #f1f5f9;
  font-size: 18px;
  font-weight: 900;
  line-height: 1.25;
}

.config-field-control {
  height: 64px;
  margin-top: 18px;
}

.config-tech-tags {
  gap: 12px 14px;
  margin-top: 16px;
}

.config-tech-tag {
  min-width: 116px;
  height: 46px;
  gap: 10px;
  padding: 0 14px;
  font-size: 14px;
}

.config-difficulty-group {
  margin-top: 18px;
}
</style>
