Your First Task Script
----------------------

```eval_rst
.. contents:: Table of Contents
    :local:
```

### Task Script : quelques bases

Un Task Script (script de Tâche) est un script autonome qui peut soit être exécuté in-game avec la [commande /ex](/guides/first-steps/ex-command), ou avec la commande `run` ou `inject` dans un autre script.

Les Task Scripts éxécutent toutes les commandes Denizen qu'ils contiennent. Ce type de script peut être très simple comme très élaboré selon selon ses instructions et peut également appeler d'autres scripts à s'exécuter. Les scripts de tâche sont très utiles pour créer des tâches logiques, répétives ou ponctuelles : comme la génération de dialogues dans le chat, gestion d'effets de particules, création d'un contenu aléatoire...

D'une certaine façon, les scripts de tâches sont les briques éléments qui peuvent constituer la plupart des scripts sur votre serveur.

### Task Script : Syntaxe

Voici un exemple basique d'un script de tâche.

```dscript_green
tache_exemple:
    type: task
    script:
    - narrate "Ceci est un script de tâche !"
```

Ce script affichera une ligne de chat avec pour texte: `Ceci est un script de tâche !` au joueur attaché au script. Si vous utilisez la commande `/ex` pour éxécuter ce script - spécifiquement, en utilisant `/ex run tache_exemple` dans le jeu, *vous* serez le joueur attaché au script.

NB : Cet échantillon de script est contouré en vert : cela signifie qu'il est fonctionnel et qu'il peut être copié/collé pour vous en servir sur votre serveur. Plus bas, se trouve un script contouré en bleu, signifiant qu'il s'agit d'un bon exemple de script, mais dont il manque certains composants afin qu'il soit fonctionnel et utilisable sur votre serveur. Vous verrez également des scripts contourés en rouge, indiquant des exemples de scripts à ne pas utiliser et illustrant des erreurs à ne *pas* faire. Pour plus d'informations sur les échantillons de script que vous trouvez sur ce guide, rendez-vous sur [This Guide - Sample Scripts](/guides/this-guide/sample-scripts).

### Construire son premier script de tâche dans VS Code

Précédement, vous avez appris [Comment installer VS Code](/guides/first-steps/script-editor), l'éditeur que nous recommandons lorsque vous éditez vos scripts Denizen.

#### Créer le Fichier

Pour créer votre premier script de tâche, commencez par ouvrir dossier `Denizen` se trouvant dans vos plugins, puis d'ouvrir dans VS Code le dossier `scripts` qui s'y trouve.

