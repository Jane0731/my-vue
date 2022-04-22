<template>
  <div
    class="
      flex
      justify-center
      items-center
      bg-gradient-to-tr
      from-emerald-500
      to-teal-300
      min-h-screen
    "
  >
  <button><HeroiconsOutlineUser class="w-8 h-8 text-blue-500" /></button>
    <div class="bg-white divide-y shadow-lg rounded-lg">
      <div class="p-8">
        <h1
          class="text-emerald-400 text-center text-2xl font-bold tracking-wider"
        >
          BMI計算器
        </h1>
        <div class="mt-6">
          <label class="text-gray-400 inline-block mb-1">身高</label>
          <div
            class="
              flex
              items-center
              px-2
              py-1.5
              border border-emerald-300
              rounded-md
            "
          >
            <input
              type="number"
              class="focus:outline-none mr-1.5 block w-full"
              v-model="height"
            />
            <span class="text-emerald-500 text-sm select-none shrink-0"
              >公分</span
            >
          </div>
        </div>
        <div class="mt-6">
          <label class="text-gray-400 inline-block mb-1">體重</label>
          <div
            class="
              flex
              items-center
              px-2
              py-1.5
              border border-emerald-300
              rounded-md
            "
          >
            <input
              type="number"
              class="focus:outline-none mr-1.5 block w-full"
              v-model="weight"
            />
            <span class="text-emerald-500 text-sm select-none shrink-0"
              >公斤</span
            >
          </div>
        </div>
        <div class="mt-6 text-center">
          <span class="text-gray-400">BMI </span
          ><span class="text-4xl">{{ bmi }}</span>
        </div>
        <div
          v-if="result === '過輕'"
          class="
            mt-6
            py-1.5
            text-center
            bg-amber-200
            text-amber-600 text-lg
            font-bold
            ring-1 ring-amber-500/30
            rounded-sm
            shadow-lg shadow-amber-200
          "
        >
          你的體重是「過輕」
        </div>
        <div
          v-if="result === '正常'"
          class="
            mt-6
            py-1.5
            text-center
            bg-green-200
            text-green-600 text-lg
            font-bold
            ring-1 ring-green-500/30
            rounded-sm
            shadow-lg shadow-green-200
          "
        >
          你的體重是「正常」
        </div>
        <div
          v-if="result === '過重'"
          class="
            mt-6
            py-1.5
            text-center
            bg-amber-200
            text-amber-600 text-lg
            font-bold
            ring-1 ring-amber-500/30
            rounded-sm
            shadow-lg shadow-amber-200
          "
        >
          你的體重是「過重」
        </div>
        <div
          v-if="result === '輕度肥胖'"
          class="
            mt-6
            py-1.5
            text-center
            bg-orange-200
            text-orange-600 text-lg
            font-bold
            ring-1 ring-orange-500/30
            rounded-sm
            shadow-lg shadow-orange-200
          "
        >
          你的體重是「輕度肥胖」
        </div>
        <div
          v-if="result === '中度肥胖'"
          class="
            mt-6
            py-1.5
            text-center
            bg-red-200
            text-red-500 text-lg
            font-bold
            ring-1 ring-red-500/30
            rounded-sm
            shadow-lg shadow-red-200
          "
        >
          你的體重是「中度肥胖」
        </div>
        <div
          v-if="result === '重度肥胖'"
          class="
            mt-6
            py-1.5
            text-center
            bg-red-200
            text-red-600 text-lg
            font-bold
            ring-1 ring-red-500/30
            rounded-sm
            shadow-lg shadow-red-200
          "
        >
          你的體重是「重度肥胖」
        </div>
      </div>
      <div class="p-8">
        <ul class="space-y-2">
          <li class="flex text-amber-400">
            <div class="w-24 font-bold">體重過輕</div>
            <div>BMI &lt; 18.5</div>
          </li>
          <li class="flex text-green-400">
            <div class="w-24 font-bold">正常範圍</div>
            <div>18.5≦BMI&lt;24</div>
          </li>
          <li class="flex text-amber-400">
            <div class="w-24 font-bold">過重</div>
            <div>24≦BMI&lt;27</div>
          </li>
          <li class="flex text-orange-400">
            <div class="w-24 font-bold">輕度肥胖</div>
            <div>27≦BMI&lt;30</div>
          </li>
          <li class="flex text-red-400">
            <div class="w-24 font-bold">中度肥胖</div>
            <div>30≦BMI&lt;35</div>
          </li>
          <li class="flex text-red-500">
            <div class="w-24 font-bold">重度肥胖</div>
            <div>BMI≧35</div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref,computed} from 'vue'

    const height=ref("")
    const weight=ref("")
    const bmi=computed(()=>{
      if (!weight.value || !height.value) {
        return "?";
      } else {
        return (
          weight.value /
          ((height.value / 100) * (height.value / 100))
        ).toFixed(1);
      }
    })
    const result=computed(()=>{
      const bmiValue = Number(bmi.value);
      if (bmiValue < 18.5) {
        return "過輕";
      } else if (bmiValue >= 18.5 && bmiValue < 24) {
        return "正常";
      } else if (bmiValue >= 24 && bmiValue < 27) {
        return "過重";
      } else if (bmiValue >= 27 && bmiValue < 30) {
        return "輕度肥胖";
      } else if (bmiValue >= 30 && bmiValue < 35) {
        return "中度肥胖";
      } else {
        return "重度肥胖";
      }
    })
</script>

