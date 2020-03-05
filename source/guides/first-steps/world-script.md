Your First World Script
-----------------------

```eval_rst
.. contents:: Table of Contents
    :local:
```

## World Script Basics

Un world script est un script qui s'active ou s'exécuté automatiquement quand un événement donné se produit sur le serveur. Ils sont constitués d'une ou plusieurs clés d'événements dans laquelle des instructions sont écrites et éxécutées sous forme de commandes Denizen, tel que les commandes `run` ou `inject` lorsque l'événement en question se produit.

Tout comme les scripts Task, les scripts World éxécuteront toutes les commandes Denizen qui les composent lorsque l'événement ciblé se produira sur le serveur. Les scripts World se révélent très utiles, voire essentiels si vous voulez gérer les actions de vos joueurs et déterminer d'autres actions en conséquence, créer des interfaces visuels avec des inventaires personalisés, tracer des actions effectuées par vos joueurs, ou créer des mini-jeux.

## Attends... "un événement" ?

Un événement (ou event) est quelques choses qui se produit sur le serveur. Il peut être, par exemple, déclenché par une entité en train de faire quelques choses, ou par un joueur en train de faire une certaine action. Admettons, on souhaite exécuter des commandes Denizen lorsqu'un joueur casse un bloc. On sait qu'il existe un event que l'on peut exploiter : l'event `on player breaks block`. On va donc monitorer cet événement et déclencher des actions lorsqu'un joueur casse un bloc.

## Syntax d'un World Script

Voilà un exemple basique de World Script fonctionnel.

```dscript_green
mon_premier_world_script:
    type: world
    events:
        on player breaks block:
        - narrate "Tu as cassé un bloc !"
```
Ce script affichera le texte  Tu as cassé un bloc !` au joueur attaché à l'événement, c'est à dire chaque joueur en train de casser un bloc.

Notons que ce script est contouré en vert, ce qui signifie qu'il peut être copié-collé et utiliser sur votre serveur. Mais attention, un tel world script avec un event `on player breaks block:` va s'éxécuter lorsque *n'importe quel joueur* cassera *n'importe quel bloc* et *n'importe où*, ce qui n'est pas recommandé ! Voyons voir de quoi ce script est constitué avant d'approfondir.

### Construire son premier world script dans VS Code

Précédemment vous avez appris [how to set up VS Code](/guides/first-steps/script-editor), l'éditeur que nous recommandons quand vous créez vos scripts Denizen.

#### Créer le fichier

Pour créer votre premier world script, commençez par ouvrir votre dossier scripts dans VS Code.

![](https://i.alexgoodwin.media/i/denizen_guide/548218.png)
![](https://i.alexgoodwin.media/i/denizen_guide/d2810b.png)

Ensuite, cliquez sur votre dossier dans l'explorateur puis cliquez sur "New file" pour créer un nouveau fichier

![](https://i.alexgoodwin.media/i/denizen_guide/5fad5b.png)

Donnez le nom que vous voulez ! Il est important d'ajouter l'extension `.dsc` - l'extension officielle des scripts Denizen.

![](https://i.alexgoodwin.media/i/denizen_guide/e3ec76.png)

On va pouvoir commencer à scripter !

#### Ecrire le script

Commençons avec le coeur du World Script:

```dscript_green
mon_premier_world_script:
    type: world
    events:
        on player places block:
        - narrate "Tu as cassé un bloc !"
        - narrate "Bravo !"
