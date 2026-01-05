# **Lisibilité**

1. # **Origine de la lisibilité aux Etats-Unis**

La lisibilité est un concept qui s’est principalement développé aux débuts du XXe siècle avec l’essor de la presse papier, en effet, il y avait des impératifs à cette époque de rendre les articles de journaux le plus accessible possible. Par conséquent, la lisibilité du contenu était extrêmement importante, et c’est de cette période que des auteurs comme (Dale & Chall, 1948\) ont proposé plusieurs indices de lisibilité pour mesurer la facilité de lecture d’un texte. A cette époque, le concept de complexité est encore très peu formalisé, et une grande partie des indices que l’on appelle aujourd’hui de la complexité sont à cette époque, de la lisibilité, mais de façon plus généraliste, notamment la longueur des phrases et des mots. Les modèles ne s’intéressent pas encore aux dépendances, pas aux descripteurs, aux structures de phrases, il ne s’agit que de regarder le nombre de mots/syllabes dans une phrase, mais également sa mise en page, sa mise en forme, des éléments assez peu linguistiques et davantage d’aspect typographique.

2. # **Arrivée du concept en France (années 1950–1970)**

En France, c’est un concept qui est beaucoup plus tardif, il se généralise à partir des années 50-70, avec (De Landsheere, 1963\) qui propose des méthodes concrètes  de lisibilité notamment ;

* La longueur des phrases, strictement en mots.  
*  La complexité lexicale (C’est-à-dire les aspects de rareté, de fréquence, de longueur)  
* Le test de closure (Landsheere, 1973), visant à mesurer la lisibilité d’un texte en évaluant avec la capacité du lecteur à reconstruire du sens lorsque certains éléments textuels sont omis.

Donc dès 1963, il y a une déjà imbrication entre ce qu’est la lisibilité et la complexité qui émerge. En effet, Landsheere dit que l’on ne peut pas mesurer la lisibilité sans mesurer la compréhension d’un texte. Et c’est sur ce concept de la compréhension que Landsheere (1963) appuie sur argumentation en se basant essentiellement sur deux éléments particulièrement pertinents pour la complexité ;

* La structure syntaxique est pour lui fondamentale, il insiste l’idée que l’expérience de lecture d’un individu dépend énormément de ses connaissances et de sa capacité à déconstruire les phrases, pour conserver une cohésion textuelle.  
* Et le second aspect est davantage psycholinguistique, car d’après-lui, les mesures obtenues insistent énormément sur une « psychologie de la lecture » autrement dit les variations de lecture des individus en condition réelle, telles que le temps de lecture.

Nombre de ses idées ont ensuite été appliquées à la didactique, notamment pour adapter les textes aux élèves en fonction de leur niveau. Néanmoins, Morissette explique tout de même que certains éléments de sa théorie sont maintenant dépassés (Morissette, 1995). De plus, bien que le concept de lisibilité ait beaucoup évolué avec l’informatique, les pôles de lisibilité que met en exergue Jean-Yves Boyer (1992), même s’ils sont dépassés, servent également de référence pour les aspects définitoire de la lisibilité dans son acception, en particulier le facteur lecteur, autrement dit, le rapport qu’à le lecteur avec ce qu’il est en train de lire, et comment la lisibilité du texte l’influence dans la compréhension et la motivation qu’il a de continuer la lecture.

3. # **L’essor du TAL : Les méthodes quantitatives**

C’est dans le TAL que la lisibilité prend son ampleur, avec l’essor des méthodes quantitatives, elle devient davantage liée à des modèles de prédictions de difficulté de lecture. Si historiquement, comme ça a été dit précédemment, il s’agissait plutôt de mesures simples, comme la longueur des phrases, aujourd’hui, les approches de la lisibilité utilisent plutôt de mesures linguistiques qui se superposent sur différentes couches d’analyse de texte conjointes, pour les intégrer dans des modèles multi-dimensionnels. Cette superposition de l’analyse permet de traiter l’information sur plusieurs couches indépendantes les unes des autres pour obtenir des résultats pertinents (Aissa et al., 2025).

