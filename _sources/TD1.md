## Séance TD-1 : Signaux & Spectres



````{exercise} Etude du secteur
:nonumber:
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

````{exercise} Modulation d'amplitude
:nonumber:
:class: dropdown

Soit $A(t)$ un signal aléatoire stationnaire, réel, de fonction d'autocorrélation $R_A(\tau)$ et de densité spectrale de puissance $S_A(f)$ définie par :

$$
S_A(f)=\left\{
              \begin{array}{ll}
              \alpha, & \hbox{si $\; |f|\leq F$} \\
                0, & \hbox{sinon.}
              \end{array}
            \right.
$$

On considère le signal $X(t)=A(t) \cos\left(2 \pi f_0 t + \theta \right)$, avec $F\ll f_0$ et $\theta $ une variable aléatoire uniformément répartie sur l'intervalle $\left[ 0,2\pi \right[$ indépendante de $A(t)$.

1. Montrer que $X(t)$ est un signal aléatoire stationnaire. Déterminer et représenter graphiquement sa densité spectrale de puissance.

    ```{dropdown} Solution
    :animate: fade-in-slide-down

    - Le signal est aléatoire. Pour montrer qu'il est stationnaire il faut montrer que $m_X$ et $R_X$ sont indépendantes du temps.

    - Sa moyenne est donnée par : 
    
    $$m_X=E\left[X(t)\right]=E\left[A(t) \cos\left(2 \pi f_0 t+\theta\right)\right]=E\left[A(t)\right] E\left[\cos\left(2 \pi f_0 t+\theta\right)\right]$$

    car $A$ et $\theta$ sont indépendantes. D'où $m_X=0$.

    - Sa fonction d'autocorrélation est donnée par :
    
    \begin{align*}
    R_X(\tau)&=E\left[X(t)X^*(t-\tau)\right]\\
    &=E\left[A(t) \cos\left(2 \pi f_0 t+\theta\right) A^*(t-\tau) \cos\left(2 \pi f_0 (t-\tau)+\theta\right)\right]\\
    &=E\left[A(t)A^*(t-\tau)\right] E\left[\cos\left(2 \pi f_0 t+\theta\right)  \cos\left(2 \pi f_0 (t-\tau)+\theta\right)\right]\\
    &=R_A(\tau) \times \frac{1}{2} \cos\left(2 \pi f_0 \tau\right)
    \end{align*}


    - Le signal est bien stationnaire (au second ordre) car sa moyenne et sa fonction d'autocorrélation sont indépendantes du temps.

    - Sa DSP est donnée par 
    \begin{align*}
    S_X(f)&=TF\left[R_X(\tau)\right]\\
    &=S_A(f) \ast \frac{1}{4} \left\{\delta\left(f- f_0\right)+\delta\left(f+f_0\right)\right\}\\
    &=\frac{1}{4} \left\{S_A\left(f- f_0\right)+S_A\left(f+f_0\right)\right\}
    \end{align*}
    ```
    
2. Afin de retrouver le signal $A(t)$ à partir de $X(t)$, on construit le signal 


    $$Y(t)=X(t) \cos\left(2 \pi f_0 t + \theta \right).$$
    
    a. Déterminer et tracer la densité spectrale de puissance de $Y(t)$.
            
            
    ```{dropdown} Solution
     :animate: fade-in-slide-down
        
     \begin{align*}
     R_Y(\tau)&=E\left[Y(t)Y^*(t-\tau)\right]\\
              &=E\left[X(t) \cos\left(2 \pi f_0 t+\theta\right) X^*(t-\tau) \cos\left(2 \pi f_0 (t-\tau)+\theta\right)\right]
     \end{align*}
        
     Attention ici $X(t)$ et le cosinus ne sont pas indépendants, tous deux dépendent de $\theta$. D'où 
        
     \begin{align*}
            R_Y(\tau)&=E\left[A(t) \cos^2\left(2 \pi f_0 t+\theta\right) A^*(t-\tau) \cos^2\left(2 \pi f_0 (t-\tau)+\theta\right)\right]\\
            &=R_A(\tau) \times E\left[\frac{1+\cos\left(4 \pi f_0 t+2\theta\right)}{2} \frac{1+\cos\left(4 \pi f_0 (t-\tau)+2\theta\right) }{2} \right]\\
            &=\frac{1}{4}R_A(\tau)E\left[1+\cos\left(2\theta+...\right)+\cos\left(2\theta+...\right)+\frac{1}{2}\left\{\cos\left(4 \pi f_0 \tau \right)+\cos\left(4 \theta + ...\right)\right\}\right]\\
            &=\frac{1}{4}R_A(\tau)\left\{1+\frac{1}{2}\cos\left(4 \pi f_0 \tau\right)\right\}
     \end{align*}
        
     \begin{align*}
            S_Y(f)&=TF\left[R_Y(\tau)\right]=\frac{1}{4} S_A(f) \ast \left\{ \delta(f) + \frac{1}{4} \left\{\delta\left(f- 2f_0\right)+\delta\left(f+2f_0\right)\right\}\right\}\\
            &=\frac{1}{4} S_A(f) + \frac{1}{16} \left\{S_A\left(f- 2f_0\right)+S_A\left(f+2f_0\right)\right\}
     \end{align*}
    ```
    

    b. Quel traitement doit-on utiliser pour retrouver $A(t)$ à partir de $Y(t)$ ?
       
    ```{dropdown} Solution
    :animate: fade-in-slide-down
        
    Il faudra utiliser un filtre passe-bas pour conserver uniquement la partie $\frac{1}{4} S_A(f)$ et couper la partie qui se trouve autour de $2f_0$.
        
    ```
 ````