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

## Notation

| Notation | Code Representation | Description    |
|----------|---------------------|----------------|
|$x$      |                      |ロボットの姿勢  |
|$u$      |                      |制御指令値      |
|$z$      |                      |センサ値のリスト|
|---------|----------------------|----------------|
|$\sigma_{ab}$|                  |                |
|$\sigma_{vv}$|                  |                |
|$\sigma_{v\omega}$|                  |                |
|$\sigma_{\omegav}$|                  |                |
|$\sigma_{v\omega}$|                  |                |


## Reference
-   『詳解 確率ロボティクス ― Pythonによる基礎アルゴリズムの実装 ―』著者:上田隆一　講談社〈KS理工学専門書〉、2019年、ISBN 978-406-51-7006-9
