Your First Task Script
----------------------

```eval_rst
.. contents:: Table of Contents
    :local:
```

### Script de tâche : la base

Un script de tâche (Task Script) est un script autonome qui peut soit être éxécuté in-game avec la [commande /ex](/guides/first-steps/ex-command), or part la commande `run` ou `inject` dans un autre script.

Les scripts de tâche éxécutent toutes les commandes Denizen qu'ils contiennent. Ce type de script peut être très simple comme très élaboré et peut également appeler l'éxécution d'autres scripts. Les scripts de tâche sont utiles pour créer des tâches logiques, répétives ou ponctuelles : génération de lignes de dialogue, gestion d'effets de particules, création d'un contenu aléatoire...

D'une certaine façon, les scripts de tâches sont les briques éléments qui peuvent constituer la plupart des scripts sur votre serveur.

### Script de tâche : Syntaxe

Voici un exemple basique d'un script de tâche.

```dscript_green
tache_exemple:
    type: task
    script:
    - narrate "Ceci est un script de tâche !"
```

Ce script affichera une ligne de chat avec pour texte: `Ceci est un script de tâche !` au joueur attaché au script. Si vous utilisez la commande `/ex` pour éxécuter ce script - spécifiquement, en utilisant `/ex run tache_exemple` dans le jeu, *vous* serez le joueur attaché au script.

NB : Cet échantillon de script est contouré en vert. Cela signifie qu'il est fonctionnl et qu'il peut être copié/collé pour vous en servir sur votre serveur. Plus bas se trouve un script contouré en bleu, signifiant qu'il s'agit d'un bon exemple de script, mais qu'il manque certains composants afin qu'il soit fonctionnel et utilisable sur votre serveur. Vous verrez également des scripts contourés en rouge, indiquant des exemples de scripts à ne pas utiliser et illustrant des serveurs à ne *pas* faire. Pour plus d'informations sur les échantillons de script que vous trouvez sur ce guide, rendez-vous sur [This Guide - Sample Scripts](/guides/this-guide/sample-scripts).

### Construire son premier script de tâche dans VS Code

Précédement, vous avez appris [comment installer VS Code](/guides/first-steps/script-editor), l'éditeur que nous recommandons lorsque vous éditez vos scripts Denizen.

#### Créer le Fichier

Pour créer votre premier script de tâche, commencez par ouvrir dossier `Denizen` se trouvant dans vos plugins, puis d'ouvrir dans VS Code le dossier `scripts` qui s'y trouve.

![](https://i.alexgoodwin.media/i/denizen_guide/548218.png)
![](https://i.alexgoodwin.media/i/denizen_guide/d2810b.png)

D'ici, faîtes un clique droit sur votre dossier `scripts` dans l'exploreur puis cliquez sur "New File" pour créer un nouveau fichier texte, qui contiendra votre script.

![](https://i.alexgoodwin.media/i/denizen_guide/5fad5b.png)

Donner le nom que vous souhaitez à ce fichier, tout en ajoutant l'extension `.dsc` - l'extension des scripts Denizen.

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

Le nom du script est ici `ma_premiere_tache`. Il est premier niveau de l'indentation du script <span class="parens">(cela signifie qu'il n'y a aucun espace au début de la ligne, là où toutes les autres lignes démarrent avec au moins 4 espaces d'indentation au début de chaque ligne)</span>. Chaque premier niveau d'indentation constitue un script. Voici un exemple contenant deux scripts:

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

Ce court exemple montre qu'un fichier peut contenir plusieurs scripts. `ma_premiere_tache` et `ma_seconde_tache` sont deux scripts différents qui n'ont aucun lieu entre eux, sinon le fait qu'ils soient dans le même fichier.

Par ailleurs, il est important de noter que les *noms de script* et que les *noms de fichiers* sont deux choses différentes. `ma_premiere_tache` et `ma_seconde_tache` peuvent être dans un même fichier intitulé `mes_premiers_scripts.dsc`. L'important est ici le nom du script <span class="parens">(that `ma_premiere_tache`)</span>, le nom du fichier <span class="parens">(`mes_premiers_scripts.dsc`)</span> n'a aucune importance fonctionnelle dans Denizen et dépend simplement de la façon dont vous souhatez organiser vos scripts.

#### Types de Scripts

Sous le nom du script - au second niveau de l'indentation - on peut voir une clé `type`.

La clé `type` est l'endroit où vous indiquez le `type` de script Denizen vous créez. Dans le cas présent, on édite script de type `task` (tâche). Il y également des scripts de type  `world`, de type `item` ou encore de type `inventory` scripts et beaucoup d'autres qui remplissent chacun une fonction précise. Nous y reviendrons plus tard. Pour l'heure, concentrons-nous sur les scripts `task`. Vous apprendrez les différences entre ces autres types de script au cours de ces guides, et vous pourrez trouver des explications sommaires sur chacun d'entre eux dans la documentation générales Denizen (en englais) sur la page [language explanation](https://one.denizenscript.com/denizen/lngs/container).

Make sure you write `type: task` in your script on the second level of indentation <span class="parens">(press **enter** to start a new line, then press **tab** to indent once. This will add 4 spaces on the line, and every time you press enter after there will automatically be 4 spaces again, until you press backspace to remove the spaces)</span>, below the script name, like this:

```dscript_blue
my_first_task:
    type: task
```

#### Script Commands

Below the `type` key, you'll see the `script` key. For a task script, the `script` key is where you write the content of the script - the set of instructions that tell Denizen what to do. Other types of scripts use other keys, and you'll learn about them as you continue to work through this guide. The majority of actual work you do in Denizen will be under keys like this one.

Let's look at another example script:

```dscript_green
my_first_task:
    type: task
    script:
    - narrate "This is a valid task script!"
    - narrate "Congratulations on writing your first script!"
```

Notice how the text we want to narrate - `This is a valid task script!` - is enclosed in `""` quotes. Because the message we want to narrate has ` ` spaces in it, we enclose it in quotes to make sure that the command only has one argument. Denizen commands have arguments that are separated by ` ` spaces. For example, `run one two three` has arguments `one`, `two`, and `three`, but `run "one two three"` only has one argument, `one two three`.

### Completed Product

At this point, you should have a task script that's ready to run! Go on, give it a try - first, type `/ex reload` in-game to load the new script in, then use the `/ex run (YourTaskName)` command to run the task in-game. For example, the in-game command to run the above script would be `/ex run my_first_task`.

If you see the text that you wrote for the `narrate` command, you've successfully written your first task script. Congratulations!

![](https://i.alexgoodwin.media/i/denizen_guide/831e94.png)

### A Little Bit Further

To take what you learned here a little bit further, and bearing in mind that while we've been using the `run` command via `/ex`, it is a Denizen script command <span class="parens">(the `/ex` command is just an in-game tool to quickly run any script command)</span>, let's look at an example that does just a little bit more than the previous ones.

You can also use one task script to trigger another task script. That looks like this:

```dscript_green
my_first_task:
    type: task
    script:
    - narrate "This is a valid task script!"
    - narrate "Congratulations on writing your first script!"
    - run my_second_task

my_second_task:
    type: task
    script:
    - narrate "This is your second task script!"
```

This is just a basic example, and you'll be able to create more complicated and powerful scripts as you learn more about Denizen.

