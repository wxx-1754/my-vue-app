<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import {
  AudioLines,
  BarChart3,
  Check,
  Eye,
  EyeOff,
  Github,
  Lock,
  Mail,
  Play,
  ShieldCheck,
  Sparkles,
} from 'lucide-vue-next'

const router = useRouter()
const email = ref('')
const password = ref('')
const showPassword = ref(false)

const checklist = ['算法思路清晰', '表达结构完整', '追问应答稳定']
const waveBars = [28, 44, 32, 62, 72, 40, 52, 86, 56, 70, 38, 64]

const handleLogin = () => {
  router.push('/dashboard')
}
</script>

<template>
  <main class="min-h-screen overflow-hidden bg-slate-950 text-slate-50 lg:h-screen">
    <div class="grid min-h-screen lg:h-screen lg:grid-cols-2">
      <section
        class="relative isolate flex min-h-[720px] flex-col overflow-hidden border-b border-blue-500/10 bg-[#020814] px-6 py-7 sm:px-10 lg:h-screen lg:border-b-0 lg:border-r lg:px-12 xl:px-14"
      >
        <div class="absolute inset-0 -z-10 bg-[radial-gradient(circle_at_45%_54%,rgba(37,99,235,0.22),transparent_30%),radial-gradient(circle_at_14%_18%,rgba(14,165,233,0.16),transparent_32%),linear-gradient(145deg,#020617_0%,#071326_54%,#020617_100%)]"></div>
        <div class="tech-grid absolute inset-x-0 bottom-0 -z-10 h-2/3 opacity-45"></div>
        <div class="absolute inset-0 -z-10 bg-[linear-gradient(90deg,rgba(15,23,42,0.8),transparent_42%,rgba(2,6,23,0.45))]"></div>

        <a href="#" class="flex w-fit items-center gap-4" aria-label="AI Interviewer 首页">
          <svg
            class="brand-mark size-14 shrink-0 sm:size-16"
            viewBox="0 0 72 72"
            role="img"
            aria-label="AI Interviewer 标志"
          >
            <defs>
              <linearGradient id="brandMarkStroke" x1="9" x2="60" y1="8" y2="64" gradientUnits="userSpaceOnUse">
                <stop stop-color="#60A5FA" />
                <stop offset="0.55" stop-color="#3B82F6" />
                <stop offset="1" stop-color="#2563EB" />
              </linearGradient>
              <filter id="brandMarkGlow" x="-30%" y="-30%" width="160%" height="160%">
                <feGaussianBlur stdDeviation="2.2" result="blur" />
                <feMerge>
                  <feMergeNode in="blur" />
                  <feMergeNode in="SourceGraphic" />
                </feMerge>
              </filter>
            </defs>
            <path
              d="M36 6 60 19.5v28L47.5 54.5 53 66 36 57.5 12 47.5v-28L36 6Z"
              fill="#071326"
              stroke="url(#brandMarkStroke)"
              stroke-linejoin="round"
              stroke-width="4"
              filter="url(#brandMarkGlow)"
            />
            <text
              x="36"
              y="42"
              fill="#F8FAFC"
              font-size="22"
              font-weight="900"
              letter-spacing="0"
              text-anchor="middle"
            >
              AI
            </text>
          </svg>
          <div>
            <p class="text-2xl font-extrabold tracking-tight text-white sm:text-3xl">AI Interviewer</p>
            <p class="mt-0.5 text-sm font-medium tracking-[0.24em] text-slate-400">AI 面试陪练</p>
          </div>
        </a>

        <div class="hero-copy max-w-[720px]">
          <p class="hero-title text-balance font-black tracking-normal text-white">
            你的私人 <span class="text-blue-400 drop-shadow-[0_0_22px_rgba(59,130,246,0.75)]">AI</span>
            面试官，<br />
            助你斩获大厂
            <span class="text-blue-400 drop-shadow-[0_0_22px_rgba(59,130,246,0.75)]">Offer</span>
          </p>
          <p class="mt-5 text-base font-medium tracking-[0.16em] text-slate-400 sm:text-lg">
            模拟真实面试 · 智能评估 · 精准复盘
          </p>
        </div>

        <div class="relative mt-auto h-[380px] min-h-[380px] w-full sm:h-[430px] xl:h-[470px]">
          <div class="network-line left-[31%] top-[13%] w-[220px] rotate-[28deg]"></div>
          <div class="network-line right-[14%] top-[17%] w-[180px] -rotate-[24deg]"></div>
          <div class="network-dot left-[28%] top-[18%]"></div>
          <div class="network-dot left-[46%] top-[10%]"></div>
          <div class="network-dot right-[18%] top-[10%]"></div>
          <div class="network-dot right-[8%] top-[1%]"></div>

          <div
            class="glass-card float-slow absolute left-0 top-14 w-[178px] rounded-2xl border border-blue-400/25 bg-slate-900/45 p-4 shadow-[0_18px_70px_rgba(2,6,23,0.45)] backdrop-blur-xl sm:left-2 sm:top-16 sm:w-[230px]"
          >
            <div class="mb-3 flex items-center justify-between">
              <p class="text-sm font-bold text-blue-100">模拟面试</p>
              <ShieldCheck class="size-4 text-blue-300" />
            </div>
            <div class="space-y-2.5">
              <div v-for="item in checklist" :key="item" class="flex items-center gap-2">
                <span class="grid size-5 shrink-0 place-items-center rounded-full bg-blue-500/15 text-blue-300">
                  <Check class="size-3.5" stroke-width="3" />
                </span>
                <span class="h-1.5 flex-1 rounded-full bg-blue-300/20">
                  <span class="block h-full w-4/5 rounded-full bg-blue-400/60"></span>
                </span>
                <Check class="size-3.5 text-blue-400" />
              </div>
            </div>
          </div>

          <div
            class="glass-card float-delay absolute bottom-24 left-0 w-[168px] rounded-2xl border border-blue-400/20 bg-slate-950/40 p-3 backdrop-blur-xl sm:left-5 sm:w-[210px] sm:p-4"
          >
            <div class="flex h-24 items-end gap-2 border-b border-l border-blue-400/15 px-2 pb-3">
              <span class="h-7 w-1.5 rounded-full bg-blue-500/60"></span>
              <span class="h-11 w-1.5 rounded-full bg-blue-400"></span>
              <span class="h-9 w-1.5 rounded-full bg-blue-500/70"></span>
              <span class="h-16 w-1.5 rounded-full bg-blue-300"></span>
              <span class="h-12 w-1.5 rounded-full bg-blue-500/80"></span>
              <span class="h-20 w-1.5 rounded-full bg-sky-300"></span>
              <BarChart3 class="ml-auto size-8 text-blue-400" />
            </div>
          </div>

          <div
            class="glass-card float-delay absolute right-0 top-20 w-[178px] rounded-2xl border border-blue-400/25 bg-slate-900/45 p-4 backdrop-blur-xl sm:right-4 sm:w-[225px]"
          >
            <p class="mb-3 text-sm font-bold text-blue-100">智能评估</p>
            <div class="flex items-center gap-4">
              <div class="score-ring grid size-16 shrink-0 place-items-center rounded-full">
                <span class="text-xl font-black text-white">92</span>
              </div>
              <div class="flex-1 space-y-2">
                <span class="block h-2 w-full rounded-full bg-blue-300/15"></span>
                <span class="block h-2 w-4/5 rounded-full bg-blue-500"></span>
                <span class="block h-2 w-3/5 rounded-full bg-blue-400/65"></span>
              </div>
            </div>
          </div>

          <div
            class="glass-card float-slow absolute bottom-20 right-0 w-[190px] rounded-2xl border border-blue-400/20 bg-slate-950/45 p-4 backdrop-blur-xl sm:right-5 sm:w-[240px]"
          >
            <div class="mb-2 flex items-center justify-between">
              <p class="text-sm font-bold text-blue-100">精准复盘</p>
              <AudioLines class="size-4 text-blue-300" />
            </div>
            <div class="flex items-center gap-3">
              <span class="grid size-10 place-items-center rounded-full bg-blue-500/15 text-blue-300">
                <Play class="size-4 fill-current" />
              </span>
              <div class="flex h-14 flex-1 items-center gap-1">
                <span
                  v-for="(height, index) in waveBars"
                  :key="`${height}-${index}`"
                  class="w-1 rounded-full bg-blue-400"
                  :style="{ height: `${height}%`, opacity: `${0.42 + index * 0.035}` }"
                ></span>
              </div>
            </div>
          </div>

          <div class="absolute inset-x-0 bottom-2 mx-auto h-36 max-w-[520px] rounded-[50%] border border-blue-500/45 bg-blue-500/10 blur-[0.5px]"></div>
          <div class="holo-base absolute inset-x-0 bottom-11 mx-auto h-20 max-w-[360px] rounded-[50%]"></div>
          <div class="hex-wrap absolute left-1/2 top-[28%] -translate-x-1/2">
            <div class="hex-aura"></div>
            <div class="hexagon grid place-items-center">
              <span class="text-6xl font-black tracking-normal text-white drop-shadow-[0_0_24px_rgba(191,219,254,0.95)]">
                AI
              </span>
            </div>
            <div class="absolute left-1/2 top-full h-24 w-px -translate-x-1/2 bg-gradient-to-b from-blue-300 to-transparent"></div>
          </div>
        </div>
      </section>

      <section
        class="relative flex min-h-screen items-center justify-center overflow-hidden bg-[radial-gradient(circle_at_52%_44%,rgba(30,64,175,0.18),transparent_33%),linear-gradient(145deg,#020617_0%,#0f172a_54%,#020617_100%)] px-5 py-10 lg:h-screen"
      >
        <div class="absolute inset-y-0 left-0 hidden w-px bg-gradient-to-b from-transparent via-blue-400/30 to-transparent lg:block"></div>
        <div class="w-full max-w-[540px]">
          <form
            class="rounded-2xl border border-slate-700/90 bg-slate-800/50 px-6 py-8 shadow-[0_30px_100px_rgba(0,0,0,0.45)] backdrop-blur-2xl sm:px-10 sm:py-10"
            @submit.prevent="handleLogin"
          >
            <div class="text-center">
              <div class="mx-auto mb-4 grid size-11 place-items-center rounded-2xl border border-blue-400/25 bg-blue-500/10 text-blue-300">
                <Sparkles class="size-6" />
              </div>
              <h1 class="text-3xl font-black tracking-normal text-white sm:text-4xl">欢迎回来</h1>
              <p class="mt-3 text-base font-medium text-slate-400">登录你的账号，开启下一场模拟面试</p>
            </div>

            <div class="auth-field-stack mt-9">
              <label class="flex flex-col gap-3">
                <span class="block text-sm font-bold text-slate-100">邮箱</span>
                <span
                  class="flex h-14 items-center gap-4 rounded-xl border border-slate-700 bg-slate-950/20 px-4 text-slate-300 transition duration-200 focus-within:border-blue-500 focus-within:ring-2 focus-within:ring-blue-500/45"
                >
                  <Mail class="size-5 shrink-0 text-slate-400" />
                  <input
                    v-model="email"
                    type="email"
                    autocomplete="email"
                    placeholder="输入你的邮箱地址"
                    class="h-full min-w-0 flex-1 bg-transparent text-base font-medium text-white outline-none placeholder:text-slate-500"
                  />
                </span>
              </label>

              <label class="flex flex-col gap-3">
                <span class="block text-sm font-bold text-slate-100">密码</span>
                <span
                  class="flex h-14 items-center gap-4 rounded-xl border border-slate-700 bg-slate-950/20 px-4 text-slate-300 transition duration-200 focus-within:border-blue-500 focus-within:ring-2 focus-within:ring-blue-500/45"
                >
                  <Lock class="size-5 shrink-0 text-slate-400" />
                  <input
                    v-model="password"
                    :type="showPassword ? 'text' : 'password'"
                    autocomplete="current-password"
                    placeholder="输入你的密码"
                    class="h-full min-w-0 flex-1 bg-transparent text-base font-medium text-white outline-none placeholder:text-slate-500"
                  />
                  <button
                    type="button"
                    class="grid size-8 shrink-0 place-items-center rounded-lg text-slate-400 transition hover:bg-slate-700/60 hover:text-blue-300 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500/70"
                    :aria-label="showPassword ? '隐藏密码' : '显示密码'"
                    @click="showPassword = !showPassword"
                  >
                    <Eye v-if="showPassword" class="size-5" />
                    <EyeOff v-else class="size-5" />
                  </button>
                </span>
              </label>
            </div>

            <div class="auth-action-row flex justify-end">
              <a href="#" class="text-sm font-bold text-blue-400 transition hover:text-blue-300">忘记密码？</a>
            </div>

            <div class="auth-submit-wrap">
              <button
                type="submit"
                class="flex h-14 w-full items-center justify-center rounded-xl bg-blue-600 text-lg font-black text-white shadow-[0_18px_40px_rgba(37,99,235,0.35)] transition duration-200 hover:bg-blue-500 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-300 focus-visible:ring-offset-2 focus-visible:ring-offset-slate-900"
              >
                登录
              </button>
            </div>

            <div class="auth-divider flex items-center gap-5 text-sm font-bold text-slate-500">
              <span class="h-px flex-1 bg-slate-700/80"></span>
              <span>或</span>
              <span class="h-px flex-1 bg-slate-700/80"></span>
            </div>

            <button
              type="button"
              class="flex h-14 w-full items-center justify-center gap-3 rounded-xl border border-slate-500 bg-transparent text-lg font-black text-white transition duration-200 hover:border-blue-400 hover:bg-blue-500/10 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500/70"
            >
              <Github class="size-6" />
              GitHub 一键授权登录
            </button>

            <p class="auth-register text-center text-base font-medium text-slate-400">
              还没有账号？
              <a href="#" class="font-bold text-blue-400 transition hover:text-blue-300">立即注册</a>
            </p>
          </form>

          <p class="mt-8 text-center text-xs leading-6 text-slate-500">
            登录即代表你同意我们的
            <a href="#" class="font-bold text-blue-400 transition hover:text-blue-300">《用户协议》</a>
            和
            <a href="#" class="font-bold text-blue-400 transition hover:text-blue-300">《隐私政策》</a>
          </p>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.brand-mark {
  overflow: visible;
  filter: drop-shadow(0 0 18px rgba(37, 99, 235, 0.32));
}

