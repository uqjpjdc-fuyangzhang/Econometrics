# Lecture 3 : 1つの母平均の検定 - 母分散が既知の場合

このノートでは、母分散が既知の場合の母平均の検定について検出力の計算方法とサンプルサイズの設計方法を説明する。ただし、このケースは現実では基本的にはありえない。

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [3-1 : 検定手順](#3-1--%E6%A4%9C%E5%AE%9A%E6%89%8B%E9%A0%86)
  - [母平均$\mu$に関する検定手順（母分散既知）](#%E6%AF%8D%E5%B9%B3%E5%9D%87%5Cmu%E3%81%AB%E9%96%A2%E3%81%99%E3%82%8B%E6%A4%9C%E5%AE%9A%E6%89%8B%E9%A0%86%E6%AF%8D%E5%88%86%E6%95%A3%E6%97%A2%E7%9F%A5)
  - [対立仮説を $H_1 : \mu \neq \mu_0$ と設定する場合の有意水準と検出力](#%E5%AF%BE%E7%AB%8B%E4%BB%AE%E8%AA%AC%E3%82%92-h_1--%5Cmu-%5Cneq-%5Cmu_0-%E3%81%A8%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88%E3%81%AE%E6%9C%89%E6%84%8F%E6%B0%B4%E6%BA%96%E3%81%A8%E6%A4%9C%E5%87%BA%E5%8A%9B)
    - [Effect Sizeの例](#effect-size%E3%81%AE%E4%BE%8B)
  - [Effect sizeの値の設定の考え方](#effect-size%E3%81%AE%E5%80%A4%E3%81%AE%E8%A8%AD%E5%AE%9A%E3%81%AE%E8%80%83%E3%81%88%E6%96%B9)
    - [考え方１：一方の母集団の100P%が他方の母集団の100P% より大きくなれば$H_0$を棄却する](#%E8%80%83%E3%81%88%E6%96%B9%EF%BC%91%E4%B8%80%E6%96%B9%E3%81%AE%E6%AF%8D%E9%9B%86%E5%9B%A3%E3%81%AE100p%25%E3%81%8C%E4%BB%96%E6%96%B9%E3%81%AE%E6%AF%8D%E9%9B%86%E5%9B%A3%E3%81%AE100p%25-%E3%82%88%E3%82%8A%E5%A4%A7%E3%81%8D%E3%81%8F%E3%81%AA%E3%82%8C%E3%81%B0h_0%E3%82%92%E6%A3%84%E5%8D%B4%E3%81%99%E3%82%8B)
    - [考え方2 : 一方の母集団の50%が他方の母集団の100P%より大きくなれば$H_0$を棄却する](#%E8%80%83%E3%81%88%E6%96%B92--%E4%B8%80%E6%96%B9%E3%81%AE%E6%AF%8D%E9%9B%86%E5%9B%A3%E3%81%AE50%25%E3%81%8C%E4%BB%96%E6%96%B9%E3%81%AE%E6%AF%8D%E9%9B%86%E5%9B%A3%E3%81%AE100p%25%E3%82%88%E3%82%8A%E5%A4%A7%E3%81%8D%E3%81%8F%E3%81%AA%E3%82%8C%E3%81%B0h_0%E3%82%92%E6%A3%84%E5%8D%B4%E3%81%99%E3%82%8B)
  - [サンプルサイズの設計方法](#%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E3%82%B5%E3%82%A4%E3%82%BA%E3%81%AE%E8%A8%AD%E8%A8%88%E6%96%B9%E6%B3%95)
    - [対立仮説を$H_1 ; \mu \neq \mu_0$と設定する場合](#%E5%AF%BE%E7%AB%8B%E4%BB%AE%E8%AA%AC%E3%82%92h_1--%5Cmu-%5Cneq-%5Cmu_0%E3%81%A8%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88)
  - [対立仮説を$H_1 : \mu > \mu_0$と設定する場合](#%E5%AF%BE%E7%AB%8B%E4%BB%AE%E8%AA%AC%E3%82%92h_1--%5Cmu--%5Cmu_0%E3%81%A8%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88)
  - [対立仮説を$H_1 : \mu < \mu_0$と設定する場合](#%E5%AF%BE%E7%AB%8B%E4%BB%AE%E8%AA%AC%E3%82%92h_1--%5Cmu--%5Cmu_0%E3%81%A8%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 3-1 : 検定手順
$x_1, x_2, ..., x_n$が互いに独立に正規分布 $N(\mu, \sigma_0^2)$ にしたがっているとする。このとき、$\sigma^2_0$は既知とする。

### 母平均$\mu$に関する検定手順（母分散既知）

1. 仮説の設定
   - 帰無仮説 $H_0 : \mu = \mu_0$
   - 対立仮説 $H_1$ の設定
2. 有意水準$\alpha$の設定（通常は$\alpha = 0.05$）
3. 棄却域$R$の設定
   - 例： $R : |u_0| \geq z_{\alpha/2}$
4. データ $x_1, ..., x_n$をとり、検定統計量$u_0$の値を計算する
   $$
   u_0 = \frac{\bar x - \mu_0}{\sqrt {\sigma_0^2 / n}}
   $$
5. $u_0$が棄却域$R$にあれば優位と判定し、$H_0$を棄却する

### 対立仮説を $H_1 : \mu \neq \mu_0$ と設定する場合の有意水準と検出力

$$
\alpha = Pr(|u_0| \geq z_{\alpha/2}) = Pr(u_0 \leq - z_{\alpha/2}) + Pr(u_0 \geq z_{\alpha/2})
$$

次に、検出力 $1 - \beta$を求める

$$
\begin{aligned}
1 - \beta & = Pr(|u_0 \geq z_{\alpha/2}|)\\
& = Pr\left(\frac{\bar x - \mu_0}{\sqrt{\sigma_0^2/n}} \leq - z{\alpha/2} \right) + Pr\left(\frac{\bar x - \mu_0}{\sqrt{\sigma_0^2/n}} \geq z{\alpha/2} \right)\\
& = Pr\left(\frac{\bar x - \mu}{\sqrt{\sigma_0^2/n}} + \frac{\mu - \mu_0}{\sqrt{\sigma_0^2/n}} \leq - z{\alpha/2} \right) + Pr\left(\frac{\bar x - \mu}{\sqrt{\sigma_0^2/n}} + \frac{\mu - \mu_0}{\sqrt{\sigma_0^2/n}} \geq  z{\alpha/2} \right)\\
& = Pr(u \leq - z_{\alpha/2} - \sqrt{n}\Delta) + Pr(u \geq -z_{\alpha/2} - \sqrt{n}\Delta)
\end{aligned}
$$

ここで
$$
\Delta = \frac{\mu - \mu_0}{\sigma_0}
$$

この$\Delta$はeffect sizeと呼ぶ場合もある。

#### Effect Sizeの例
- Glass’s $\Delta$
- Cohen’s d
- Hedges’s g and $g^∗$
- Root mean square standardized effect (RMSSE)

### Effect sizeの値の設定の考え方

母集団0 $N(\mu_0, \sigma_0^2)$ と母集団1 $N(\mu, \sigma^2_0)$を考える。

#### 考え方１：一方の母集団の100P%が他方の母集団の100P% より大きくなれば$H_0$を棄却する
P = 0.8の場合を考える。


<img src  = "https://github.com/RyoNakagami/omorikaizuka/blob/master/Econometrics/fig3_1.jpg?raw=true">

2つの確率密度関数の交わっている横軸の値をmとおくと$m = (\mu_0 + \mu)/2$。$x \sim N(\mu, \sigma^2_0)$とすると

$$
0.80 = Pr(x \geq m) = Pr\left(\frac{x - \mu}{\sigma_0}\geq \frac{m - \mu}{\sigma_0}\right) = r\left(u geq \frac{m - \mu}{\sigma_0}\right) 
$$
これより

$$
z_{0.20} = - 0.842 = \frac{m - \mu}{\sigma_0} = \frac{(\mu_0 + \mu)/2 - \mu}{\sigma_0} = \frac{\mu_0 - \mu}{2\sigma_0} = - \frac{\Delta}{2}
$$

したがって$\Delta = 1.684$と設定する。

#### 考え方2 : 一方の母集団の50%が他方の母集団の100P%より大きくなれば$H_0$を棄却する
P = 0.9の場合を考える。

$$
0.90 = Pr(x_0 \leq \mu) = Pr\left(\frac{x_0 - \mu_0}{\sigma_0} \leq \frac{\mu - \mu_0}{\sigma_0}\right) = Pr(u \leq \Delta)
$$

### サンプルサイズの設計方法
#### 対立仮説を$H_1 ; \mu \neq \mu_0$と設定する場合

$\delta = (\mu - \mu_0)/\sigma_0$について、$|\Delta| \geq \Delta_0(>0)$のとき、検出力$1 - \beta$で$H_0$を棄却したいと考える。

$$
1 - \beta = Pr(u \leq - z_{\alpha/2} - \sqrt n \Delta) + Pr(u \geq z_{\alpha/2} - \sqrt n \Delta)
$$
問題の単純化のため$\Delta > 0$とする。第１項は$\sqrt n \Delta$が非常に小さい場合以外は無視できるから

$$
1 - \beta \approx Pr(u \geq z_{\alpha/2} - \sqrt n \Delta)
$$

$$
z_{\alpha/2} - \sqrt n \Delta_0 \approx z_{1 - \beta}
$$

これからサンプルサイズ n を求める次式を得る

$$
n \approx \left(\frac{z_{\alpha/2} - z_{1-\beta}}{\Delta_0}\right)^2
$$

### 対立仮説を$H_1 : \mu > \mu_0$と設定する場合
$$
n = \left(\frac{z_{\alpha} - z_{1-\beta}}{\Delta_0}\right)^2
$$

### 対立仮説を$H_1 : \mu < \mu_0$と設定する場合
$$
n = \left(\frac{-z_{1-\alpha} + z_{\beta}}{\Delta_0}\right)^2 = \left(\frac{z_{\alpha} - z_{1-\beta}}{\Delta_0}\right)^2
$$
