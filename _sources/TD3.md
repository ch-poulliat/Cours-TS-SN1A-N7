## {icon}`fa-solid fa-chalkboard-user` Séance TD-3 : Echantilonnage


### {icon}`fa-solid fa-folder` Exercice 1 :

````{margin}
```{dropdown} Propriétés TF
:animate: fade-in-slide-down
:icon: bell

**Propriétés générales T.F.**

\begin{align*} 
\small ax(t)+by(t) & \small \rightleftharpoons  aX(f)+bY(f) \\
\small x(t-t_{0}) & \small \rightleftharpoons X(f)e^{-i 2 \pi f t_{0}} \\
\small x(t)e^{+i 2 \pi f_{0} t} & \small \rightleftharpoons X(f-f_{0}) \\
\small x^{\ast }(t)& \small\rightleftharpoons  X^{\ast}(-f) \\
\small x(t) y(t)& \small \rightleftharpoons   X(f)\ast Y(f) \\
\small x(t)\ast y(t) & \small \rightleftharpoons  X(f) Y(f) \\
\small x(at+b) & \small \rightleftharpoons  \frac{1}{\left|a\right|}X\left(\frac{f}{a}\right) e^{i2\pi \frac{b}{a}f} \\
\small \frac{dx^{(n)}(t)}{dt^{n}} & \small \rightleftharpoons  \left( i2\pi f\right) ^{n}X(f)  \\
\small \left( -i2\pi t\right)^{n}x(t) & \small \rightleftharpoons  \frac{dX^{(n)}(f)}{df^{n}}  
\end{align*} 

**Formules Parseval**

$$\small\int_{\mathbb{R}}x(t)y^{\ast }(t)dt=\int_{\mathbb{R}}X(f)Y^{\ast }(f)df$$   
    
$$\small\int_{\mathbb{R}}\left| x(t)\right| ^{2}dt=\int_{\mathbb{R}}\left|X(f)\right| ^{2}df$$  

**Série de Fourier**
    
$$\small\underset{n\in \mathbb{Z}}{\sum }c_{n}e^{+i2\pi nf_{0}t} \rightleftharpoons \underset{n\in \mathbb{Z}}{\sum }c_{n}\delta \left( f-nf_{0}\right) $$  
```
````

````{margin}
```{dropdown} Tables TF
:animate: fade-in-slide-down
:icon: bell

\begin{align*}
\small 1 & \small \rightleftharpoons  \delta \left( f \right)\\ 
\small \delta \left( t\right) & \small \rightleftharpoons  1 \\ 
\small e^{+i2\pi f_{0}t}& \small \rightleftharpoons \delta \left( f-f_{0}\right)\\ 
\small\delta \left( t-t_{0}\right) & \small \rightleftharpoons e^{-i2\pi ft_{0}} \\
\small \amalg \hspace{-0.3cm}\amalg _{T}\left( t\right)  & \small\rightleftharpoons \frac{1}{T}\amalg \hspace{-0.3cm}\amalg _{1/T}\left(f\right) \\
\small \cos \left( 2\pi f_{0}t\right) & \small \rightleftharpoons \frac{1}{2}\left(\delta \left( f-f_{0}\right) +\delta \left( f+f_{0}\right) \right) \\ 
\small \sin \left( 2\pi f_{0}t\right) & \small \rightleftharpoons \frac{1}{2i}\left( \delta \left( f-f_{0}\right)-\delta \left( f+f_{0}\right) \right)\\ 
\small e^{-a\left| t\right| } & \small \rightleftharpoons \frac{2a}{a^{2}+4\pi ^{2}f^{2}} \\ 
\small e^{-\pi t^{2}} & \small \rightleftharpoons e^{-\pi f^{2}} \\ 
\small \Pi _{T}\left( t\right) & \small \rightleftharpoons T \mathrm{sinc}\left( \pi Tf\right) \\ 
\small \Lambda _{T}\left( t\right) & \small \rightleftharpoons T \mathrm{sinc}^{2}\left( \pi Tf\right) \\ 
\small B \mathrm{ sinc}\left( \pi Bt\right) & \small \rightleftharpoons \Pi _{B}\left( f\right) \\ 
\small B \mathrm{ sinc}^{2}\left( \pi Bt\right)  & \small \rightleftharpoons \Lambda _{B}\left( f\right) \\ 
\end{align*}  

où

$$\small \amalg \hspace{-0.3cm}\amalg _{T}\left( t\right) = \underset{k\in \mathbb{Z}}{\sum } \delta \left( t-kT\right)$$

$$\small \mathrm{sinc}\left( \pi Tf\right)=\frac{\sin \left( \pi Tf\right) }{\pi T f}$$
```
````


