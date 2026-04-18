
## 1. 問題描述

給定系統方程式（牛頓第二定律建模）：

$$m \frac{d^2x}{dt^2} + c \frac{dx}{dt} + kx = F(t)$$

其中：

- $m$：質量 (Mass)
- $c$：阻尼 (Damping coefficient)
- $k$：彈簧常數 (Spring constant)
- $F(t) = F_0 \cos(\omega t)$：正弦外力 (Harmonic forcing function)

目標：求解位移 $x(t)$。

---

## 2. 數學求解過程

此微分方程的通解由兩部分組成：
$$x(t) = x_h(t) + x_p(t)$$
其中 $x_h(t)$ 是齊次解（代表瞬態響應）， $x_p(t)$ 是特解（代表穩態響應）。在工程實務中，我們通常最關注穩態響應 $x_p(t)$ 。

### A. 齊次解 $x_h(t)$ (Transient Response)
考慮 $m\ddot{x} + c\dot{x} + kx = 0$，其特徵方程為：
$$ms^2 + cs + k = 0$$
解得 $s = \frac{-c \pm \sqrt{c^2 - 4mk}}{2m}$。根據 $c$ 的大小，會出現欠阻尼、過阻尼或臨界阻尼三種情況。隨時間增加， $x_h(t)$ 會趨近於 0。

### B. 特解 $x_p(t)$ (Steady-State Response)
當外力為 $F_0 \cos(\omega t)$ 時，我們假設特解形式為：
$$x_p(t) = X \cos(\omega t - \phi)$$
其中 $X$ 為振幅， $\phi$ 為相位差。

將假設代入原方程，或使用複數方法（令 $\hat{F} = F_0 e^{i\omega t}$）：
1. **振幅 $X$：**
   $$X = \frac{F_0}{\sqrt{(k - m\omega^2)^2 + (c\omega)^2}}$$
2. **相位角 $\phi$：**
   $$\phi = \tan^{-1}\left( \frac{c\omega}{k - m\omega^2} \right)$$

---

## 3. 最終解答

假設系統已進入穩態（無視隨時間衰減的齊次項），位移函數為：

$$x(t) = \frac{F_0}{\sqrt{(k - m\omega^2)^2 + (c\omega)^2}} \cos\left( \omega t - \tan^{-1}\left( \frac{c\omega}{k - m\omega^2} \right) \right)$$

### 物理意義說明：
1. **共振 (Resonance)**：當外力頻率 $\omega$ 接近系統自然頻率 $\omega_n = \sqrt{k/m}$ 時，分母變小，振幅 $X$ 會急劇增大。
2. **阻尼影響**：阻尼 $c$ 的存在防止了共振時振幅無限大，並產生了相位延遲 $\phi$。
