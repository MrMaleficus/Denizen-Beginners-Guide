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

### Attend... Dans la narration ? Je voulais coder, pas écrire un dialogue !

Pas d'inquiétude ! La commande `narrate` est la premiére commande Denizen, sinon la plus basique, que vous devez apprendre : elle affiche une ligne de texte dans le Chat du joueur en question. <span class="parens">(Quand vous l'utilisez avec `/ex`, vous verrez également des informations de debug liées à l'exécution de la commande Denizen, mais dans un usage en condition réelle, c'est à dire dans un script, vous ne verrez que la ligne de texte affichée avec `narrate`)</span> C'est une commande basique, très commune et très utile pour tester un tag par exemple. Elle est également utiliser dans des scripts de PNJ <span class="parens">(tout tout ce que le joueur doit lire mais qui n'est pas dit par le PNJ, - la commande narrate peut s'avérer utile !)</span>, dans les commandes serveur customs, <span class="parens">(le texte affiché lorsque le joueur tape dans le Chat une `/commande` que vous avez créé avec Denizen le sera avec l'aide de la commande narrate)</span> et bien plus encore !

### Ok. Je fais quoi ?

Well if you haven't caught on yet: open your in-game chat and type `/ex narrate "hi <player.name>"`. This will be a recurring theme throughout this guide: you'll find examples of things you can do and descriptions of what they do and how they work... you won't always be explicitly told to, but you should always go ahead and try them out (on your local test server!). As you get to writing actual script files, there will be examples specifically color-coded to indicate whether you can just copy them in. Please take a moment to open [This Guide: Sample Scripts](/guides/this-guide/sample-scripts) in a new tab to review the color coding system before you continue.

Note that rather than raw copy-pasting, as much as possible you should be retyping the scripts you're testing. This helps guarantee you've actually read every bit of the script, and gives you time to think and understand exactly what each bit is before running it - and, importantly, gives you light practice writing scripts. You will of course be much more ready to test something with `/ex` if you've typed a few `/ex` test commands already (compared to if you've only read about the idea and copypasted a sample).

### Back On Topic: What Can `/ex` Do?

Basically anything! You can run any Denizen command from `/ex`, and there's Denizen commands for just about everything. In fact it's so powerful that I must note: on public servers, don't give permission access to `/ex` to anyone you wouldn't give full operator access to. If you have any doubts about that level of restriction: note that any player with access to `/ex` could easily do `/ex adjust <player> is_op:true`.

### What's This Got To Do With Scripting?

Denizen commands are at the heart of every script. Scripts can be described as simple config files listing a bunch of Denizen commands <span class="parens">(and the configuration parts just there to indicate when exactly it is the commands should run)</span>.

`/ex` is a really handy way to test out individual commands in-game quickly. We'll be making a lot of use of it in the upcoming sections of this guide. It's one of several Denizen power-tools that make your life easy <span class="parens">(and make Java developers hate their choice to learn Java after seeing how much better it is on the Denizen side!)</span>.
