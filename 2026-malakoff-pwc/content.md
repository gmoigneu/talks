# Adapter l'ingénierie aux agents IA

**Événement :** Malakoff · PwC, 2026
**Format :** 30 min de talk + 15 min de questions
**Public :** managers d'ingénierie, peu familiers avec le détail technique
**Angle :** retour d'expérience. Comment l'IA change l'organisation de l'ingénierie, pas
comment elle écrit du code.
**Langue :** français

## Thèse

Le goulot n'est plus l'écriture du code. Le goulot, c'est la clarté du travail.

Donner des outils IA aux développeurs ne suffit pas. L'IA peut accélérer des individus,
mais cette vitesse locale crée des îlots, déplace les goulots vers la revue, l'intégration
et la coordination, puis expose ce que l'organisation n'a pas encore formulé.

Le rôle du manager d'ingénierie change : il ne manage plus seulement des personnes. Il
manage du contexte, des workflows et des preuves. Pour passer de la vitesse individuelle
à la vélocité d'organisation, il faut rendre le travail spécifié, vérifiable et partagé.

## Transformation recherchée

**Avant :** les managers ont peur du changement et pensent que fournir des outils suffit.

**Après :** ils comprennent que l'adoption de l'IA demande de repenser les rôles, les
workflows et le niveau de spécification attendu de toute l'équipe.

## Architecture narrative

- **Conclusion d'abord :** le problème n'est plus de produire du code, mais de clarifier
  le travail.
- **Duarte Sparkline :** alternance entre "ce qui se passe" et "ce qui pourrait se passer".
- **Three-Act Structure :** piège individuel, rôle collectif, système d'organisation.
- **MECE :** contexte, workflows, preuves.
- **Fichtean Curve légère :** les tensions montent des îlots à l'agent qui triche.
- **Nouvel équilibre :** une équipe augmentée sait spécifier, vérifier et partager son
  travail.

## Les trois phrases d'ancrage

1. **Le goulot n'est plus l'écriture du code. Le goulot, c'est la clarté du travail.**
2. **Demain, le manager d'ingénierie ne manage pas seulement des personnes. Il manage du
   contexte, des workflows et des preuves.**
3. **Ce qui ne peut pas être spécifié, vérifié et partagé ne passera pas à l'échelle avec
   l'IA.**

## Slide plan resserré

### Slide 1 · Titre
**Message :** Adapter l'ingénierie aux agents IA.
**Note orateur :** Poser le cadre : 30 minutes, retour d'expérience, pas une démo technique.

### Slide 2 · Qui je suis, et l'équipe Upsun
**Message :** Guillaume Moigneu. Je développe des applications web depuis 1998.
**Points clés :**
- Agences, clients finaux, puis Upsun depuis dix ans.
- Obsession : optimiser mon travail, les projets et la façon dont les équipes livrent.
- Depuis deux ans : travail en profondeur sur les pratiques d'ingénierie avec l'IA.
- Chez Upsun : 3 produits, 110 personnes côté ingénierie et produit.
- Rôle actuel : Field CTO, surveiller et tester les nouvelles solutions, puis voir comment
  l'ingénierie peut en bénéficier.
**Note orateur :** Ancrer le talk dans mon contexte : je développe des applications web depuis
1998, j'ai travaillé en agence, chez des clients finaux, puis chez Upsun depuis dix ans. Je
suis obsédé par l'optimisation de mon travail et des projets. Depuis deux ans, je travaille en
profondeur sur l'IA. Mon rôle aujourd'hui : Field CTO, surveiller et tester les nouvelles
solutions, puis voir comment l'ingénierie peut en bénéficier, dans une organisation de 110
personnes côté ingénierie et produit, qui livre trois produits.

## ACT I · Le piège : l'outil ne fait pas l'organisation

### Slide 3 · L'essentiel
**Message :** Le goulot n'est plus l'écriture du code. Le goulot, c'est la clarté du travail.
**Rôle narratif :** donner la conclusion dès le début.
**Note orateur :** L'IA change moins la quantité de code que l'exigence de clarté autour du
travail. Les managers doivent écouter la suite comme un sujet d'organisation, pas d'outillage.

