# MCL_2d
パーティクルフィルタを用いたモンテカルロ自己位置推定(MCL:Monte Carlo Localization)を実装したパッケージ
『詳解 確率ロボティクス ― Pythonによる基礎アルゴリズムの実装 ―』の第5章 パーティクルフィルタによる自己位置推定を参考に実装を行っている.


![demo](https://github.com/Shuma-s58/MCL_2d/blob/main/movies/no_sampling.gif)
![demo](https://github.com/Shuma-s58/MCL_2d/blob/main/movies/simple_sampling.gif)
![demo](https://github.com/Shuma-s58/MCL_2d/blob/main/movies/systematic_sampling.gif)

## expression
$\alpha$

## function
* 信念分布 $b_t$  
$$
b_t(x) = p_t(x|x_t, u_{1:t}, z_{1:t}) = p_t(x | x_0, u_0, u_1, ..., u_t, z_0, z_1, z_2, ..., z_t)
$$

* 尤度関数 $L_j$

$$
L_j(x|z) = \eta p_j(z|x) = \mathcal{N}[z = z_j|h_j(x), Q_j(x)]
$$

$$
Q_{j(x)} = \begin{pmatrix} \ell_{j(x)}\sigma_{\ell} & 0 \\
                          0 & \sigma_{\varphi}^2 \end{pmatrix}
$$



* 雑音の大きさ
$$
\delta_{ab} \sim \mathcal{N}(0, \sigma_{ab}^2)
$$

* 雑音を加えた制御指令値 $u'$

$$
u' = \begin{pmatrix} v' \\ \omega' \end{pmatrix}^T 
  = \begin{pmatrix} v \\ \omega \end{pmatrix}^T +
    \begin{pmatrix} \delta_{vv} \sqrt{|v| / \Delta t} + \delta_{v \omega} \sqrt{|\omega| / \Delta t} \\ 
                    \delta_{\omega v} \sqrt{|v| / \Delta t} + \delta_{\omega \omega} \sqrt{|\omega| / \Delta t} \end{pmatrix}
$$

* 各パーティクルの姿勢 $x_t^{(i)}$ における信念分布の密度 $b_t(x_t^{(i)})$  

$$
b_t(x_t^{(i)}) = \hat{b}_t(x_t^{(i)}| z_{j,t}) = \eta p_j(z_{j,t}|x_t^{(i)}) \hat{b}_t(x_t^{(i)}) = \eta' L_j \hat{b}_t(x_t^{(i)}| z_{j,t}) \hat{b}_t(x_t^{(i)})
$$

## Notation

| Notation | Description    |
|----------|----------------|
|$x$      |ロボットの姿勢  |
|$u$      |制御指令値      |
|$z$      |センサ値のリスト|
|$m$      |ランドマーク    |
|---------|----------------|
|$\sigma_{ab}$|bがaに与えるばらつきの標準偏差|
|$\sigma_{vv}$|直進1[m]で生じる道のりのばらつきの標準偏差|
|$\sigma_{v\omega}$|回転1[rad]で生じる道のりのばらつきの標準偏差|
|$\sigma_{\omega v}$|直進1[m]で生じる回転のばらつきの標準偏差|
|$\sigma_{v\omega}$|回転1[rad]で生じる回転のばらつきの標準偏差|
|$\sigma_{\ell}$||
|$\sigma_{\varphi}$||



## Reference
-   『詳解 確率ロボティクス ― Pythonによる基礎アルゴリズムの実装 ―』著者:上田隆一　講談社〈KS理工学専門書〉、2019年、ISBN 978-406-51-7006-9
