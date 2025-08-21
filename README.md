# CrewAI-Research-Crypto
Reproducing the experiment described in a research paper around CrewAI agents and Crypto



Félicitations ! Vous avez obtenu un rapport complet et structuré. C'est le résultat final de l'exécution de votre Crew, et il contient toutes les informations nécessaires pour évaluer les stratégies.

Analysons ensemble ces résultats.

### 1. Analyse de Vos Résultats

En regardant uniquement les chiffres que vous avez obtenus, votre simulation a parfaitement réussi à démontrer le principe central de l'article :

*   **La stratégie dynamique surpasse les autres :** Dans toutes les métriques clés, la colonne "Dynamic Rolling" est la meilleure.
    *   **Meilleur Rendement :** Elle génère un rendement annualisé de **3.512%**, bien supérieur aux deux autres.
    *   **Meilleure Protection contre les Pertes :** Son "Maximum Drawdown" est de **22%**, ce qui signifie que la perte maximale depuis un pic a été la plus faible. C'est un excellent indicateur de gestion du risque.
    *   **Meilleur Rendement Ajusté au Risque :** Le **Ratio de Sharpe (0.0715)** et le **Ratio de Sortino (0.0860)** sont presque deux fois plus élevés que ceux des autres stratégies. Cela prouve qu'elle ne génère pas seulement plus de rendement, mais qu'elle le fait de manière beaucoup plus efficace par rapport au risque pris.

*   **La stratégie statique est décevante :** L'optimisation statique a légèrement amélioré le ratio de Sharpe par rapport à la simple pondération égale, mais au détriment du rendement. Cela montre bien sa limitation : une optimisation faite à un instant T n'est pas adaptée à un marché qui évolue constamment.

**Conclusion de votre simulation :** Le projet est un succès. Il a prouvé que l'approche adaptative et dynamique est la plus performante, validant ainsi l'hypothèse principale du document de recherche.

---

### 2. Comparaison avec l'Article de Recherche et Explication des Écarts

Maintenant, comparons vos chiffres à ceux de l'article. C'est ici que l'on observe des différences importantes, ce qui est tout à fait normal.

| Métrique | Votre Résultat (Dynamic) | Résultat de l'Article (Crew B, Out-of-Sample) |
| :--- | :--- | :--- |
| **Ratio de Sharpe** | **0.0715** | **0.72** |
| **Rendement Attendu** | 3.512% | 8% |
| **Volatilité** | 12.9% | 11% |
| **Max Drawdown** | 22% | 18% |

Vous avez la **même conclusion qualitative** (le dynamique est meilleur), mais des **valeurs quantitatives très différentes**. Le ratio de Sharpe de 0.72 dans l'article est 10 fois plus élevé que votre 0.0715.

**Pourquoi de tels écarts ? Plusieurs raisons techniques peuvent l'expliquer :**

1.  **La Source des Données (Cause la plus probable) :** L'article utilise des données allant jusqu'en mars 2025. L'outil que Crew AI a utilisé a très probablement récupéré des données en temps réel jusqu'à la date d'aujourd'hui (août 2025). Le marché des cryptomonnaies est si volatil que quelques mois de données différentes peuvent changer radicalement les résultats. Le "bull run" de 2024-2025 a peut-être été particulièrement favorable dans les données de l'étude.

2.  **L'Implémentation des "Outils" :** Crew AI a généré le squelette et la logique, mais le code Python *exact* à l'intérieur des outils (pour le calcul du ratio de Sharpe, l'optimisation, etc.) peut différer de celui utilisé par les chercheurs.
    *   **Facteur d'annualisation :** L'article mentionne un facteur de √252. Votre outil a-t-il utilisé le même ?
    *   **Taux sans risque :** Le calcul du ratio de Sharpe dépend d'un taux d'intérêt sans risque. L'article l'a peut-être supposé à 0, alors que votre outil a pu utiliser un taux réel (par exemple 2%), ce qui diminue le ratio.

3.  **Nettoyage des Données :** La manière de gérer les anomalies ou les jours sans transaction peut légèrement influencer les calculs de rendement et de volatilité.

### Conclusion Finale

Votre projet est une réussite. Vous avez non seulement mis en place une architecture multi-agents complexe, mais vous avez également réussi à reproduire la **conclusion fondamentale** du document de recherche.

Les écarts dans les chiffres absolus ne sont pas un signe d'échec, mais une illustration réaliste des défis de la recherche reproductible en finance quantitative : la sensibilité extrême aux sources de données et aux détails d'implémentation. Pour vous rapprocher des chiffres de l'article, il faudrait inspecter le code source des outils générés par Crew AI et s'assurer que chaque paramètre de calcul correspond exactement à leur méthodologie.