### Slide 4 · Ce qui se passe : les individus accélèrent
**Message :** Certains avancent déjà beaucoup plus vite que le reste du système.
**Points clés :**
- Un développeur adopte ses outils, ses prompts, son contexte personnel.
- La direction pense avoir "donné l'accès à l'IA".
- Une vitesse locale apparaît, mais le reste du système ne change pas.
**Note orateur :** La vraie histoire n'est pas un individu exceptionnel. C'est qu'augmenter des
personnes avec des outils ne suffit pas si le rôle et le workflow restent identiques.

### Slide 5 · Ce qui pourrait se passer : convertir la vitesse en vélocité
**Message :** La vitesse d'un développeur n'est pas la vélocité d'une organisation.
**Points clés :**
- Le manager ne se limite plus à débloquer la production individuelle.
- Il convertit aussi des pratiques isolées en capacité partagée.
- La question devient : qu'est-ce qui doit être clair pour que toute l'équipe avance ?
**Note orateur :** Premier pivot : on sort du débat "quel outil ?" pour aller vers "quel
système de travail ?".

### Slide 6 · La carte de maturité
**Message :** Huit niveaux, mais trois mouvements : l'individu, l'équipe, l'organisation.
**Points clés :**
- **Individu :** le vide, la dérive, les îlots.
- **Équipe :** standardiser, repenser le workflow, faire des agents des coéquipiers.
- **Organisation :** Agent Factory, puis autonomie sur déclencheurs.
**Note orateur :** Ne pas demander au public de mémoriser les huit niveaux. Les raconter comme
une carte : les usages personnels créent des îlots, puis l'équipe doit standardiser et repenser
le workflow, avant de viser une organisation plus autonome. Poser le curseur sur les îlots pour
préparer la slide suivante.

### Slide 7 · Ce qui se passe : les îlots créent les nouveaux goulots
**Message :** Deux équipes, même boîte, deux rythmes. Et des frictions partout.
**Points clés :**
- Revues en attente, intégration plus difficile, décisions implicites.
- Frustration côté équipe rapide, ressentiment côté équipe qui décroche.
- Les délais s'accumulent là où personne n'a repensé le workflow.
**Note orateur :** Nommer le coût humain. Les îlots ne sont pas seulement inefficaces, ils
abîment la confiance entre équipes.

## ACT II · Le nouveau rôle : manager le contexte, le workflow et les preuves

### Slide 8 · Ce qui pourrait se passer : spécifier pour franchir les silos
**Message :** Spécifier n'est plus de la paperasse. C'est l'interface entre équipes.
**Points clés :**
- Spécifier le travail : résultat attendu, contraintes, non-objectifs.
- Spécifier les responsabilités : qui décide, qui valide, qui maintient.
- Spécifier les interfaces : ce que chaque équipe peut consommer sans réunion.
**Note orateur :** Le silo n'est pas seulement un organigramme. C'est du contexte non écrit.

### Slide 9 · Standardiser pour aligner
**Message :** La standardisation fait passer l'IA en capacité financée, pas en avantage privé.
**Points clés :**
- Alignement : mêmes attentes et mêmes règles de travail.
- Vélocité : pratiques réutilisables au-delà d'une équipe.
- Coût et sécurité : SSO, audit, accès, gouvernance.
**Note orateur :** La standardisation n'est pas une manie de contrôle. C'est ce qui permet à
l'organisation de financer et sécuriser l'usage de l'IA.

### Slide 10 · Le nouveau rôle du manager
**Message :** Demain, le manager d'ingénierie ne manage pas seulement des personnes. Il manage
du contexte, des workflows et des preuves.
**Points clés :**
- Les managers deviennent coaches, architectes de workflow et propriétaires de qualité.
- Une part importante du travail commence avant le code : intention, contraintes, preuve
  attendue.
**Note orateur :** Phrase d'ancrage numéro deux. Le manager devient le designer du système de
travail, pas seulement le responsable des personnes.

### Slide 11 · Une promotion, pas une menace
**Message :** Les développeurs passent de l'exécution au jugement d'ingénierie.
**Points clés :**
- Avant : écrire le code, relire le diff ligne à ligne, porter l'exécution.
- Avec agents : définir l'intention, poser les contraintes, demander la preuve.
- Programmer devient davantage la conséquence d'un travail d'ingénierie bien formulé.
**Note orateur :** Répondre à la peur de face. Ce n'est pas une dévalorisation, c'est une
promotion du rôle d'ingénierie.

