La Commande Ex
--------------

```eval_rst
.. contents:: Table of Contents
    :local:
```

### Alors comme ça, vous voulez utiliser Denizen ?

Si vous lisez cette page, vous êtes très probablement nouveau à Denizen Script et vous êtes prêt à apprendre les bases élémentaires de Denizen. Comme évoqué dans les pages précédentes de ce guide, Denizen est un *moteur de script*. Est-ce que cela signifie que vous allez écrire des fichiers de scripts remplis d'instructions scriptées et codées ? Hé bien, en quelques sortes... Vous n'avez pas *besoin* d'écrire des scripts dans des fichiers séparés. Pour les besoins de ce guide et afin de vous plonger en douceur dans l'univers de Denizen, nous n'allons utiliser qu'une fonction phare de Denizen : vous pouvez écrire des commandes Denizen in-game, et c'est suffisant !

### Commandes Denizen vs Commandes Serveur

Avant d'aller plus loin, il y a une importante distinction à saisir entre une "commande Denizen" et une "commande Serveur".

- Une **commande Serveur** est une commande que vous pouvez utilisez directement in-game dans le Chat avec le `/` que vous connaissez très bien !
- Une **commande Denizen** est une commande qui prend place dans un script Denizen et qui est exécutée par le moteur de script Denizen. Par exemple, `- narrate "salut <player.name>"` est une commande Denizen. Notons qu'un `-` est utilisé et est présent avant la commande (en vertu des standards Denizen) et peut utiliser des tags (comme `<player.name>`), ce que les commandes serveur ne peuvent pas faire.

Ces commandes ne sont pas interchangeables ! On ne peut pas utiliser `/narrate "salut <player.name>"` - cela vous indiquera 'commande inconnue'. De même, vous ne pouvez pas non plus utiliser `- gamemode creative` dans un script, car cela vous donnera une erreur de script.

### Mais tu disais qu'on pouvait utiliser des commandes Denizen in-game...

C'est vrai ! Mais pour ça, nous allons devoir transformer des commandes Denizen en commandes serveur ! Comment diable fait-on ça ? Il y a une commande serveur qui permet d'exécuter des commandes Denizen, et il y a aussi une commande Denizen qui permet d'exécuter des commandes Serveur.