`````{admonition} Effet de l'échantillonnage
:class: exercise, dropdown

Soit le signal suivant : $x(t)=\cos(2 \pi f_0 t),  \; f_0=10$ kHz.

1. Tracer la transformée de Fourier de $x(t)$: $X(f)$.

    ````{admonition} Solution
    :class: solution, dropdown
  
    La transformée de Fourier de $x(t)$, $X(f)$, est tracée sur la figure suivante.

    ```{image} ./img/spectre_cos.png
    :alt: original_image
    :align: center
    ```
    ````

2. Est-il possible d'échantillonner $x(t)$ sans perte d'information ? Si oui à quelle condition ?

    ````{admonition} Solution
    :class: solution, dropdown
    
    Il est possible d'échantillonner $x(t)$ sans perte d'information en utilisant une fréquence d'échantillonnage 
    
    $$F_e>2f_0=20 \text{ kHz (respect de la condition de Shannon)}$$
    ````

3. Tracer, entre $0$ et $F_e$, la transformée de Fourier de $x(t)$ échantillonné à $T_e=1/F_e$ quand :
    
    a. $F_e=30$ kHz.

    b. $F_e=8$ kHz.
    
    ````{admonition} Solution
    :class: solution, dropdown

    La transformée de Fourier de $x(t)$, échantillonné à $T_e=1/F_e$, est tracée entre $0$ et $F_e$ sur les figures suivantes quand $F_e=30$ kHz et quand $F_e=8$ kHz.

    ```{image} ./img/spectre_cos_Fe_30.png
    :alt: original_image
    :align: center
    ```
    ```{image} ./img/spectre_cos_Fe_8.png
    :alt: original_image
    :align: center
    ```
    ````
4. A partir des échantillons nous souhaitons reconstruire $x(t)$ par filtrage passe-bas à $F_e/2$. Quels seront les signaux obtenus pour chaque fréquence d'échantillonnage précédente ?

    ````{admonition} Solution
    :class: solution, dropdown
    
    Par filtrage passe-bas à $F_e/2$, nous obtenons 
    
    $$x(t)=\cos(2 \pi f_0 t), \text{ avec} f_0=10 \text{ kHz pour } F_e=30 \text{ kHz}$$

    $$x(t)=\cos(2 \pi f_1 t), \text{ avec} f_1=2 \text{ kHz pour } F_e=8 \text{ kHz}$$
    ````
`````

### {icon}`fa-solid fa-folder` Exercice 2 :
````{admonition} Echantillonneur moyenneur
:class: exercise, dropdown

