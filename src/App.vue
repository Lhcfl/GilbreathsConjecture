<template>
  <h1 class="m-2 text-4xl">Gilbreath's Conjecture 吉尔布雷斯猜想</h1>
  <p class="m-2">block size: 
    <input type="number" max="20" min="1" v-model.number="BLOCK_SIZE">
    （可调整）
  </p>
  <p class="m-2">
    下面的方块，位置在 (i, j) 代表素数列的 j 阶差的第 i 项。如果是红色，代表它是 1，绿色代表是 0，蓝色代表是 2，灰色代表其他数字。
    <br />
    吉尔布雷斯猜想是一个数论里面看似很简单实则现在也没人证明的猜想：<br />
    对于素数列
    <math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>0</mn></msubsup><mo>=</mo><mn>2</mn><mo>,</mo><mn>3</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>11</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>19</mn><mo>,</mo><mn>23</mn><mo>,</mo><mn>29</mn><mo>,</mo><mn>31</mn><mo>,</mo><mo>&#x22EF;</mo></math>
    <br />我们定义：
    其 1 阶差为 
    <math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>1</mn></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mn>0</mn></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mn>0</mn></msubsup><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#x22EF;</mo></math>
    <br />其 2 阶差为 
    <math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>2</mn></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mn>1</mn></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mn>1</mn></msubsup><mo>=</mo><mn>1</mn><mo>,</mo><mn>0</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mo>&#x22EF;</mo></math>
    <br />以此类推 k 阶差为 
    <math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mi>k</mi></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>k</mi><mo>&#x2212;</mo><mn>1</mn></mrow></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>k</mi><mo>&#x2212;</mo><mn>1</mn></mrow></msubsup></math>
    <br />猜想： 
    <math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mn>1</mn><mi>k</mi></msubsup><mo>=</mo><mn>1</mn></math>
    即 1 阶及其以后的列，第一项都是 1.
    <br />
    <a class="text-blue-600" href="https://zhuanlan.zhihu.com/p/719148875">https://zhuanlan.zhihu.com/p/719148875</a>
  </p>
  <main>
    <canvas ref="canvas" style="width: 100vw; height: 100%" width="1920" height="1080" />
  </main>
</template>

<script setup>
import { useTemplateRef, onMounted, ref, watch } from "vue";
const canvas = useTemplateRef("canvas");
const BLOCK_SIZE = ref(3);

function get_primes(n) {
  let isnt_prime = new Int8Array(n + 1);
  let res = [];
  for (let i = 1; i <= n; i++) {
    if (i < 2 || isnt_prime[i]) continue;
    for (let k = i * 2; k <= n; k += i) isnt_prime[k] = 1;
    res.push(i);
  }
  return res;
}

function draw_line(lineno, arr) {
  const ctx = canvas.value.getContext("2d");
  let id = 0;
  for (const i of arr) {
    ctx.fillStyle =
      i == 1 ? "red" : i == 2 ? "blue" : i == 0 ? "green" : "gray";
    ctx.fillRect(id * BLOCK_SIZE.value, lineno * BLOCK_SIZE.value, BLOCK_SIZE.value, BLOCK_SIZE.value);
    id++;
  }
}

function draw_image() {
  let arr = get_primes(30000);
  let lineno = 0;
  while (arr.length > 1) {
    draw_line(lineno, arr);
    let next_arr = [];
    for (let i = 0; i < arr.length - 1; i++) {
      next_arr.push(Math.abs(arr[i + 1] - arr[i]));
    }
    arr = next_arr;
    lineno++;
  }
}

watch(BLOCK_SIZE, () => {
  draw_image();
});

onMounted(() => {
  draw_image();
});
</script>