4. # **Méthodologie d’application de la lisibilité**

C’est le cas notamment de CamemBERT, qui est un transformer de type neuronal francophone basé lui-même sur BERT. Il sert, en tout cas chez Aissa et al. 2025, à faire des prédictions implicites d’indices de complexité. Aissa et al. (2025) ont donc enrichi le modèle avec des paramètres syntaxiques et l’ont entraîné en utilisant des corpus annotés (généralement plutôt pour des enfants, mais produit ici pour des adultes peu alphabétisés) selon une annotation dite locale (en segments, en phrases, en passages) qui permet à CamemBERT de localiser les zones pertinentes du texte, et en particulier les zones difficiles. Cette annotation (dont le but est de donner un jugement humain de type « cette phrase est plus ou moins difficile ») sert donc à l’analyse de complexité notamment de surface (Lu, 2010\) tels que la longueur des phrases, rareté des mots, ou la distance moyenne des dépendances, et à partir de ceci, lorsque l’on a mesure de complexité de la phrase, alors une mesure de la lisibilité devient possible.

1. # **Exemple de calcul d’indice de complexité** 

a)  «Un biais modifie subrepticement notre interprétation», devrait donner ceci ;  
(1)    Longueur de la phrase : 6        	  
(2)    Nombre de mots rares : 1  
(3)    Distances des dépendances : 7/6 \= \~1.20  
(a)    Un biais : 1+1 (« biais » lié à racine, « un » lié à biais)  
(b)    Modifie : 0 (mot-racine)  
(c)     Subrepticement : 1 (lié à au mot-racine)  
(d)    Notre : 1 (lié à interprétation)  
(e)    Interprétation : 3 (lié au mot-racine)

Cet exemple illustre la manière avec laquelle les indices de complexité syntaxique interagissent avec la lisibilité pour la mesurer, une fois ces données obtenues sur chacune des phrases d’un corpus donné, il est alors nécessaire de compiler l’entièreté des phrases annotées dans des outils d’analyse tels que des modèles statistiques ou neuronaux (CamemBERT), pour que ledit modèle, puisse automatiquement produire l’analyse que nous avons proposé ci-dessus pour l’ensemble du corpus. (Aissa et al., 2025\)

2. # **Exemple de mesure de lisibilité**

Par exemple, avec un corpus de 10 phrases, et avec un modèle qui a déjà été entraîné avec un corpus de difficulté des phrases, et qui a déjà produit l’analyse des trois indices ci-dessus (Longueur, rareté, dépendance, et autant qu’on le souhaite) il suffira alors de calculer \[somme totale\] / \[nombre de phrases\]. Pour simplifier l’interprétation, on s’appuiera sur un indice de difficulté de phrases entre 1 et 5\. et les données sont les suivantes ;

·         \[1,1,2,4,5,3,4,2,3,4\] /10 \= 2,9  

·         Soit è \[somme totale des phrases triées par difficulté\] / \[nombre total de phrases\]

Ce qui donne une mesure de lisibilité qui est égale à 2,9/5. De quoi il est alors possible de conclure, que si CamemBERT avait produit cette analyse[^1], il aurait déterminé qu’il s’agit d’un texte qui est de difficulté moyenne, si le niveau du lecteur correspond exactement à son corpus d'entraînement. (Lee et al., 2021)[^2]

5. # **Interdépendance entre lisibilité et complexité**

L’aspect assez technique de la question ayant été abordé, l’analyse à s’en faire est que la lisibilité est extrêmement intéressante pour pouvoir analyser un corpus. De plus, il est rapidement observable que la complexité et la lisibilité sont absolument interdépendants dans une analyse quantitative de corpus. En effet, il est bien plus aisé d’analyser la complexité syntaxique d’un texte, mais pour appliquer la mesure de lisibilité, il y a besoin de la complexité. Par conséquent cette dernière mesure plutôt des propriétés marquées linguistiquement, et qui vont rendre une phrase plus ou moins coûteuse/difficile en analyse (Lu, 2010), tandis que la lisibilité a plutôt pour but de proposer une interprétation de la difficulté globale d’un texte, du point de vue des lecteurs (qui est crucial en didactique, car, la difficulté n’est pas interprétée de la même façon selon le texte, quand on a dix ans, que quand on en soixante, et ceci permet d’avoir des niveaux de difficulté concrets.).