```

Cet exemple peut sembler familier - il est trés similaire à l'exemple abordé ci-dessus, excepté que l'on utilise `on player places block` au lieu de `on player breaks block`, cela signifie que le script se déclenchera à chaque fois qu'un bloc sera placé par le joueur. Décomposons ce que l'on voit ici.

- `mon_premier_world_script:` est le nom du script, se situant au sommet de l'indentation du script. Il s'agit du nom interne à Denizen qui permettra de l'identifier. Chaque nom de script doit être unique, c'est à dire que plusieurs scripts ne peuvent pas avoir le même nom, ou des erreurs se produiront.

- `type: world` est la clé qui définit le type de script dont il s'agit. Elle est placée au second niveau d'indentation du script, c'est à dire 4 espaces après le niveau un d'indentation. Nous avons pu voir précédemment des scripts de type `task`. Ce type va définir à la fois sa fonction et ses effets. Comme expliqué précédemment, le type `world` est un type de script qui s'active ou s'exécuté automatiquement quand un événement donné se produit sur le serveur.

- `events:` est la clé qui va contenir l'essentiel de vos instructions. Elle est placée au second niveau d'indentation du script, au même niveau que la clé `type` car elle est obligatoire à son fonctionnement. Elle est semblable à la clé `script:` pour les scripts de type `task`. Différence notable : les world scripts n'ont pas de clé `script:` de même que les task scripts n'ont pas de clé `events:`, qui est une particularité propre aux world scripts. A partir de là, le contenu prenant place dans un niveau d'indentation supérieur, c'est à dire 8 espace après le premier et 4 espaces après celui-ci constitue l'essentiel de votre code.

- `on player places block:` est un événement, qui se présente sous la forme d'une clé, et qui va contenir toutes les instructions qui seront exécutées au moment où l'événement indiqué se produira. (En l'espéce, ici : lorsqu'un joueur place un bloc.) Cette clé est personnalisable et peut prendre la forme de n'importe quel événement implanté dans Denizen. La liste de tous les événements exploitables est indiquée ici : https://one.denizenscript.com/denizen/evts/ Les commandes qui seront éxécutées lorsque l'événement se produira sont situées sous cette clé, au même niveau d'indentation que la clé de l'événement, comme dans l'exemple ci-dessus. Chaque "event" peut être personnalisé selon l'événement exact que l'on recherche, et nous le verrons dans un instant.

- `- narrate` une commande denizen. Les commandes sont éxécutées les unes après les autres, du haut vers le bas, et doivent disposer d'arguments valides afin d'être éxécutées. Si la construction d'une commande Denizen n'est pas correcte, ou si un tag n'est pas correct, des erreurs surviendront. Par convention, il est recommandé que les commandes Denizen associées à un event soient situées au même niveau d'identation que l'événement associé.

## Précisons les choses

Admettons que nous voulions afficher un dialogue au joueur lorsqu'il casse un minerai de diamant uniquement. Nous pouvons directement insérer le minerai de diamant comme bloc à utiliser dans l'event, grâce à son *material ID* : `diamond_ore`. La liste des ID pour chaque matériaux et objets du jeu est disponible ici : https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html. Démonstration :

```dscript_green
world_script_diamant:
    type: world
    events:
        on player breaks diamond_ore:
        - narrate "Tu as cassé un minerai de diamant !"
```

Chaque joueur qui cassera un minerai de diamant (à ne pas confondre `diamond_block` qui est le material ID du bloc de diamant) aura la phrase `Tu as cassé un minerai de diamant !` affichée dans son chat. N'oublions pas qu'un world script peut contenir plusieurs events. Démonstration :

```dscript_green
world_script_diamant:
    type: world
    events:
        on player breaks diamond_ore:
        - narrate "Tu as cassé un minerai de diamant !"
        on player places diamond_block:
        - narrate "Tu es riche !"
        on player breaks emerald_ore:
        - narrate "Tu cas cassé un minerai d'émeraude !"
```

Dans ce script, les joueurs verront afficher dans lignes dans leur chat à chaque fois qu'ils casseront un minerai de diamant, placeront un bloc de diamant, ou casseront un minerai d'émeraude.

Vous savez maintenant construire des world scripts basiques et éxécuter des commandes Denizen en fonction des actions entreprises par les joueurs.

## Les Contextes

Pour comprendre cette partie, il est essentiel d'avoir lu et compris la documentation concernant les Tags dans Denizen.
Dans l'utilisation des world scripts et dans votre recherche d'événements que vous souhaiterez exploiter, vous allez constater que certains events ont des tags qui leur sont propres et qui commencent le plus souvent par `<context.` comme ci-dessous.

(insérer le screen)

Ces tags sont donc des tags spéciaux qui ne peuvent utilisés qu'uniquement dans le cadre de l'éxécution de l'event associé. En l'espéce l'event `on player breaks block` a comme tags de contexte la position du bloc qui a été cassé, sous forme de LocationTag (`<context.location>`), le matériel du bloc qui a été cassé, sous fomre de MaterialTag (`<context.material>`) et l'XP droppé par la casse du bloc, sous forme de ElementTag de type nombre (`<context.xp>`) ces tags sont automatiques remplis par les valeurs correspondantes associées à l'événement lorsqu'il se réalise. Prenons le cas du script suivant :

```dscript_blue
world_script_diamant:
    type: world
    events:
        on player breaks block:
        - narrate "Tu cassé un <context.material> !"
        - narrate "La position du bloc était <context.location> !"
        - narrate "Tu as droppé <context.xp> XP !"
```