.hero-copy {
  margin-top: clamp(54px, 7vh, 88px);
}

.hero-title {
  font-size: clamp(2.15rem, 4.45vw, 3.45rem);
  line-height: 1.18;
}

.auth-field-stack {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.auth-action-row {
  padding-top: 0.75rem;
}

.auth-submit-wrap {
  padding-top: 0.9rem;
}

.auth-divider {
  padding-top: 1.15rem;
  padding-bottom: 1.1rem;
}

.auth-register {
  margin-top: 1.15rem;
}

.tech-grid {
  background-image:
    linear-gradient(rgba(37, 99, 235, 0.14) 1px, transparent 1px),
    linear-gradient(90deg, rgba(37, 99, 235, 0.14) 1px, transparent 1px);
  background-size: 42px 42px;
  mask-image: linear-gradient(to top, black, transparent);
  transform: perspective(560px) rotateX(62deg) scale(1.25);
  transform-origin: bottom;
}

.glass-card {
  transform-style: preserve-3d;
}

.glass-card::before {
  position: absolute;
  inset: 0;
  pointer-events: none;
  content: '';
  border-radius: inherit;
  background: linear-gradient(135deg, rgba(96, 165, 250, 0.18), transparent 42%);
}

.score-ring {
  background:
    radial-gradient(circle at center, #0f172a 58%, transparent 59%),
    conic-gradient(#38bdf8 0 331deg, rgba(30, 64, 175, 0.35) 331deg 360deg);
  box-shadow: inset 0 0 20px rgba(59, 130, 246, 0.24), 0 0 20px rgba(59, 130, 246, 0.22);
}

.network-line,
.network-dot {
  position: absolute;
  pointer-events: none;
}

.network-line {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.85), transparent);
}

.network-dot {
  width: 7px;
  height: 7px;
  border-radius: 999px;
  background: #3b82f6;
  box-shadow: 0 0 20px #3b82f6;
}

.holo-base {
  background:
    radial-gradient(circle, rgba(56, 189, 248, 0.5) 0 18%, transparent 19%),
    radial-gradient(ellipse, rgba(37, 99, 235, 0.45) 0 42%, transparent 43%);
  border: 1px solid rgba(59, 130, 246, 0.8);
  box-shadow:
    0 0 34px rgba(59, 130, 246, 0.55),
    inset 0 0 30px rgba(59, 130, 246, 0.35);
}

.hex-wrap {
  width: 170px;
  height: 190px;
  animation: hover-pulse 5.8s ease-in-out infinite;
}

.hexagon,
.hex-aura {
  position: absolute;
  inset: 0;
  clip-path: polygon(50% 0, 94% 25%, 94% 75%, 50% 100%, 6% 75%, 6% 25%);
}

.hexagon {
  background:
    linear-gradient(135deg, rgba(96, 165, 250, 0.95), rgba(37, 99, 235, 0.54) 42%, rgba(29, 78, 216, 0.95)),
    linear-gradient(45deg, transparent 35%, rgba(255, 255, 255, 0.35), transparent 65%);
  border: 1px solid rgba(191, 219, 254, 0.75);
  box-shadow:
    inset 0 0 32px rgba(147, 197, 253, 0.55),
    inset 0 -24px 40px rgba(29, 78, 216, 0.45),
    0 0 46px rgba(37, 99, 235, 0.75);
}

.hex-aura {
  filter: blur(18px);
  background: rgba(37, 99, 235, 0.75);
  transform: scale(1.1);
}

.float-slow {
  animation: panel-float 6.4s ease-in-out infinite;
}

.float-delay {
  animation: panel-float 7s ease-in-out infinite;
  animation-delay: -2.1s;
}

@keyframes panel-float {
  0%,
  100% {
    transform: translateY(0) rotateX(0deg);
  }
  50% {
    transform: translateY(-12px) rotateX(2deg);
  }
}

@keyframes hover-pulse {
  0%,
  100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(-14px);
  }
}

@media (max-width: 640px) {
  .hex-wrap {
    width: 118px;
    height: 134px;
    top: 33%;
  }
}
</style>
