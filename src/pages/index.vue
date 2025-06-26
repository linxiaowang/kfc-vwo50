<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'IndexPage',
})

const pictures = ref<Array<string>>([
  '/kfc1.jpg',
  '/kfc2.jpg',
  '/kfc3.jpg',
  '/kfc4.jpg',
  '/kfc5.jpg',
])

const pictureIndex = ref<number>(1)

const pictrue = computed<string>(() => {
  return pictures.value[pictureIndex.value]
})

const router = useRouter()
const noButtonSize = ref(120)
const okButtonSize = ref(120)

function handleOkClick() {
  router.push('/success')
}

function handleNoClick() {
  pictureIndex.value = pictureIndex.value > 4 ? 1 : pictureIndex.value + 1
  noButtonSize.value = Math.max(60, noButtonSize.value - 20)
  okButtonSize.value = Math.min(200, okButtonSize.value + 20)
}
</script>

<template>
  <div flex flex-col items-center>
    <img :src="pictrue" alt="" h-128 w-128>
    <div mb-1 mt-1>
      可以请我吃kfc吗
    </div>
    <div mt-4 flex gap-4 items-center>
      <button
        class="ok-button"
        :style="{ width: `${okButtonSize}px`, height: `${okButtonSize * 0.4}px` }"
        @click="handleOkClick"
      >
        请你请你
      </button>
      <button
        class="no-button"
        cursor-pointer
        :style="{ width: `${noButtonSize}px`, height: `${noButtonSize * 0.4}px` }"
        @click="handleNoClick"
      >
        就不
      </button>
    </div>
  </div>
</template>

<style scoped>
.ok-button,
.no-button {
  border: none;
  color: white;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  transition: all 0.2s ease;
  font-size: 16px;
  border-radius: 25px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  font-weight: bold;
  letter-spacing: 1px;
  position: relative;
  overflow: hidden;
}

.ok-button {
  background: linear-gradient(145deg, #4caf50, #45a049);
}

.no-button {
  background: linear-gradient(145deg, #f44336, #e53935);
}

.ok-button:hover,
.no-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

.ok-button:active,
.no-button:active {
  transform: translateY(1px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.ok-button::before,
.no-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(120deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: 0.5s;
}

.ok-button:hover::before,
.no-button:hover::before {
  left: 100%;
}
</style>
