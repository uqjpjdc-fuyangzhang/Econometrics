# Lecture 2 : 正規分布と分布のズレの評価
#### Keywords
- normal distribution
- Kolmogorov-Smirnov test

#### 参考
- [Enginnering statistics handbook](https://www.itl.nist.gov/div898/handbook/eda/section3/eda35g.htm)


<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Lecture 2 : 正規分布と分布のズレの評価](#lecture-2--%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83%e3%81%a8%e5%88%86%e5%b8%83%e3%81%ae%e3%82%ba%e3%83%ac%e3%81%ae%e8%a9%95%e4%be%a1)
      - [Keywords](#keywords)
      - [参考](#%e5%8f%82%e8%80%83)
  - [2-3 : 2次元正規分布の同時確率密度関数](#2-3--2%e6%ac%a1%e5%85%83%e6%ad%a3%e8%a6%8f%e5%88%86%e5%b8%83%e3%81%ae%e5%90%8c%e6%99%82%e7%a2%ba%e7%8e%87%e5%af%86%e5%ba%a6%e9%96%a2%e6%95%b0)
  - [2- 4 : Kolmogorov-Smirnov test and Lilliefors test](#2--4--kolmogorov-smirnov-test-and-lilliefors-test)
      - [Notation](#notation)
      - [Theorem 1](#theorem-1)
        - [Proof](#proof)
      - [CLT](#clt)
      - [Theorem 2](#theorem-2)
    - [KS test](#ks-test)
    - [KS test for two samples](#ks-test-for-two-samples)
      - [KS testのメリットとデメリット](#ks-test%e3%81%ae%e3%83%a1%e3%83%aa%e3%83%83%e3%83%88%e3%81%a8%e3%83%87%e3%83%a1%e3%83%aa%e3%83%83%e3%83%88)
      - [KS Testのロジック](#ks-test%e3%81%ae%e3%83%ad%e3%82%b8%e3%83%83%e3%82%af)
        - [Definition	The Kolmogorov-Smirnov test](#definition-the-kolmogorov-smirnov-test)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 2-3 : 2次元正規分布の同時確率密度関数
$$
\begin{aligned}
f(x, y) & = \frac{1}{2\pi \sqrt{1 - \rho^2_{xy}}\sigma_x\sigma_y}\exp\left(-\frac{1}{2}D^2\right)\\
D^2 & = \frac{1}{1 - \rho^2_{xy}}\left\{\frac{(x - \mu_x)^2}{\sigma_x^2} - 2\rho_{xy}\frac{(x - \mu_x)(y-\mu_y)}{\sigma_x\sigma_y} + \frac{(y - \mu_y)^2}{\sigma_y^2}\right\}
\end{aligned}
$$

この同時確率密度関数を用いてcovarianceを求める

まず$D^2$の変形
$$
\begin{aligned}
(1 - \rho^2_{xy})D^2 = \left[\frac{( y - \mu_y)}{\sigma_y} = \rho_{xy} \frac{( x - \mu_x)}{\sigma_x}\right]^2 + (1 - \rho^2_{xy})\frac{( x - \mu_x)^2}{\sigma^2_x}
\end{aligned}
$$
Then, 
$$
\begin{aligned}
E(xy) & = \int\int xy f(x, y)dxdy\\
& = \int x\frac{1}{\sqrt{2\pi}\sigma_x}\exp\left(-\frac{(x - \mu_x)^2}{2\sigma^2_x}\right)\int y \frac{1}{\sqrt{2\pi}\sigma_y\sqrt{1 - \rho_{xy}^2}}\exp\left(-\frac{1}{2(1 - \rho^2_{xy})\sigma^2_y}\left(y - \mu_y - \rho_{xy}\frac{\sigma_y}{\sigma_x}(x - \mu_x)\right)^2\right)dydx\\
& = \int x \left(\mu_y +  \rho_{xy}\frac{\sigma_y}{\sigma_x}(x - \mu_x)\right)\frac{1}{\sqrt{2\pi}\sigma_x}\exp\left(-\frac{(x - \mu_x)^2}{2\sigma^2_x}\right)dx\\
& = \mu_x\mu_y + \rho_{xy}\sigma_x\sigma_y
\end{aligned}
$$

## 2- 4 : Kolmogorov-Smirnov test and Lilliefors test
未知の分布 $\mathbf  P$ に従う i.i.d sample $X_1, ..., X_n$を考える。ここで分布$\mathbf P$が$\mathbf P_0$に従うかどうかの検定を行いたいとする

$$
H_0 : \mathbf P = \mathbf P_0, \  \  H_1 : \mathbf P \neq \mathbf P_0
$$

#### Notation
- $F(x) = Pr (X_i \leq x)$ : true c.d.f
- $F_n(x) =  Pr_n (X_i \leq x) = \frac{1}{n}\sum_i^NI(X_i\leq x)$ : empirical c.d.f

任意の$x\in R$について、law of large numbersより

$$
F_n(x) = \frac{1}{n}\sum I(X_i \leq x)\to \mathbf E I(X_i\leq x) = \mathbf P(X_i \leq x) = F(x)
$$

#### Theorem 1
If $F(x)$ is continuous then the distribution

$$
\sup_{x\in R} |F_n(x) - F(x)|
$$

does not depend on $F$.

##### Proof
$F$の逆関数を以下のように定義する

$$
F^{-1}(y) = \min\{x: F(x)\geq y \}
$$

これを用いて

$$
Pr(\sup_{x\in R} |F_n(x) - F(x)|\leq t) = Pr(\sup_{0\leq y \leq 1} |F_n(F^{-1}(y)) - y|\leq t)
$$

empirical c.d.f $F_n$の定義より

$$
F_n(F^{-1}(y))  = \frac{1}{n}\sum I(X_i\leq F^{-1}(y)) = \frac{1}{n}\sum I(F(X_i)\leq y)
$$

<img src = "https://github.com/RyoNakagami/omorikaizuka/blob/master/Econometrics/ks_test.jpg?raw=true">

よって
$$
Pr(\sup_{0\leq y \leq 1} |F_n(F^{-1}(y)) - y|\leq t) = Pr\left(\sup_{0\leq y \le 1}\left|\frac{1}{n}\sum I(F(X_i)\leq y) - y\right| \right)
$$

また$F(X_i)$の分布は $[0, 1]$ 区間で一様分布である、なぜならば

$$
Pr(F(X_i) \leq t) = Pr(X_i \leq F^{-1}(t)) = F(F^{-1}(t)) = t
$$

よって、確率変数

$$
U_i = F(X_i) \  \ \text{ for } i \in \{1, ..., N \}
$$
はindependent and uniform distribution on $[0, 1]$. Then,

$$
Pr(\sup_{x\in R} |F_n(x) - F(x)|\leq t) = Pr\left(\sup_{0\leq y \le 1}\left|\frac{1}{n}\sum I(U_i\leq y) - y\right| \leq t\right)
$$
よってFと独立であることが確かめられた。

#### CLT
$$
\sqrt{n} (F_n(x) - F(x)) \xrightarrow d N(0, F(x)(1 - F(x)))
$$

#### Theorem 2
$$
Pr(\sqrt{n} \sup_{x\in R} |F_n(x) - F(x)|\leq t) \to H(t) = 1 - 2 \sum_{i = 1}^{\infty}(-1)^{i-1}\exp(-2i^2t)
$$
where $H(t)$ is the c.d.f of Kolmogorov-Smirnov distribution

証明は難しいので省略。

### KS test
$$
H_0 : \mathbf P = \mathbf P_0, \  \  H_1 : \mathbf P \neq \mathbf P_0
$$
を書き換えると

$$
H_0 : F = F_0, \  \  H_1 : F \neq F_0
$$

このときの統計量を

$$
D_n = \sqrt{n} \sup_{x\in R} |F_n(x) - F(x)|
$$ 

このとき$D_n$はKS分布に収束する。critical value, $\delta$,の表現は

$$
\sup_x |F_n(x) - F_0(x)| > \delta
$$

これを$\sqrt n$倍すると

$$
D_n > \sqrt n \delta
$$

仮に $H_0$ がfailであった場合、$D_n \to \infty$. よってdecision ruleは

$$
\text{ decision rule } = \begin{cases}
H_0 : D_n \leq c\\
H_1 : D_n > c 
\end{cases}
$$

significance level, $\alpha$, との関係は以下のように表せられる

$$
\alpha = Pr(D_n > c | H_0)
$$

### KS test for two samples
$X \sim F$ and $Y \sim G$と考える。このときそれぞれからsize m と n のsample を取得する。

- $x_i \xrightarrow d F, \sharp (x) = m$
- $y_i \xrightarrow d G, \sharp(x) = n$

仮説設定は
$$
H_0 : F = G \  \ \text{ vs } \  \ H_1 : F \neq G
$$

$F_m(x), G_n(y)$ をそれぞれの empirical c.d.fとする。

$$
D_{mn} = \left(\frac{mn}{m+n}\right)^{1/2} \sup_x |F_m(x) - G_n(x)|
$$

このとき, $D_{mn} > c : 1 - H(c) = \alpha$ ならば仮説を棄却する。

#### KS testのメリットとデメリット

- メリット： 分布に依存しない, exact test
- デメリット: 連続分布にしか使えない（拡張は存在する）, tailと比べて分布の中心でよりsensitive, 分布をfully specifiedしなくてはならない（推定ではダメ）

 Anderson-Darling test 、the Cramer Von-Mises testを用いた方が良いとされる。

#### KS Testのロジック
The Kolmogorov-Smirnov test は empirical c.d.fに基づいているので, data points $x_1, ..., x_N$に対して

$$
ecdf(c) = \frac{\text{ the number of obs where } x_i \leq c}{\text{the number of observations}}
$$

これは $1/N$ ずつ上昇する step function。

##### Definition	The Kolmogorov-Smirnov test

- $H_0$ : dataは検定したい分布に従う
- $H_1$ : dataは検定したい分布に従わない
- significance level: $\alpha$
- Test Statistic:

$$
D = \max_i \left(F(x_i) - \frac{i-1}{N}, \frac{i}{N} - F(x_i) \right)
$$

where F はパラメーターをfully specifiedされた検定したいcumulative distribution、連続分布

Dからわかるようにupper boundは$i/N$. 

実装は難しいので別の機会に。。。