![](https://i.alexgoodwin.media/i/denizen_guide/548218.png)
![](https://i.alexgoodwin.media/i/denizen_guide/d2810b.png)

D'ici, faîtes un clique droit sur votre dossier `scripts` dans l'exploreur puis cliquez sur "New File" pour créer un nouveau fichier texte, qui contiendra votre script.

![](https://i.alexgoodwin.media/i/denizen_guide/5fad5b.png)

Donner le nom que vous souhaitez à ce fichier, tout en ajoutant l'extension `.dsc` - l'extension officielle des scripts Denizen.

![](https://i.alexgoodwin.media/i/denizen_guide/e3ec76.png)

Nous allons pouvoir commencer à scripter.

#### Éditer le Script

Commençons avec le coeur du script:

```dscript_blue
ma_premiere_tache:
    type: task
    script:
    - narrate (texte)
```

Cet exemple peut sembler familier : il est trés similaire à l'exemple vu précédemment.

#### Noms de Script

Le nom du script est ici `ma_premiere_tache`. Il est situé au premier niveau de l'indentation du script <span class="parens">(cela signifie qu'il n'y a aucun espace au début de la ligne, là où toutes les autres lignes démarrent avec *au moins* 4 espaces d'indentation au début de chaque ligne)</span>. Chaque premier niveau d'indentation constitue un script. Voici un exemple de fichier pouvant contenir deux scripts:

```dscript_green
ma_premiere_tache:
    type: task
    script:
    - narrate "C'est ma premiére tâche !"

ma_seconde_tache:
    type: task
    script:
    - narrate "C'est ma seconde tâche !"
```

Ce court exemple montre qu'un fichier peut contenir plusieurs scripts. `ma_premiere_tache` et `ma_seconde_tache` sont deux scripts différents qui n'ont aucun lieu entre eux, sinon qu'ils soient dans le même fichier.

Par ailleurs, il est important de noter que les *noms de script* et que les *noms de fichiers* sont deux choses différentes. `ma_premiere_tache` et `ma_seconde_tache` peuvent être dans un même fichier intitulé `mes_premiers_scripts.dsc`. L'important, dans Denizen, est le nom du script <span class="parens">(comme `ma_premiere_tache`)</span>, le nom du fichier <span class="parens">(`mes_premiers_scripts.dsc`)</span> n'a aucune importance fonctionnelle dans Denizen et dépend simplement de la façon dont vous souhatez organiser vos scripts.

#### Types de Scripts

Sous le nom du script - au second niveau d'indentation - on peut voir une clé `type`.

La clé `type` est l'endroit où vous indiquez le `type` de script Denizen que vous créez. Ici, on édite script de type `task` (tâche). Il y également des scripts de type  `world`, de type `item` ou encore de type `inventory` et beaucoup d'autres qui remplissent chacun un un rôle précis. Nous y reviendrons plus tard : concentrons-nous sur les scripts `task`. Vous apprendrez les différences entre ces autres script au cours de votre apprentissage, et vous pourrez trouver des explications sommaires sur chacun d'entre eux dans la documentation générales Denizen <span class="parens">(en englais)</span> sur la page [language explanation](https://one.denizenscript.com/denizen/lngs/container).

Votre `type: task` doit se trouver au second niveau d'indentation, c'est à dire 4 espaces après le début de votre ligne <span class="parens">(**entrer** pour faire un saut de ligne, puis **tab** pour passer un niveau d'indentation. VS Code conventira votre tab en 4 espaces. Chaque nouveau saut de ligne vous donnera automatiquement l'indentation précédente, jusqu'à ce que vous retirez manuellement des espaces ou diminuez votre indentation)</span> sous le nom de votre script, comme-çi:

```dscript_blue
ma_premiere_tache:
    type: task
```

#### Commandes de Script

Sous la clé `type` vous pouvez pouvez voir une nouvelle clé : `script`. Pour un Task Script, la clé `script` est l'endroit où vous rédigez le contenu de votre script, c'est à dire l'ensemble des instructions qui seront éxécutées par Denizen. Les autres types de script utilisent d'autres clés et nous y reviendrons plus tard. La majeure partie de votre travail s'effectuera sous cette clé `script` dans les Task Scripts.

Autre exemple de script:

```dscript_green
ma_premiere_tache:
    type: task
    script:
    - narrate "Ceci est un exemple de script"
    - narrate "Félicitations ! Vous avez écrit votre premier script !"
```

Il est important de noter que le texte que l'on veut afficher - `Ceci est un exemple de script` - est délimité par des `""` guillemets. Parce que le message que nous voulons affichier contient des ` ` espaces, on utilise des guillemets afin que la commande ne reconnait ce qu'il y a entre ces guillements comme un seul argument. Certaines commandes Denizen peuvent avoir des arguments séparés par des ` ` espaces. Par exemple, `run un deux trois` a comme arguments `un`, `deux`, et `trois`, tandis que `run "un deux trois"` n'a qu'un seulement argument : `un deux trois`.

### Produit fini

Arrivé ici, vous devriez avoir un script de tâche prêt à être exécuter ! C'est parti ! Utilisez `/ex reload` in-game pour rechar, then use thegez vos scripts afin de prendre en compte vos modifications puis utilisez `/ex run (VotreNomDeScript)` pour exécuter le script in-game. Pour l'exemple ci-dessus, utilisez `/ex run ma_premiere_tache`.

Si vous voyez dans le Chat le texte que vous avez inséré avec la commande `narrate`, vous avez écrit et exécuté votre premier script avec succès. Félicitations !

![](https://i.alexgoodwin.media/i/denizen_guide/831e94.png)

### Pour aller plus loin

Pour aller plus loin, tout en gardant à l'esprit qu'on utilise la commande `run` via `/ex` in-game, <span class="parens">(la commande `/ex` une commande in-game qui ne sert qu'à tester rapidement une commande Denizen. Souvent, elle n'est utilisé qu'afin de débugger des scripts ou des scripts précis)</span>, prenons un exemple un exemple qui fait un peu plus que ce qu'on a vu précédemment.

Vous pouvez utiliser un task script afin d'éxecuter un autre task script !  Exemple:

```dscript_green
ma_premiere_tache:
    type: task
    script:
    - narrate "C'est un script de tâche valide !"
    - narrate "Bravo, vous avez écrit votre premier script de tâche !"
    - run ma_seconde_tache

ma_seconde_tache:
    type: task
    script:
    - narrate "C'est votre second script de tâche !"
```

Dans cet exemple, `ma_premiere_tache` va exécuter `ma_seconde_tache`, vous verrez ainsi 3 lignes de Chat lors de l'éxécution de votre premier script. Il s'agit d'un exemple très basique, mais qui peut être étendu avec d'autres commandes, dans d'autres scripts, avec d'autres façons !

