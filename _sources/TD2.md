## Séance TD-2 : Filtrage


### Exercice 1 :

``````{exercise} Filtre moyenneur à mémoire finie 
:nonumber:
:class: dropdown

Le filtre moyenneur à mémoire finie est un système défini par la relation entrée-sortie suivante :

$$
y(t)=\frac{1}{T} \int_{t-T}^{t} x(u) du,
$$

où $x(t)$ représente l'entrée du filtre et $y(t)$ la sortie.

1. Montrer que ce filtre moyenneur à mémoire finie est un filtre linéaire et calculer sa réponse impulsionnelle.

    `````{dropdown} Solution
    :animate: fade-in-slide-down


    **Il existe plusieurs manières de répondre à cette question :**

    ````{tab-set}

    ```{tab-item} Sol. 1
                
    Placer $x(t)=e^{j 2 \pi f t}$ à l'entrée du filtre et montrer que la sortie $y(t)$ s'écrit alors $y(t)=H(f)e^{j 2 \pi f t}$.    

    Ici :
    
    \begin{align*}
    y(t)&=\frac{1}{T}\int_{t-T}^{t} e^{j 2 \pi f u} du\\
    &=sinc(\pi f T) e^{-j \pi f T} e^{j 2 \pi f t}\\
    &=H(f)x(t)
    \end{align*} 
    
    avec 
    
    $$H(f)=sinc(\pi f T)e^{-j \pi f T}.$$
    
    
    On a bien un filtre linéaire de réponse en fréquence 
    
    $$H(f)=sinc(\pi f T)e^{-j \pi f T}$$ 
    
    et donc de réponse impulsionnelle 
    
    $$h(t)=\frac{1}{T} \Pi_T \left(t-\frac{T}{2}\right)$$
    
    si $\Pi_T \left(t\right)$ représente une fonction porte de largeur $T$, de hauteur $1$ et centrée en $t=0$.
    ```
    ```{tab-item} Sol. 2
              
    Montrer que, pour toute entrée $x(t)$, la sortie $y(t)$ s'écrit $y(t)=x(t) \ast h(t)$, où $h(t)$ représente la réponse impulsionnelle du filtre et le définit.
                
    Ici :
    
    \begin{align*}
    y(t)&=\frac{1}{T} \int_{t-T}^{t} x(u) du\\
    &=\frac{1}{T} int_{\mathbb{R}} x(u) \Pi_T \left( u- \left( t-\frac{T}{2}\right) \right) du\\
    &=\frac{1}{T}\int_{\mathbb{R}} x(u) \Pi_T \left(\left(t-\frac{T}{2}\right)-u\right) du\\
    &=x(t) \ast h(t)  
    \end{align*}
    
    avec 
    
    $$h(t)=\frac{1}{T}\Pi_T \left(t-\frac{T}{2}\right).$$ 
    
    On a donc bien un filtre linéaire, de réponse impulsionnelle $h(t)=\frac{1}{T}\Pi_T \left(t-\frac{T}{2}\right)$.
    ```
    ```{tab-item} Sol. 3
                
    Placer un dirac en entrée, déterminer la sortie, $h(n)$, correspondante et montrer ensuite que, pour toute entrée $x(t)$, la sortie $y(t)$ peut s'écrire comme $y(t)=x(t) \ast h(t)$.
    
    Ici si $x(t)=\delta(t)$ alors 

    $$ 
    y(t) = \frac{1}{T} \int_{t-T}^{t} \delta(u) du =\left\{
          \begin{array}{rl}
          \frac{1}{T} & \mbox{si } 0<t<T\\
           0 & \mbox{sinon.} \\
         \end{array} \right. \;
    $$

    D'où 

    $$h(t)=\frac{1}{T} \Pi_T \left(t-\frac{T}{2}\right)$$
 
    Il faut alors montrer que nous avons bien un filtre, c'est-à-dire que l'on a bien $y(t)=x(t)\ast h(t)$ : 
     
    \begin{align*}
       x(t) \ast h(t) &= \frac{1}{T}\Pi_T \left(t-\frac{T}{2}\right) \ast x(t)\\
       &= \frac{1}{T}\int_{\mathbb{R}} x(u) \Pi_T \left(t-\frac{T}{2}-u\right) du\\
       &=\frac{1}{T}\int_{t-T}^{t} x(u) du=y(t)
    \end{align*}

    Nous avons bien affaire à un filtre linéaire.
       
    ```
    ```{tab-item} Sol. 4
            
    on peut également dériver :
    
    $$y'(t)=\frac{1}{T}\left\{x(t)-x(t-T)\right\}$$
     
    D'où par transformée de Fourier 
    
    $$j 2 \pi f Y(f)=\frac{1}{T}\left\{X(f)-e^{-j 2 \pi f T} X(f)\right\}$$ 
    
    Et donc 
    
    $$H(f)=\frac{Y(f)}{X(f)}=\frac{1-e^{-j 2 \pi f T}}{j 2 \pi f T}=e^{- j \pi f T} sinc(\pi f T)$$
    
    Ce qui donne par transformée de Fourier inverse : 
    
    $$h(t)=\frac{1}{T}\Pi_T \left(t-\frac{T}{2}\right)$$
    ```
    ````
    `````
        
2. Ce filtre est-il réalisable ?

    `````{dropdown} Solution
    :animate: fade-in-slide-down
    
    Un filtre est réalisable si :
    
    a. sa réponse impulsionnelle $h(t)$ est réelle : OK ici.
    
    b. sa réponse impulsionnelle est causale : OK ici car pour $t<0$ on a bien  $h(t)=0$.
    
    c. sa réponse impulsionnelle vérifie la condition de stabilité $\int_\mathbb{R} \left|h(t)\right|dt<\infty$ : OK ici car $\int_\mathbb{R} \left|h(t)\right|dt=\frac{1}{T}\times T=1$


    **$\Rightarrow$ Ce filtre est donc bien réalisable**
    `````

``````

### Exercice 2 :

````{margin}


```{tip} 
:class: dropdown

Le rapport Signal sur Bruit en décibels (dB) est défini par : 

$$RSB=10\log_{10} \left( \frac{P_{Y_{s}}}{P_{YB}}\right) \text{ (dB).}$$  
    
On le note aussi *SNR* (Signal to Noise Ratio).
```
````


``````{exercise} Calcul d'un Rapport Signal sur Bruit (RSB) en sortie d'un filtre linéaire
:nonumber:
:class: dropdown

Considérons un filtre linéaire de réponse en fréquence :

$$
H(f)=\frac{1}{\theta +j2\pi f}
$$

On applique à l'entrée de ce filtre un processus aléatoire $X(t)$ constitué de la somme d'un signal sinusoïdal $s(t)=A\sin \left( 2\pi f_{0}t\right) $, où $f_0$ et $A$ sont des constantes et d'un bruit blanc stationnaire réel $B(t)$, de densité spectrale de puissance $s_{B}(f)=\frac{N_{0}}{2} \forall f$ :

$$
X(t)=s(t)+B(t)
$$

Le filtre étant linéaire, la sortie du filtre s'écrit :

$$
Y(t)=Y_{s}(t)+Y_{B}(t)
$$

où $Y_{s}(t)$ représente la réponse du filtre à l'entrée $s(t)$ et $Y_{B}(t)$ représente la réponse du filtre à l'entrée $B(t)$.

1. Donner l'expression du rapport Signal sur Bruit à la sortie du filtre :

    $$
    RSB=\frac{P_{Y_{s}}}{P_{Y_{B}}}
    $$

    où $P_{Y_s}$ représente la puissance du signal $Y_s(t)$ et $P_{Y_B}$ la puissance du signal $Y_B(t)$.

    `````{dropdown} Solution
    :animate: fade-in-slide-down


    **Il existe plusieurs manières de répondre à cette question :**

    ````{tab-set}

    ```{tab-item} Sol. 1

    \begin{align*}
    P_{Y_s}&=\int_{\mathbb{R}} S_{Y_{s}}(f) df\\
    &=\int_{\mathbb{R}} S_{s}(f) \left|H(f)\right|^2 df\\
    &=\int_{\mathbb{R}} \frac{A^2}{4}\left\{\delta(f-f_0)+\delta(f+f_0)\right\} \frac{1}{\theta^2+4 \pi^2 f^2} df\\
    &=\frac{A^2}{4} \frac{1}{\theta^2+4 \pi^2 f_0^2} \times 2
    \end{align*}
    
    \begin{align*}
    P_{Y_B}&=\int_{\mathbb{R}} S_{Y_{B}}(f) df\\
    &=\int_{\mathbb{R}} S_{B}(f) \left|H(f)\right|^2 df\\
    &=\int_{\mathbb{R}} \frac{N_0}{2} \frac{1}{\theta^2+4 \pi^2 f^2} df\\
    &=\frac{N_0}{4 \pi \theta} \int_{\mathbb{R}} \frac{1}{1+u^2} du\\
    &=\frac{N_0}{4 \pi \theta} \left[arctan(u)\right]_{-\infty}^{+\infty}\\
    &=\frac{N_0}{4 \theta}.
    \end{align*}
    ```
    ```{tab-item} Sol. 2
    
    Autre solution en utilisant les tables de Transformées de Fourier : 
    
    \begin{align*}
    R_{Y_B}(\tau)&=TF^{-1}\left[S_{Y_{B}}(f)\right]\\
    &=\frac{N_0}{4 \theta}e^{- \theta |\tau|} 
    \end{align*}
    
    qui donne 
    
    $$P_{Y_B}=R_{Y_B}(0)=\frac{N_0}{4 \theta},$$
   
    
    D'où l'expression du rapport signal sur bruit en sortie du filtre : 
    
    $$RSB=\frac{2 \theta A^2}{N_0}\frac{1}{\theta^2+4 \pi^2 f_0^2}$$
    ```
    ````
    `````

2. Montrer qu'il est maximal pour $\theta =2\pi f_{0}$.

    `````{dropdown} Solution
    :animate: fade-in-slide-down

    \begin{align*}
    \frac{d RSB}{d \theta}&=2\frac{A^2}{N_0}\frac{4 \pi^2 f_0^2- \theta^2}{\left(4 \pi^2 f_0^2 + \theta^2\right)^2}
    \end{align*}
     
     et donc 
     
    $$\frac{d RSB}{d \theta}=0 \text{ pour }\theta=2\pi f_{0}$$
   
    `````
``````

### Exercice 3

````{margin}

```{tip} 
:class: dropdown

Si la variable aléatoire $Z$ suit une loi normale $\mathcal{N}\left( m,\sigma ^{2}\right)$ et $u$ est une constante alors on a :

$$
E\left[ e^{uZ}\right] =\exp \left( mu+\frac{\sigma ^{2}}{2}u^{2}\right)
$$

```
````


````{exercise} Filtrage non linéaire de type exponentiel
:nonumber:
:class: dropdown

On considère un filtre non linéaire de type exponentiel. Si $X\left(t\right) $ est l'entrée du filtre, la sortie $Y\left( t\right) $ s'écrit :

$$
Y\left( t\right) =\exp \left( X(t)\right)
$$

L'entrée du filtre est un bruit gaussien, réel, centré, de variance $\sigma ^{2}$.

1. Calculez la moyenne du signal en sortie du filtre.

    ```{dropdown} Solution
    :animate: fade-in-slide-down
    
    \begin{align*}
    m_Y&=E\left[Y(t)\right]\\
    &=E\left[e^{X(t)}\right]\\
    &=e^{\frac{\sigma^2}{2}} \text{ (voir Tip)}
    \end{align*}
    ```
   

2. Calculez la variance du signal en sortie du filtre.

    ```{dropdown} Solution
    :animate: fade-in-slide-down

    
    \begin{align*}
    Var_Y1=E\left[\left(Y(t)-m_Y\right)^2\right]\\
    &=E\left[Y^2(t)\right]- m_Y^2\\ 
    &=E\left[e^{2X(t)}\right]-e^{\sigma^2}\\
    &=e^{2\sigma^2}-e^{\sigma^2}
    \end{align*}
    ```


3. Calculez la fonction d'autocorrélation du signal en sortie du filtre en fonction de celle du signal à l'entrée.

    ```{dropdown} Solution
    :animate: fade-in-slide-down
    
    On utilise le théorème de Price :

    $$\frac{\partial E\left[Y_1(t)Y_2(t)\right]}{\partial E\left[X_1(t)X_2(t)\right]}=E\left[\frac{\partial Y_1}{\partial X_1} \frac{\partial Y_2}{\partial X_2}\right]$$
    
    avec

    $$X_1(t)=X(t), \; Y_1(t)=e^{X(t)}=Y(t)$$ 

    et 
    $$X_2(t)=X(t-\tau), \; Y_2(t)=e^{X(t-\tau)}=Y(t-\tau)$$

    Cela donne :

    $$\frac{\partial R_Y(\tau)}{\partial R_X(\tau)}=E\left[e^{X(t)}e^{X(t-\tau)}\right]=E\left[Y(t) Y(t-\tau)\right]=R_Y(\tau).$$ 

    Et donc 
    
    $$\frac{\partial R_Y(\tau)}{R_Y(\tau)}=\partial R_X(\tau)$$

    Soit 
    
    $$\ln R_Y(\tau)=R_X(\tau)+K \text{ (K constante) donnant } R_Y(\tau)=e^{K+R_X(\tau)}$$

    **Calcul de K :**

    $$R_Y(0)=e^{K+\sigma^2}=E\left[Y^2(t)\right]=E\left[e^{2 X(t)}\right]=e^{2 \sigma^2}$$
    
    D'où 
    
    $$K=\sigma^2$$ 
    
    et 
    
    $$R_Y(\tau)=e^{\sigma^2}e^{R_X(\tau)}$$
    ```
````