6. #    **L’usage traditionnel de la lisibilité** 

Traditionnellement, c’est une mesure véritablement statistique des textes, avec une moyenne des indices de complexité, et des données croisées pour les faire ressortir, et plus les indices y sont élevés, plus c’est jugé difficile, or, cette analyse pose problème, dès lors qu’on essaie de l’appliquer à un modèle TAL, ça n’offre suffisamment de précision, mais c’est encore plus ou moins utilisé en typologie pour trier les différents textes  (Revaz & Bronckart, 1988), par conséquent, c’est une méthode qui, bien que dépassée techniquement, reste encore valide lorsqu’il n’y a pas besoin d’une précision élevée sur le degré de probabilité d’une difficulté.

7. #    **Son rôle central en didactique**

Tout comme le concept de complexité, la lisibilité est primordiale en didactique, il est difficilement concevable à l’heure actuelle, de pouvoir créer du contenu pédagogique de qualité sans utiliser des mesures de lisibilité (François, 2022)., c’est pourquoi les études actuelles cherchent plutôt à complexifier les mesures, en utilisant notamment les « transformers » et les modèles dits de  « supervision » pour maximiser les taux de prédiction et leur efficacité (François & Fairon, 2013), un autre aspect didactique à concevoir est que, et qui a été brièvement parcouru à travers la méthodologie, c’est qu’une mesure de lisibilité est issue d’un corpus humain de traitement de difficulté des phrases par subjectivité des individus, ce qui est très important pour la validité de l’annotation, il faut donc trouver des critères qui vont donner une subjectivité similaire à celui du lecteur, et le meilleur critère envisageable, c’est l’âge, et le niveau de langue, or, on ne peut pas utiliser un corpus ayant été annoté autour de la subjectivité des lecteurs enfants, avec des adultes ou d’autres profils, il faut nécessairement refaire un corpus pour chaque cible, ce qui est un frein considérable pour les aspects d’application méthodologique (Aissa et al., 2025). 

8. #     **Limites du concept de lisibilité**

Dans un premier temps, il est important de soulever un grand frein à l’acception généralisée d’un tel concept, il est extrêmement hermétique et difficile à appréhender, sa définition typique autrement dit « mesure de facilitation de lecture des textes » est vraiment trop général, et ça ne rend finalement pas tellement compte de ce qui se fait réellement en TAL sur la question : En effet, cette acception donne à croire qu’il s’agit davantage d’une analyse textuelle, quand il s’agit plutôt en réalité d’une analyse subjective, la lisibilité dépend des lecteurs, et en particulier ceux qui sont responsable de l’annotation en termes difficulté des phrases. De plus, c’est généralement un phénomène associé à la pédagogie pour enfants, et il y a finalement peu de contenu pour les apprenants L2 dans un milieu non scolaire, ce qui en limite énormément l’usage pour l’humanité numérique en général, en effet, ce genre d’outils ne sont généralement pas à destination de personnes peu alphabétisés, alors que dans l’absolu, c’est bien eux qui en auraient le plus besoin, et non les enfants dont la quantité de contenu adapté est très vaste(Aissa et al., 2025). De plus, un corpus de mesure de lisibilité, n’est pas géographiquement stable, on ne peut pas utiliser une mesure de lisibilité issue d’un corpus annoté pour les lecteurs enfants parisiens, et l’appliquer aux lecteurs enfants de bruxellois, ce qui est encore une fois un frein considérable(De Landsheere, 1963).

