# GilbreathsConjecture 吉尔布雷斯猜想可视化

https://lhcfl.github.io/GilbreathsConjecture

吉尔布雷斯猜想是一个数论里面看似很简单实则现在也没人证明的猜想：

对于素数列

<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>0</mn></msubsup><mo>=</mo><mn>2</mn><mo>,</mo><mn>3</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>11</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>19</mn><mo>,</mo><mn>23</mn><mo>,</mo><mn>29</mn><mo>,</mo><mn>31</mn><mo>,</mo><mo>&#x22EF;</mo></math>

我们定义：

其 1 阶差为 

<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>1</mn></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mn>0</mn></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mn>0</mn></msubsup><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#x22EF;</mo></math>

其 2 阶差为 

<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mn>2</mn></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mn>1</mn></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mn>1</mn></msubsup><mo>=</mo><mn>1</mn><mo>,</mo><mn>0</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mo>&#x22EF;</mo></math>

以此类推 k 阶差为 

<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mi>n</mi><mi>k</mi></msubsup><mo>=</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi></mrow><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>k</mi><mo>&#x2212;</mo><mn>1</mn></mrow></msubsup><mo>&#x2212;</mo><msubsup><mi>p</mi><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>n</mi><mo>&#x2212;</mo><mn>1</mn></mrow><mrow class=&quot;MJX-TeXAtom-ORD&quot;><mi>k</mi><mo>&#x2212;</mo><mn>1</mn></mrow></msubsup></math>

猜想： 

<math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;><msubsup><mi>p</mi><mn>1</mn><mi>k</mi></msubsup><mo>=</mo><mn>1</mn></math>

即 1 阶及其以后的列，第一项都是 1.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
pnpm install
```

### Compile and Hot-Reload for Development

```sh
pnpm dev
```

### Compile and Minify for Production

```sh
pnpm build
```
