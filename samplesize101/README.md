# スコープ
サンプルサイズの決め方・設計方法を解説する

#### key words
- 統計的検定
- 検出力
- 区間推定

## なぜサンプルサイズ設計が重要なのか
$$
x_i \sim N(\mu, \sigma^2), i = 1, ..., N
$$
のとき帰無仮説を$H_0 : \mu = \mu_0$, 対立仮説を$H_0 : \mu \neq \mu_1$とする。このときの統計検定量は
$$
t_0 = \frac{\bar x - \mu_0}{\sqrt V/n}
$$
ここで$\bar x$は標本平均、$V$は標本分散である。一般的には$|t_0|$が自由度$n-1$のt分布の両側5%点より大きければ「有意差がある」と判定して、「帰無仮説を棄却」し、「対立仮説が成り立っている」と判断する。このとき、

1. nが大きくなるとどんなに差が小さくても有意差ありとなる
2. nが小さすぎると$\mu$と$\mu_0$に実質的な意味のある差があっても、サンプルサイズnが小さいならば$|t_0|$の値が大きくならず有意差が見出せない
3. データをとることにはコストがかかるから、サンプルサイズに制限がかかることが多いが、検出力とのトレードオフである

このうち
```
2. nが小さすぎて有意差が見出せない
```
という状況は特に問題。サンプルサイズが小さくて有意でないだけなのに、帰無仮説が成り立っていると誤解して、「これまで通りの品質（$\mu = \mu_0$）だと判断してコストの安い方に移行したtが、結果的には品質が劣化した」といった誤った判断を引き起こしやすい。