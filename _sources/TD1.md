## Séance TD-1 : Signaux & Spectres



````{exercise} Etude du secteur
:class: dropdown

On considère dans cet exercice différents modèles du secteur et on étudie la densité spectrale de puissance des signaux obtenus à l'aide de ces modèles.

1. Dans une première approche, on utilise le modèle :

    $$
    X\left( t\right) =A_{0}\cos \left( 2\pi f_0t\right)
    $$

    où $f_{0}=50Hz$ et $A_{0}=220\sqrt{2}V$.

    Préciser la classe à laquelle appartient le signal $X(t)$ puis déterminer sa fonction d'autocorrélation $R_X(\tau)$ et sa densité spectrale de puissance $S_X(f)$.  

    ```{dropdown} Solution
    :animate: fade-in-slide-down

    - Le signal est déterministe à puissance moyenne finie périodique : en notant $T_0=\frac{1}{f_0}$, on a 

    \begin{align*}
    P&=\frac{1}{T_0}\int_{T_0} \left|X(t)\right|^2 dt\\
    &=\frac{1}{T_0}\int_{T_0} A_0^2 \cos^2\left(2 \pi f_0 t\right) dt\\
    &=\frac{A_0^2}{T_0}\int_{T_0}  \frac{1}{2} \left\{1+\cos\left(4 \pi f_0 t\right)\right\} dt\\
    &=\frac{A_0^2}{2}<\infty
    \end{align*}


    - Sa fonction d'autocorrélation est donc donnée par : 

    \begin{align*}
    R_X(\tau)&=\frac{1}{T_0}\int_{T_0} X(t) X^*(t-\tau) dt \\
    &=\frac{1}{T_0}\int_{T_0} A_0^2 \cos\left(2 \pi f_0 t\right)\cos\left(2 \pi f_0 (t-\tau)\right) dt\\
    &=\frac{A_0^2}{T_0}\int_{T_0}  \frac{1}{2} \left\{\cos\left(2 \pi f_0 \tau\right)+\cos\left(4 \pi f_0 t - 2 \pi f_0 \tau\right)\right\} dt\\
    &=\frac{A_0^2}{2} \cos\left(2 \pi f_0 \tau\right)
    \end{align*}

    - Sa DSP est donnée par : 

    \begin{align*}
      S_X(f)&=TF\left[R_X(\tau)\right]\\
      &=\frac{A_0^2}{4} \left\{\delta\left(f- f_0\right)+\delta\left(f+f_0\right)\right\}
    \end{align*}
    ```

2. On considère ensuite le modèle suivant :

    $$
    X\left( t\right) =A_{0}\cos \left( 2\pi f_{0}t+\theta \right)
    $$

    $\theta $ étant une variable aléatoire uniformément répartie sur l'intervalle $\left[ 0,2\pi \right[ $, $f_{0}=50Hz$ et $A_{0}=220\sqrt{2}V$. 

    Préciser la classe à laquelle appartient le signal $X(t)$ puis d\'{e}terminer sa moyenne, sa fonction d'autocorrélation $R_X(\tau)$ et sa densité spectrale de puissance $S_X(f)$.

    ```{dropdown} Solution
    :animate: fade-in-slide-down

    - Le signal est aléatoire.

    - Sa moyenne est donc donnée par : 

    \begin{align*}
       m_X&=E\left[X(t)\right]=E\left[A_0 \cos\left(2 \pi f_0 t+\theta\right)\right]\\
       &=A_0 \int_{0}^{2 \pi} \cos\left(2 \pi f_0 t+\theta\right)\times\frac{1}{2\pi} d\theta\\
       &=0
    \end{align*}


    - Sa fonction d'autocorrélation est donc donnée par :

    \begin{align*}
    R_X(\tau)&=E\left[X(t)X^*(t-\tau)\right]\\
    &=E\left[A_0^2 \cos\left(2 \pi f_0 t+\theta\right)\cos\left(2\pi f_0 (t-\tau)+\theta\right)\right]\\
    &=\frac{A_0^2}{2}E\left[ \cos\left(2 \pi f_0 \tau\right)+\cos\left(4 \pi f_0 t-2 \pi f_0 \tau +2\theta\right)\right]\\
    &=\frac{A_0^2}{2}\cos\left(2 \pi f_0 \tau\right)
    \end{align*} 

    - Le signal est stationnaire au second ordre car sa moyenne et sa fonction d'autocorrélation sont indépendantes du temps.

    - Sa DSP est donnée par : 

    $$
    S_X(f)=TF\left[R_X(\tau)\right]=\frac{A_0^2}{4} \left\{\delta\left(f- f_0\right)+\delta\left(f+f_0\right)\right\}
    $$
    ```