Si vous êtes in-game, et que vous utilisez des commandes Serveur ; pour pouvoir exécuter des commandes Denizen, il faudra utiliser la commande `/ex`. Par exemple : `/ex narrate "salut <player.name>"`. La commande `/ex` est une commande Serveur qui permet de faire l'interface entre les commandes Denizen et les commandes Serveur, indiquant à Denizen les instructions à exécuter. Concréctement, cela ressemble à ça :
![](https://i.alexgoodwin.media/i/denizen_guide/a5d1c0.png)

Inversement, si vous êtes en édition de script et que vous souhaitez, dans ce script, utiliser des commandes serveur ; vous pouvez utilisez la commande denizen `- execute`, comme `- execute as_op "gamemode creative"` <span class="parens">(vous pouvez aussi utiliser `as_player`, `as_server`, ou même `as_npc`)</span>. Notons que dans la plupart des cas, l'utilisation de la commande `- execute` n'est pas recommandée et peut être évitée, car tout ce que peut faire une commande serveur, une commande Denizen peut le faire aussi bien, voire mieux <span class="parens">(Pour l'exemple ci-dessus : `- adjust <player> gamemode:creative`)</span>. La commande `- execute` peut cependant être trés utile si vous souhaitez intégrer des commandes serveur qui sont gérées par d'autres plugins que vous souhaitez intégrer à vos scripts Denizen.

Nota Bene : `/ex` et `- execute` ont des fonctions opposées mais complémentaires. De façon générale, il n'y a *AUCUNE* raison de les utiliser en même temps sur la même commande. Quand vous y pensez, l'idée de ces les utiliser en même temps est assez folle... mais des utilisateurs ont déjà tenté des choses comme `- execute as_server "ex narrate 'hi'"`. Bien ce genre de commande est un non-sens total où dans un script il suffirait juste d'utiliser `- narrate 'hi'`.

### Attend... De la narration ? Je voulais coder, pas écrire un dialogue !

Pas d'inquiétude ! La commande `narrate` est la premiére commande Denizen, sinon la plus basique, que vous devez apprendre : elle affiche une ligne de texte dans le Chat du joueur cible. <span class="parens">(Quand vous l'utilisez avec `/ex`, vous verrez également des informations de debug liées à l'exécution de la commande Denizen dans votre Chat, mais dans un usage en condition réelle, c'est à dire dans un script, vous ne verrez que la ligne de texte affichée par le `narrate`)</span> C'est une commande basique et très utile pour tester un tag par exemple. Elle est également utiliser dans des scripts de PNJ <span class="parens">(dans tout ce que le joueur doit lire mais qui ne constitue pas un dialogue prononcé par le PNJ, - la commande narrate peut s'avérer utile !)</span>, dans les commandes Serveur customs, <span class="parens">(le texte affiché, lorsque le joueur tape dans le Chat une `/commande` que vous avez créé avec Denizen, le sera avec l'aide de la commande `narrate`)</span> et bien plus encore !

### Ok. Je fais quoi ?

Bon... Si vous n'avez pas encore saisi : ouvrez votre Chat tapez `/ex narrate "coucou <player.name>"`. Cela sera un thème récurrent à travers l'ensemble de ce guide : vous pourrez trouver tout un tas d'exemples de ce que vous pouvez faire, de ce que vous pouvez tester, et surtout, de comment ces choses fonctionnent... Le secret, c'est qu'on ne vous dira pas tout le temps explicitement de faire telle ou telle chose, ça sera parfois à vous d'aller de l'avant et de tenter des choses (sur votre serveur de test local !). Dans votre progression sur l'écriture de vos premiers scripts, vous trouverez dans ce guide des exemples de scripts que vous pouvez reprendre comme bon vous semble. Prenez ne le temps qu'il faut pour analyser quelques échantillons de scripts fonctionnels sur [This Guide: Sample Scripts](/guides/this-guide/sample-scripts) afin de saisir quels échantillons sont fonctionnels, et quels échantillons sont à éviter !

Cependant, au lieu de copier-coller ces scripts, il est vivement recommandé de les retaper entiérement au fur et à mesure de vos tests. Pourquoi ? Parce que cela vous aide à comprendre les instructions que vous tapez, parce qu'en même temps de coder, vous lisez ce que vous codez, et - surtout, c'est un très bon apprentissage pour passer à la suite et faire de nouveaux scripts. Vous serez également, sans doute, plus enclein à faire vos tests avec `/ex` si vous avez déjà utilisé plusieurs fois la commande `/ex` pour vos tests, car vous saurez exactement ce que vous voulez tester (c'est toujours mieux que de n'avoir que l'idée approximative de ce qu'un script fait et de le reproduire sans réfléchir !).

### Mais au fait, la commande `/ex`, elle sert à quoi ?

Vous pouvez tout faire avec la commande `/ex` : éxécuter n'importe quelle commande Denizen... Et la bonne nouvelle, c'est à qu'il y a des commandes Denizen pour tout ! Chose importante à noter : il n'est pas recommandé (du tout) de donner la permission d'utiliser `/ex` à vos joueurs, car ils pourront, d'une seule commande, devenir Opérateur. N'importe quel joueur avec la commande `/ex` peut par exemple faire `/ex adjust <player> is_op:true`, pour cette raison, il n'y aurait que vous, administrateur du serveur, qui pourrait avoir d'utiliser cette commande.

### Quel est le rapport avec le Scripting?

Les commandes Denizen sont le coeur de tous les scripts. Ils peuvent être décrtis comme de simples fichiers de configuration listant une succession de commandes Denizen. <span class="parens">(et la partie configuration n'est là simplement que pour indiquer quand exactement une commande Denizen doit s'exécuter)</span>.

`/ex` est à ce titre un outil fort utile fin de tester individuellement des commandes rapidement. Nous n'hésiterons pas à beaucoup l'utiliser dans les prochaines sections de ce guide. C'est une commande destinée à vous rendre la vie plus facile <span class="parens">(et faire en sorte que les développeurs Java regrettent leur choix d'avoir appris le Java voyant comment Denizen fonctionne !)</span>.
