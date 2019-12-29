# Lecture 2: 確率分布の基本的事項

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Lecture 2: 確率分布の基本的事項](#lecture-2-%e7%a2%ba%e7%8e%87%e5%88%86%e5%b8%83%e3%81%ae%e5%9f%ba%e6%9c%ac%e7%9a%84%e4%ba%8b%e9%a0%85)
  - [2-1 : 確率分布と期待値](#2-1--%e7%a2%ba%e7%8e%87%e5%88%86%e5%b8%83%e3%81%a8%e6%9c%9f%e5%be%85%e5%80%a4)
    - [確率密度函数と累積分布函数](#%e7%a2%ba%e7%8e%87%e5%af%86%e5%ba%a6%e5%87%bd%e6%95%b0%e3%81%a8%e7%b4%af%e7%a9%8d%e5%88%86%e5%b8%83%e5%87%bd%e6%95%b0)
      - [確率密度函数<math><semantics><mrow><mi>f</mi><mo stretchy="false">(</mo><mi>x</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">f(x)</annotation></semantics></math>f(x)の定義](#%e7%a2%ba%e7%8e%87%e5%af%86%e5%ba%a6%e5%87%bd%e6%95%b0mathsemanticsmrowmifmimo-stretchy%22false%22momixmimo-stretchy%22false%22momrowannotation-encoding%22applicationx-tex%22fxannotationsemanticsmathfx%e3%81%ae%e5%ae%9a%e7%be%a9)
      - [累積分布函数<math><semantics><mrow><mi>F</mi><mo stretchy="false">(</mo><mi>w</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">F(w)</annotation></semantics></math>F(w)の定義](#%e7%b4%af%e7%a9%8d%e5%88%86%e5%b8%83%e5%87%bd%e6%95%b0mathsemanticsmrowmifmimo-stretchy%22false%22momiwmimo-stretchy%22false%22momrowannotation-encoding%22applicationx-tex%22fwannotationsemanticsmathfw%e3%81%ae%e5%ae%9a%e7%be%a9)
      - [期待値の定義](#%e6%9c%9f%e5%be%85%e5%80%a4%e3%81%ae%e5%ae%9a%e7%be%a9)
      - [期待値の性質](#%e6%9c%9f%e5%be%85%e5%80%a4%e3%81%ae%e6%80%a7%e8%b3%aa)
      - [分散の定義](#%e5%88%86%e6%95%a3%e3%81%ae%e5%ae%9a%e7%be%a9)
      - [分散の性質](#%e5%88%86%e6%95%a3%e3%81%ae%e6%80%a7%e8%b3%aa)
    - [moment generating function](#moment-generating-function)
      - [定義：moment](#%e5%ae%9a%e7%be%a9moment)
      - [Example 1 : Bernoulli random variableとMFG](#example-1--bernoulli-random-variable%e3%81%a8mfg)
      - [Example 2 : Normal districutionと　MFG](#example-2--normal-districution%e3%81%a8-mfg)
      - [Example 3 : Uniform distribution と　MFG](#example-3--uniform-distribution-%e3%81%a8-mfg)
      - [MGFの性質](#mgf%e3%81%ae%e6%80%a7%e8%b3%aa)
    - [同時確率密度函数の定義](#%e5%90%8c%e6%99%82%e7%a2%ba%e7%8e%87%e5%af%86%e5%ba%a6%e5%87%bd%e6%95%b0%e3%81%ae%e5%ae%9a%e7%be%a9)
    - [共分散の定義](#%e5%85%b1%e5%88%86%e6%95%a3%e3%81%ae%e5%ae%9a%e7%be%a9)
    - [相関係数の定義](#%e7%9b%b8%e9%96%a2%e4%bf%82%e6%95%b0%e3%81%ae%e5%ae%9a%e7%be%a9)
    - [共分散の性質](#%e5%85%b1%e5%88%86%e6%95%a3%e3%81%ae%e6%80%a7%e8%b3%aa)
    - [独立性の定義](#%e7%8b%ac%e7%ab%8b%e6%80%a7%e3%81%ae%e5%ae%9a%e7%be%a9)
  - [2-2 : 正規分布](#2-2--%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83)
    - [正規分布の確率密度函数](#%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83%e3%81%ae%e7%a2%ba%e7%8e%87%e5%af%86%e5%ba%a6%e5%87%bd%e6%95%b0)
    - [正規分布の標準化](#%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83%e3%81%ae%e6%a8%99%e6%ba%96%e5%8c%96)
    - [2次元正規分布](#2%e6%ac%a1%e5%85%83%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83)
      - [正規分布の性質](#%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83%e3%81%ae%e6%80%a7%e8%b3%aa)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 2-1 : 確率分布と期待値
### 確率密度函数と累積分布函数
- 確率変数：正しいサイコロを一回投げるとき出る目をxとおくとxには1から6までのどれかの値が出現し、それぞれの起こる確率は1/6。このxように、どのような値になるのか確率が定まっている性質を持つ変数を確率変数という
- 確率分布：確率変数がどのような値になるのかという法則を与えるもの

確率変数は連続型確率変数と離散型確率変数の区別がある

#### 確率密度函数$f(x)$の定義
次の性質を満たす函数$f(x)$を確率密度函数と呼ぶ
$$
f(x)\geq 0, \int^\infty_{-\infty}f(x)dx = 1
$$

このとき
$$
Pr(a\leq x \leq b) = \int^{b}_{a}f(x)dx
$$

#### 累積分布函数$F(w)$の定義
次の性質を満たす函数$F(w)$を確率変数$x$の累積分布函数と呼ぶ
$$
F(w) = Pr(x\leq w) = \int^w_{-\infty}f(x)dx
$$

#### 期待値の定義
$$
E(x) = \infty^{\infty}_{-\infty}f(x)dx
$$
より一般的に、$g(x)$を$x$の函数とするとき
$$
E[g(x)] = \infty^{\infty}_{-\infty}g(x)f(x)dx
$$

#### 期待値の性質
a, b を定数とするとき
$$
\begin{aligned}
& E[ax+b] = aE[x] + b\\
& E[ag(x) + bh(x)] = aE[g(x)] + bE[h(x)]
\end{aligned}
$$

#### 分散の定義
$$
V(x) = E[(x - E[x])^2] = \int^{\infty}_{-\infty}\{x - E[x]\}^2f(x)dx
$$

$V(x)$はxの確率分布のばらつきの大きさを表す。標準偏差は

$$
D(x) = \sqrt{V(x)}
$$

#### 分散の性質
$$
\begin{aligned}
V(x) & = E[x^2] - (E[x])^2\\
V(ax+b) & = a^2V(x)
\end{aligned}
$$
証明は分散の定義より
$$
V(x) = E[(x - E[x])^2] = E[x^2] - 2E[x]E[x] + E[x]^2 = E[x^2] - (E[x])^2
$$
及び
$$
\begin{aligned}
V(ax+b) & = E[(ax + b  - E[ax + b ])^2]\\
& = E[(ax - E[ax])^2]\\
& = E[a^2(x - E[x])^2]\\
& a^2V(x)
\end{aligned}
$$

### moment generating function
$$
M_x(\theta) = E[\exp(\theta x)]
$$

#### 定義：moment
$$
E(x^k) = \int^{\infty}_{-\infty} x^k f(x)dx
$$
をk-th moment of xと呼ぶ。

moment generating functionは以下のようにも表現できる
$$
M_x(t) = E[\exp(xt)] = E\left(\sum_{k = 0}^\infty \frac{x^kt}{k!}\right)
$$
また
$$
\left(\frac{d}{dt}\right)
^kM_x(t)|_{t = 0} = \text{k th moment of x}
$$


#### Example 1 : Bernoulli random variableとMFG
Bernoulli random variableのパラメーターをpとしたとき

$$
M_x(t) = E[\exp(tx)] = \exp(0)(1 - p) + \exp(t\cdot 1)p = \exp(t)p + ( 1 - p)
$$
よって

$$
\text{kth moment} = p\exp(t)|_{t = 0} = p
$$

#### Example 2 : Normal districutionと　MFG
$$
X \sim N(\mu, \sigma^2) 
$$
とするこのとき

$$
\begin{aligned}
M_x(t) = E(\exp(Xt)) & =  \int^{\infty}_{-\infty}\exp(xt) \frac{1}{\sqrt{2\pi \sigma^2}}\exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)dx\\
& = \int^{\infty}_{-\infty}\frac{1}{\sqrt{2\pi \sigma^2}}\exp\left(\frac{(1}{2\sigma^2} (2xt\sigma^2 - (x-\mu)^2)\right)dx\\
& = \int^{\infty}_{-\infty}\frac{1}{\sqrt{2\pi \sigma^2}}\exp\left(-\frac{1}{2\sigma^2} (x- (t\sigma^2 + \mu))^2 + \frac{1}{2\sigma^2} (t^2\sigma^4+ 2t\sigma^2\mu)\right)dx\\
& = \exp\left(\frac{1}{2\sigma^2} (t^2\sigma^4 + 2t\sigma^2\mu)\right)\\
& = \exp(\frac{t^2\sigma^2}{2} + t\mu)
\end{aligned}
$$
最後の式変形は
$$
\int^{\infty}_{-\infty}\frac{1}{\sqrt{2\pi \sigma^2}}\exp\left(-\frac{1}{2\sigma^2} (x- (t\sigma^2 + \mu))^2\right)dx = 1
$$
でこの式は $x\sim N(t\sigma^2 + \mu, \sigma^2)$ より明らか。

#### Example 3 : Uniform distribution と　MFG
$$
X\sim Unif(0, 1)
$$
このとき
$$
M_x(t) = E[\exp(tx)] = \int^1_0\exp(tx)dx = \exp(t)\left(1 - \frac{1}{t}\right)
$$
k-th momentの計算にはロピタルの定理を用いて計算する。

#### MGFの性質
モーメント母関数と確率分布は1対1に対応する。

### 同時確率密度函数の定義
次の性質を満たす函数$f(x, y)$を同時確率密度函数と呼ぶ
$$
f(x, y) \geq 0, \int^{\infty}_{-\infty}\int^{\infty}_{-\infty} f(x, y)dxdy = 1
$$

xの周辺確率密度函数は
$$
f_X(x) = \int^{\infty}_{-\infty} f(x, y)dy
$$

また
$$
\begin{aligned}
E[ax + by] & = \int^{\infty}_{-\infty}\int^{\infty}_{-\infty}(ax + by)f(x, y)dxdy\\
& = \int^{\infty}_{-\infty}\int^{\infty}_{-\infty} ax f(x, y)dxdy + \int^{\infty}_{-\infty}\int^{\infty}_{-\infty}by f(x,y)dxdy\\
& = \int^{\infty}_{-\infty}ax f_X(x)dx + \int^{\infty}_{-\infty}by f_Y(y)dy\\
& = aE[x] + bE[y]
\end{aligned}
$$

### 共分散の定義
$$
Cov(x, y) = E[(x - E(x))(y - E(y))]
$$

### 相関係数の定義
$$
\rho_{xy} = \frac{Cov(x, y)}{\sqrt{V(x)}\sqrt{V(y)}}
$$


### 共分散の性質
$$
Cov(x, y) = E[xy] - E[x]E[y]
$$

$$
V(ax + by) = a^2V(x) + b^2 V(y) + 2abCov(x, y)
$$

### 独立性の定義
同時確率密度函数$f(x, y)$と周辺確率密度函数$f_x(x), f_y(y)$の間に、全てのx, yに対して

$$
f(x, y) = f(x)f(y)
$$

が成り立つとき、x, yは互いに独立であるという

## 2-2 : 正規分布
### 正規分布の確率密度函数
$$
X \sim N(\mu, \sigma^2)
$$

$$
f(x) = \frac{1}{sqrt{2\pi\sigma^2}}\exp\left\{-\frac{(x - \mu)^2}{2\sigma^2}\right\}
$$
コードで正規分布の特徴について確認する（別ファイル）。

### 正規分布の標準化
$$
X \sim N(\mu, \sigma^2)
$$
を次のように変換することを標準化（standardization）と呼ぶ。

$$
X \sim N(\mu, \sigma^2) \Rightarrow z = \frac{x- \mu}{\sigma} \sim N(0, 1)
$$

### 2次元正規分布
２次元正規分布の同時確率密度函数
$$
f(x, y) = \frac{1}{s\pi \sqrt{1 - \rho^2_{xy}\sigma_x\sigma_y}}\exp\left(-\frac{1}{2}D^2\right)
$$
ここで
$$
D^2 = \frac{1}{1- \rho^2_{xy}}\left\{\frac{(x - \mu_x)^2}{\sigma^2_x} - 2\rho_{xy}\frac{(x - \mu_x)(y - \mu_y)}{\sigma_x\sigma_y} + \frac{(y - \mu_y)^2}{\sigma^2_y} \right\}
$$

#### 正規分布の性質
$$
X \sim N(\mu, \sigma^2)
$$
でa, bが定数のとき
$$
ax + b \sim N(a\mu+ b , a^2\sigma)
$$
である。証明は以下、

$$
\begin{aligned}
M(t) = E[\exp(t(ax+b))] & = E[\exp(t(ax))\exp(tb)]\\
& = \exp(tb) E[\exp(t(ax))\\
& = \exp(tb)\exp\left(a\mu t + \frac{a^2\sigma^2t^2}{2}\right)\\
& = \exp\left((a\mu + b)t + \frac{(a\sigma)^2t^2}{2}\right)
\end{aligned}
$$
これは$N(a\mu + b, a^2\sigma^2)$のMGF。