### Slide 12 · Le workflow change
**Message :** Un ticket vague risque de produire du code vague, plus vite.
**Points clés :**
- Avant : ticket, code, revue ligne à ligne.
- Avec agents : spécification, génération, contrôles, inspection, validation humaine.
- Le manager doit rendre ce chemin explicite et répétable.
**Note orateur :** L'IA ne corrige pas le flou toute seule. Elle peut le reproduire plus vite.

### Slide 13 · Ce qui se passe : plus de contexte peut empirer le résultat
**Message :** Plus de contenu n'est pas un meilleur contexte.
**Points clés :**
- Les agents peuvent produire beaucoup de docs, tests et instructions.
- Trop de contexte devient du bruit et dilue les règles importantes.
- La discipline n'est pas d'écrire plus, mais de curer ce qui compte.
**Note orateur :** Mériter chaque ligne. Les modèles savent produire du code plausible ; ce
qu'ils ignorent, ce sont vos contraintes spécifiques.

## ACT III · Le système : passer à l'échelle sans baisser la barre

### Slide 14 · Ce qui se passe : l'agent peut tricher
**Message :** Un agent a buté sur un test. Il l'a "corrigé" en modifiant le test.
**Points clés :**
- Puis il a annoncé : vert.
- On ne fait pas confiance à un succès auto-déclaré.
- La tension n'est plus "peut-il produire ?", mais "peut-on croire le résultat ?"
**Note orateur :** Histoire simple et mémorable. Tout le monde comprend la triche à l'examen.

### Slide 15 · Ce qui pourrait se passer : séparer vérification et validation
**Message :** La vérification s'automatise. La validation reste humaine.
**Points clés :**
- Vérification : tests, types, contrôles, évaluations, conformité à la
  spécification.
- Validation : intention, comportement réel, arbitrage métier et technique.
- Les managers doivent posséder la barre de qualité.
**Note orateur :** Automatiser une partie de la vérification libère du temps pour le jugement.
Elle ne le remplace pas.

### Slide 16 · Le mandat du lundi matin
**Message :** Ce qui ne peut pas être spécifié, vérifié et partagé ne passera pas à l'échelle
avec l'IA.
**Points clés :**
- **Contexte partagé :** sortir la connaissance des têtes.
- **Workflows partagés :** rendre le passage de l'idée à la fusion observable.
- **Preuves partagées :** automatiser ce qui peut l'être, assumer le jugement humain.
**Note orateur :** C'est le take-away opérationnel. Pas besoin de courir après l'usine autonome :
il faut d'abord tuer les îlots.

### Slide 17 · Nouvel équilibre
**Message :** Une équipe augmentée n'est pas seulement une équipe où chacun utilise un agent.
**Points clés :**
- C'est une équipe dont le travail est assez clair pour être accéléré sans perdre son
  intention.
- C'est une équipe dont les standards vivent davantage dans le système, moins seulement
  dans les têtes.
- C'est une équipe où l'IA aide à faire passer la clarté à l'échelle, pas le chaos.
**Note orateur :** Clore la transformation émotionnelle : on passe de la peur à un rôle plus net.

### Slide 18 · Dispatch et questions
**Message :** Dispatch est une réponse logique à ces problèmes : agents partagés, workflows
gouvernés, contexte d'organisation, coût et preuves attachées au travail.
**Points clés :**
- Agents partagés sur infrastructure commune, pas sur des postes individuels.
- Workflow comme primitive de gouvernance.
- Contexte et preuves qui peuvent s'améliorer à chaque exécution.
- Coût par workflow, pas seulement par siège.
**Note orateur :** Ne pas en faire un argumentaire commercial. Dispatch arrive comme
conséquence des problèmes mentionnés. Rester sur cette slide pendant les 15 minutes de
questions.

## Phrase finale

**Avec l'IA, votre organisation ne passe pas à l'échelle avec plus de code ; elle passe à
l'échelle avec plus de clarté.**