3. La fréquence du courant électrique n'est jamais exactement $f_{0}=50Hz$. Afin de modéliser les variations en fréquence, on considère le modèle :

    $$
    X\left( t\right) =A_{0}\cos \left( 2\pi ft+\theta \right)
    $$

    $f$ étant une variable uniformément répartie sur l'intervalle $ \left[ f_{0}-\Delta f,f_{0}+\Delta f\right] $ indépendante de $\theta $. Calculer alors la moyenne, la fonction d'autocorrélation et la densité spectrale de puissance de $X\left( t\right) $.
    
    ```{dropdown} Solution
    :animate: fade-in-slide-down
    
    - Le signal est aléatoire.
    
    - Sa moyenne est donc donnée par : 
    
    \begin{align*}
    m_X &=E\left[X(t)\right]=E_{f,\theta}\left[A_0 \cos\left(2 \pi f t+\theta\right)\right]\\
    &=E_{f}\left[E_{\theta}\left[A_0 \cos\left(2 \pi f t+\theta\right) | f\right]\right]\\
    &=E_{f}\left[0\right]=0
    \end{align*}

    - Sa fonction d'autocorrélation est donc donnée par : 
    \begin{align*}
    R_X(\tau)&=E\left[X(t)X^*(t-\tau)\right]\\
             &=E_{f}\left[E_{\theta}\left[A_0^2 \cos\left(2 \pi f t+\theta\right)\cos\left(2 \pi f (t-\tau)+\theta\right)| f\right]\right]\\
             &=E_{f}\left[\frac{A_0^2}{2}\cos\left(2 \pi f \tau\right)\right]\\
             &=\frac{A_0^2}{2} \int_{f_{0}-\Delta f}^{f_{0}+\Delta f}\cos\left(2 \pi f \tau\right)\times\frac{1}{2 \Delta f} df\\
             &=\frac{A_0^2}{4 \Delta f} \left[\frac{\sin\left(2 \pi f \tau\right)}{2 \pi \tau}\right]_{f_{0}-\Delta f}^{f_{0}+\Delta f}\\
             &=\frac{A_0^2}{8 \pi \tau \Delta f} \left\{\sin\left(2 \pi (f_{0}+\Delta f) \tau\right)-\sin\left(2 \pi (f_{0}-\Delta f) \tau\right)\right\}\\
             &=\frac{A_0^2}{4 \pi \tau \Delta f} \sin\left(2 \pi \Delta f \tau\right) \cos\left(2 \pi f_{0}\tau\right)\\
             &=\frac{A_0^2}{2} sinc\left(2 \pi \Delta f \tau\right) \cos\left(2 \pi f_{0}\tau\right)
    \end{align*}
    
    - Le signal est stationnaire au second ordre car sa moyenne et sa fonction d'autocorrélation sont indépendantes du temps.

    - Sa DSP est donnée par :
    
     \begin{align*}
     S_X(f)=TF\left[R_X(\tau)\right]&=\frac{A_0^2}{2} \frac{1}{2 \Delta f} \prod_{2 \Delta f}(f) \ast \frac{1}{2}\left\{\delta\left(f- f_0\right)+\delta\left(f+f_0\right)\right\}\\
     &=\frac{A_0^2}{8\Delta f} \left\{\prod_{2 \Delta f}\left(f- f_0\right)+\prod_{2 \Delta f}\left(f+f_0\right)\right\}
     \end{align*}
    
    ```

````