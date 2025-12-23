<template>
  <div>
    <a-alert type="info">
      <template #message>
        <div>
          假设本地机器无法做加减乘除运算，需要通过远程请求让服务端来实现。
        </div>
      </template>
    </a-alert>
    <div class="flex"><span>总耗时：</span>{{ duration }} ms</div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

// 以加法为例，现有远程API的模拟实现
const addRemote = async (a: number, b: number): Promise<number> =>
  new Promise((resolve) => {
    setTimeout(() => resolve(a + b), Math.random() > 0.5 ? 1000 : 500);
  });

const inputs = [1, 2, 3, 4, 5, 6];
async function add(nums: number[]): Promise<number> {
  let ret = 0;
  while (nums.length > 1) {
    ret = await addRemote(nums.shift() || 0, nums.shift() || 0);
    nums.push(ret);
  }
  return nums[0] as number;
}

const duration = ref(0);
let start = Date.now();
add(inputs).then(() => {
  duration.value = Date.now() - start;
});
</script>

<style scoped>
.flex {
  display: flex;
  align-items: center;
  margin: 10px 0;
}
</style>