De plus, tout comme la complexité, il y a de nombreuses critiques sur son manque de rigueur linguistique, les indices de complexité utilisés, sont assez souvent les mêmes indices syntaxiques de type longueur de phrases, de dépendance, de rareté, et ceci est beaucoup trop superficiel pour donner une mesure fidèle de la lisibilité, cela permet une entrée en matière, mais pas du tout de pouvoir en avoir une interprétation fiable, en effet, il faudrait rajouter des indices de complexité sémantique, pragmatiques, interactionnels, et davantage de cohésion de texte, notamment pour des corpus à l’oral.(François & Fairon, 2012\)  
Par conséquent, bien que la lisibilité soit un concept extrêmement riche et efficace dans le bon environnement, il s’avère néanmoins que bien souvent, elle ne soit pas adaptable à d’autres lecteurs, et que ses indices de complexité qui lui servent de support ne sont généralement pas suffisamment fiables pour donner suffisamment d’information sur la lisibilité, certaines études comme François & Fairon (2012) vont jusqu’à utiliser 46 critères de lisibilité simultanément, mais les outils automatiques dépassent  rarement les quelques critères de complexité qui vont permettre une mesure de lisibilité.

9. # **Bibliographie**

Aissa, W., Bañeras-Roux, T., Vanzeveren, E., Gao, L., Wilkens, R., & François, T. (2025). Assessing French Readability for Adults with Low Literacy : A Global and Local Perspective. In C. Christodoulopoulos, T. Chakraborty, C. Rose, & V. Peng (Éds.), *Proceedings of the 2025 Conference on Empirical Methods in Natural Language Processing* (p. 20528‑20550). Association for Computational Linguistics. https://doi.org/10.18653/v1/2025.emnlp-main.1036

Boyer, J.-Y. (1992). La lisibilité. *Revue française de pédagogie*, *99*(1), 5‑14. https://doi.org/10.3406/rfp.1992.1322

Dale, E., & Chall, J. S. (1948). A Formula for Predicting Readability. *Educational Research Bulletin*, *27*(1), 11‑28.

De Landsheere, G. (1963). Pour une application des tests de lisibilite de Flesch a la langue francaise. *Travail Humain*, *26*. https://orbi.uliege.be/handle/2268/87609

François, T. (2022). Le traitement automatique du langage pour l’évaluation automatique de la difficulté lexicale en FLE. *Revue japonaise de didactique du français*, *17*(1‑2), 129‑144. https://doi.org/10.24495/rjdf.17.1-2\_129

François, T., & Fairon, C. (2012). An “AI readability” Formula for French as a Foreign Language. In J. Tsujii, J. Henderson, & M. Paşca (Éds.), *Proceedings of the 2012 Joint Conference on Empirical Methods in Natural Language Processing and Computational Natural Language Learning* (p. 466‑477). Association for Computational Linguistics. https://aclanthology.org/D12-1043/

François, T., & Fairon, C. (2013). Les apports du TAL à la lisibilité du français langue étrangère \[Contributions of NLP to the readability of French as a foreign language\]. *Traitement Automatique des Langues*, *54*(1), 171‑202.

Landsheere, G. de. (1973). *Le Test de closure. Mesure de la lisibilité et de la compréhension*. Nathan; Labor.

Lee, B. W., Jang, Y. S., & Lee, J. (2021). Pushing on Text Readability Assessment : A Transformer Meets Handcrafted Linguistic Features. *Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing*, 10669‑10686. https://doi.org/10.18653/v1/2021.emnlp-main.834

Lu, X. (2010). Automatic analysis of syntactic complexity in second language writing. *International Journal of Corpus Linguistics*, *15*(4), 474‑496. https://doi.org/10.1075/ijcl.15.4.02lu

Morissette, D. (1995). ÉVALUATION CONTINUE ET EXAMENS : PRÉCIS DE DOCIMOLOGIE. De Landsheere, Gilbert, (6 éd.). Bruxelles : Labor, 310 pages, 1992\. *Mesure et évaluation en éducation*, *17*(3), 125\. https://doi.org/10.7202/1092316ar

Revaz, F., & Bronckart, J.-P. (1988). *Mesurer la lisibilité*. https://doi.org/10.3406/rfp.1988.1435

[^1]:   Est à noter que je me suis servi de Lee et al. 2021 pour l’aspect méthodologique, de la mesure, mais les résultats sont inventés, ils n’ont aucun lien avec CamemBERT

[^2]: Voir   le 3\.