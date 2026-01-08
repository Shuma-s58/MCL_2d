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
$b_t(x) = p_t(x|x_t, u_{1:t}, z_{1:t}) = p_t(x | x_0, u_0, u_1, ..., u_t, z_0, z_1, z_2, ..., z_t)$

* 尤度関数
$$
L_j(x|z) = \eta p_j(z|x) = \mathcal{N}[z = z_j|h_j(x), Q_j(x)]
$$

$$
Q_j(x) = \begin{pmatrix} l_j(x)\sigma_l & 0 \\ 0 & \sigma_\phi^2 \end{pmatrix}
$$



* 雑音の大きさ
$\delta_{ab} \sim \mathcal{N}(0, \sigma_{ab}^2)$

* 雑音を加えた制御指令値 $v'$

$$
u' = \begin{pmatrix} v' \\ \omega' \end{pmatrix}^T 
  = \begin{pmatrix} v \\ \omega \end{pmatrix}^T +
    \begin{pmatrix} \delta_{vv} \sqrt{|v| / \Delta t} + \delta_{v \omega} \sqrt{|\omega| / \Delta t} \\ 
                    \delta_{\omega v} \sqrt{|v| / \Delta t} + \delta_{\omega \omega} \sqrt{|\omega| / \Delta t} \end{pmatrix}
$$



## Notation

| Notation | Code Representation | Description    |
|----------|---------------------|----------------|
|$x$      |                      |ロボットの姿勢  |
|$u$      |                      |制御指令値      |
|$z$      |                      |センサ値のリスト|
|---------|----------------------|----------------|
|$\sigma_{ab}$|                  |bがaに与えるばらつきの標準偏差|
|$\sigma_{vv}$|                  |直進1[m]で生じる道のりのばらつきの標準偏差|
|$\sigma_{v\omega}$|                  |回転1[rad]で生じる道のりのばらつきの標準偏差|
|$\sigma_{\omega v}$|                  |直進1[m]で生じる回転のばらつきの標準偏差|
|$\sigma_{v\omega}$|                  |回転1[rad]で生じる回転のばらつきの標準偏差|



## Reference
-   『詳解 確率ロボティクス ― Pythonによる基礎アルゴリズムの実装 ―』著者:上田隆一　講談社〈KS理工学専門書〉、2019年、ISBN 978-406-51-7006-9