L'échantillonneur moyenneur est une méthode pratique d'échantillonnage qui consiste à calculer, toutes les $T_e$ secondes (période d'échantillonnage), la valeur moyenne du signal pendant un intervalle de temps $\theta $ ($\theta <<T_e$) et à affecter cette valeur moyenne à l'échantillon discrétisé :

\begin{eqnarray*}
y\left( kT_e\right) &=&\frac{1}{\theta }\int_{kT_e-\theta }^{kT}x(u)du \\
x_{ech}(t) &=&\sum_k y\left( kT_e\right) \delta \left( t-kT_e\right)
\end{eqnarray*}


1.  Démontrer que le signal échantillonné $x_{ech}(t)$ peut se mettre sous la forme :

    $$
    x_{ech}(t)=\frac{1}{\theta }\left[ \Pi _{\theta }\left( t\right) \ast x\left( t-\frac{\theta }{2}\right) \right] .\amalg \hspace{-0.3cm}\amalg_{T_e}\left( t\right)
    $$

    où $\Pi _{\theta }\left( t\right) $ et $\amalg \hspace{-0.3cm}\amalg_{T_e}\left( t\right) $ représentent respectivement la fenêtre rectangulaire de largeur $\theta$ et le peigne de Dirac de période $T_e$.

    ```{admonition} Solution
    :class: solution, dropdown

    $$x_{ech}(t)=\sum_k y\left( kT_e\right) \delta \left( t-kT_e\right)= y(t) \sum_k \delta \left( t-kT_e\right)=y(t) .\amalg \hspace{-0.3cm}\amalg_{T_e}\left( t\right)$$

    Reste à montrer que 
    
    $$y(t)=\frac{1}{\theta }\left[ \Pi _{\theta }\left( t\right) \ast x\left( t-\frac{\theta }{2}\right) \right],$$ 

    que l'on obtient de la manière suivante
    
    \begin{align*}
        y(t)&=\frac{1}{\theta }\int_{t-\theta }^{t}x(u)du\\
        &=\frac{1}{\theta}\int_{-\infty }^{+\infty}x(u) \times \Pi_{\theta}\left(u-\left(t-\frac{\theta}{2}\right)\right) du\\
        &=\frac{1}{\theta}\int_{-\infty }^{+\infty}x(u) \times \Pi_{\theta}\left(\left(t-\frac{\theta}{2}\right)-u\right) du\\
        &=\frac{1}{\theta }\left(x \ast \Pi_{\theta}\right)\left(t-\frac{\theta}{2}\right)
    \end{align*}
    ```
    
2. En déduire la transformée de Fourier correspondante $X_{ech}\left( f\right) $.

    ```{admonition} Solution
    :class: solution, dropdown
     
     \begin{align*}
         X_{ech}(f)&= Y(f) \ast \frac{1}{T_e} \amalg \hspace{-0.3cm}\amalg_{1/T_e}\left( f\right)\\
         &=\frac{1}{T_e}\sum_k Y\left( f-\frac{k}{T_e}\right), \text{ avec } Y(f)=sinc(\pi f \theta) X(f) e^{-j \pi f \theta}
     \end{align*}
    ```

3.  En considérant un signal à support spectral borné $2\Delta f$ et en prenant en compte que la fonction $sinc(\pi \theta f)$ peut être supposée constante sur l'intervalle $\left[ -\frac{1}{3\theta },\frac{1}{3\theta }\right] $

    $$
    sinc(\pi \theta f)=\frac{\sin (\pi \theta f)}{\pi \theta f}\approx 1 \; \text{pour }f\in \left[ -\frac{1}{3\theta },\frac{1}{3\theta }\right]
    $$

    a. quelle(s) condition(s) doit vérifier $\theta $ pour que le signal $x(t)$ puisse être restitué par filtrage de $x_{ech}(t)$ ?

    ```{admonition} Solution
    :class: solution, dropdown
    
    Il faut que $\Delta f \leq \frac{1}{3\theta} \Leftrightarrow \theta \leq \frac{1}{3\Delta f}$
    ```
    
    b. Dans ces conditions peut-on échantillonner à la fréquence de Shannon ?

    ```{admonition} Solution
    :class: solution, dropdown
    
    Après filtrage antialiasing on pourra prendre $F_e$ tel que $\Delta f < \frac{F_e}{2}=\frac{1}{2T_e} \Leftrightarrow T_e< \frac{1}{2\Delta f}$
    ```
````

### {icon}`fa-solid fa-folder` Exercice 3 :
````{admonition} Echantillonnage d'un signal à spectre non borné
:class: exercise, dropdown

Soit le signal $x(t)$ défini par :

$$
x(t) = \left\{
    \begin{array}{rl}
        e^{-at} & \mbox{si } t\geq 0, a>0\\
        0 & \mbox{si } t<0. \\
    \end{array} \right. \;
$$

1. Déterminer la transformée de Fourier $X(f)$ du signal $x(t)$. Tracer $\left|X(f)\right|$.

    ```{admonition} Solution
    :class: solution, dropdown
     
    $$X(f)=\int_{0}^{+\infty} e^{-(a+j 2 \pi f)t} dt=\frac{1}{a+j 2 \pi f}$$
    
    $$\left|X(f)\right|=\frac{1}{\sqrt{a^2+ 4 \pi^2 f^2}}$$
    ```

2. Le signal $x(t)$ est-il échantillonnable sans perte d'information ? Expliquez votre réponse.

    ```{admonition} Solution
    :class: solution, dropdown
    
    Non car le spectre n'est pas borné. Il n'est donc pas possible d'appliquer la condition de Shannon.
    ```
    
3. En considérant la transformée de Fourier comme négligeable pour une atténuation minimale de $40$ dB par rapport à sa valeur maximum, dimensionner la fréquence d'échantillonnage, $F_e$, à utiliser.

    ```{admonition} Solution
    :class: solution, dropdown
    
    On a le maximum du spectre pour $f=0$. On souhaite donc trouver $F_{max}$ telle que :
    
    $$10 \log_{10}\left|X(F_{max})\right|^2 \leq 10 \log_{10}\left|X(0)\right|^2-10 \log_{10}\left(10^4\right)=10 \log_{10} \frac{\left|X(0)\right|^2}{10^4}$$
    
    D'où 
    
    $$\frac{1}{\sqrt{a^2+ 4 \pi^2 F_{max}^2}}\leq \frac{1}{10^4 a^2}$$ 
    
    et donc 
    
    $$F_{max}^2\geq \frac{\left(10^4-1\right) a^2}{4 \pi^2}$$
     
    Soit, en négligeant $1$ devant $10^4$ : 
    
    $$F_{max}\geq \frac{100 a}{2 \pi} \text{ et donc } F_e\geq \frac{100 a}{\pi}$$
    
    ```
    
4. Une fois $F_e$ déterminée, quel traitement doit-on appliquer au signal avant de l'échantillonner ?

    ```{admonition} Solution
    :class: solution, dropdown
    
    Un filtre anti repliement afin de tronquer le spectre du signal à $F_{max}$.
    ```
````