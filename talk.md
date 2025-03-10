class: middle, center, title-slide

# Les modèles de diffusion et leurs applications scientifiques

Café numérique<br>
3 mars 2025

<br>

.grid[
.kol-1-3[
.width-60.circle[![](figures/faces/gilles.jpg)]
]
.kol-2-3[

<br>
Gilles Louppe<br>
[g.louppe@uliege.be](mailto:g.louppe@uliege.be)

]
]

---

class: black-slide, middle

.width-100[![](figures/flux.png)]

.center[Ces images sont-elles réelles ou générées par une IA?]

.footnote[Source: [black forest labs](https://blackforestlabs.ai), 2024.]

---

class: middle

.center[
.width-100[![](figures/perturb_vp.gif)]

Un .bold[processus de diffusion] est un processus stochastique $x\_t$ qui détériore progressivement un signal $x$ en lui ajoutant du bruit.

]

.footnote[Credits: [Song](https://yang-song.net/blog/2021/score/), 2021.]

---

class: middle

.center[
.width-100[![](figures/denoise_vp.gif)]

En simulant le processus de .bold[diffusion à l'envers], on peut<br> retirer progressivement le bruit et retrouver un signal $x$.
]

.footnote[Credits: [Song](https://yang-song.net/blog/2021/score/), 2021.]

---

class: middle

.center[
.width-100[![](figures/architecture.svg)]

Mathématiquement, la diffusion inverse peut s'approximer par un .bold[réseau de neurones] $d\_\theta(x\_t, t)$ entraîné à retirer le bruit d'un signal perturbé $x\_t$.
]

---

class: middle, center

.center.width-10[![](figures/icons/remote-control.png)]

La génération par diffusion inverse peut être télécommandée par<br> un signal auxiliaire $y$ pour produire des données conditionnelles.

---

class: middle

.center.width-100[![](figures/sd35-prompts.jpg)]

.center[Text-to-image generation<br> ($x$ = image, $y$ = texte)]

.footnote[Source: [stability.ai](https://stability.ai/stable-image), 2024.]

---

class: middle

.center[

<video  width="100%" controls autoplay muted>
     <source src="./figures/super-resolution.m4v" type="video/mp4">
</video>

]

.center[Image-to-image generation<br> ($x$ = image haute résolution, $y$ = image basse résolution)]

.footnote[Credits: [Saharia et al](https://arxiv.org/abs/2104.07636), 2021.]

---

class: middle

.center[
    <video width="90%" controls autoplay muted>
        <source src="figures/sora.webm" type="video/mp4">
    </video>
]

.center[Text-to-video generation<br> ($x$ = vidéo, $y$ = texte)]

.footnote[Source: [OpenAI](https://openai.com/sora/), 2024.]

---

background-image: url(figures/controverse.png)
background-size: contain

.center[L'IA générative, un réel progrès?]

???

On pourrait se demander, mais bon sang, à quoi bon générer de jolies images ou vidéos? Est-ce vraiment utile?

Les applications de cette technologie sont déjà bien nombreuses dans les domaines de l'audiovisuel, comme le cinéma, la télévision, la musique, la photographie, le design, le jeu vidéo, la publicité, etc, où des artistes, des acteurs, des musiciens, des écrivains, ou des réalisateurs sont, dans le meilleur des cas, assistés, et dans le pire des cas, remplacés par ces modèles.

Cela suscite immédiatement de nombreuses questions sociétales, éthiques, et économiques, qui sont loin d'être résolues, mais on peut en tout cas légitimement se demander si ces technologies constituent vraiment un réel progrès. 

---

class: middle

.center.width-10[![](figures/icons/science.png)]

.center[L'IA est capable de résoudre des problèmes scientifiques<br> que personne ne peut résoudre.]

---

class: middle, black-slide, center
background-image: url(figures/y.png)
background-size: cover

.bold.larger[D'observations bruitées $y$...]

---

class: middle, black-slide, center
background-image: url(figures/x.png)
background-size: cover

.bold.larger[... peut-on reconstruire<br> un signal $x$?]

---

class: middle

.width-90[![](figures/setup.svg)]

---

background-image: url(./figures/weather-forecast.png)
background-size: cover
class: middle, center

---

class: middle

.center.width-80[![](figures/WeatherModel.png)]

.center[

$x$ = état météorologique

]

---

class: middle

.grid[
.kol-1-2[

<br><br><br><br><br><br>

.bold[Gencast] (Google Deepmind) est un modèle de diffusion de type image-to-image pour la prévision météorologique du prochain état $x\_{t+1}$ à partir de l'état actuel $x\_t$.
]
.kol-1-2[
.center.width-100[![](figures/gencast.jpg)]
]
]

---

class: middle, center, black-slide

.center.width-100[![](figures/satellite.gif)]

Comment les conditions initiales $x\_0$ sont-elles connues?<br> Seules des observations partielles $y$ sont disponibles!

---

class: middle

.center.width-100[![](figures/dynamical.svg)]

L'estimation de trajectoires plausibles $x\_{1:L}$ à partir d'observations bruitées $y$ est un problème d'.bold[assimilation de données].

---

class: middle

.avatars[![](figures/frozet.jpg)![](figures/gilles.jpg)]

.center.width-100[![](figures/sda.svg)]

Notre approche (SDA):
- Construire un modèle de diffusion pour générer des trajectoires $x\_{1:L}$.
- Conditionner la génération à des observations bruitées $y$.

---

class: middle

.avatars[![](figures/frozet.jpg)![](figures/gilles.jpg)]

.center.width-100[![](figures/sda1-0.png)]

.center[Exemple de trajectoires $x\_{1:L}$ générées à partir d'observations bruitées $y$.]

---

class: middle
count: false

.avatars[![](figures/frozet.jpg)![](figures/gilles.jpg)]

.center.width-100[![](figures/sda1.png)]

.center[Exemple de trajectoires $x\_{1:L}$ générées à partir d'observations bruitées $y$.]

---

class: middle

.center.width-75[![](figures/ok.png)]

.center[SDA peut assimiler des observations météorologiques bruitées.<br>
$x$ = état météorologique régional, $y$ = observations ponctuelles]

.footnote[Credits: [Manshausen et al](https://arxiv.org/abs/2406.16947), 2024.]

---

class: middle, black-slide

.avatars[![](figures/faces/gerome.jpg)![](figures/faces/frozet.jpg)![](figures/faces/victor.jpg)![](figures/faces/omer.jpg)![](figures/faces/sacha.jpg)![](figures/faces/mathias.jpg)![](figures/faces/elise.jpg)![](figures/faces/gilles.jpg)]

.center.width-40[![](figures/earth.jpg)]

À l'échelle de la Terre (pour une résolution de 0.25°), .bold[une trajectoire $x\_{1:L}$ contient trop de variables].
- $1440 \times 720 \times 6 \times 37 \times 24 \times 14 = 77 \times 10^9$ variables pour 14 jours.
- Un modèle de diffusion pour la Terre nécessiterait .bold[des ressources colossales].

---

class: middle

.avatars[![](figures/faces/gerome.jpg)![](figures/faces/frozet.jpg)![](figures/faces/victor.jpg)![](figures/faces/omer.jpg)![](figures/faces/sacha.jpg)![](figures/faces/mathias.jpg)![](figures/faces/elise.jpg)![](figures/faces/gilles.jpg)]

<br>
.grid[
.kol-3-5[<br><br>
.center.width-100[![](figures/ae.png)]
]
.kol-2-5[
.center.width-100[![](figures/dit.png)]
]
]
Notre approche (en cours): 
- Un .bold[autoencoder] pour encoder et décoder des trajectoires $x\_{1:L}$ vers un espace latent de dimension réduite.
- Un .bold[video diffusion model] (basé sur une variante spatiotemporelle du DiT) produisant des trajectoires $z_{1:L}$ latentes.

---

class: middle, center, black-slide

.width-24[![](figures/gifs/latent_0.gif)] .width-24[![](figures/gifs/latent_3.gif)] .width-24[![](figures/gifs/latent_4.gif)] .width-24[![](figures/gifs/latent_5.gif)] 
.width-24[![](figures/gifs/latent_6.gif)] .width-24[![](figures/gifs/latent_10.gif)] .width-24[![](figures/gifs/latent_14.gif)] .width-24[![](figures/gifs/latent_18.gif)]
.width-24[![](figures/gifs/latent_19.gif)] .width-24[![](figures/gifs/latent_23.gif)] .width-24[![](figures/gifs/latent_27.gif)] .width-24[![](figures/gifs/latent_31.gif)]
.width-24[![](figures/gifs/latent_32.gif)] .width-24[![](figures/gifs/latent_36.gif)] .width-24[![](figures/gifs/latent_40.gif)] .width-24[![](figures/gifs/latent_44.gif)]
.width-24[![](figures/gifs/latent_45.gif)] .width-24[![](figures/gifs/latent_49.gif)] .width-24[![](figures/gifs/latent_53.gif)] .width-24[![](figures/gifs/latent_57.gif)]
.width-24[![](figures/gifs/latent_58.gif)] .width-24[![](figures/gifs/latent_62.gif)] .width-24[![](figures/gifs/latent_66.gif)] .width-24[![](figures/gifs/latent_70.gif)]


---

class: middle

.center.width-10[![](figures/icons/globe-terrestre.png)]

## Conclusions

- Les modèles de diffusion sont pas que des générateurs d'images.
- Ils sont un outil pour traiter des problèmes inverses de haute dimension en science.

---

class: middle

.center.width-10[![](figures/icons/high-five.png)]

.center[

.width-20.circle[![](figures/faces/gerome.jpg)] .width-20.circle[![](figures/faces/frozet.jpg)] .width-20.circle[![](figures/faces/victor.jpg)] .width-20.circle[![](figures/faces/omer.jpg)] .width-20.circle[![](figures/faces/sacha.jpg)] .width-20.circle[![](figures/faces/mathias.jpg)] .width-20.circle[![](figures/faces/elise.jpg)]

(Gérome, François, Victor, Omer, Sacha, Matthias, Elise)

]

