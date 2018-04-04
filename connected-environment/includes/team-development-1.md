Jusqu’à présent, nous avons exécuté le code de notre application comme si nous étions le seul développeur à travailler sur l’application. Dans cette section, nous allons découvrir en quoi Connected Environment simplifie le développement en équipe :
* Permettre à une équipe de développeurs de travailler dans le même environnement de développement.
* Permettre à chaque développeur d’itérer au sein de son code de manière isolée sans craindre de perturber les autres.
* Tester du code de bout en bout, préalablement à sa validation, sans avoir à créer des objets fictifs ou à simuler des dépendances.

## <a name="challenges-with-developing-microservices"></a>Difficultés liées au développement de microservices
Notre exemple d’application n’est pas très complexe pour le moment. Mais dans le cadre d’un développement réel, les difficultés ne tardent pas se manifester à mesure que des services sont ajoutés et que l’équipe de développement s’étoffe.

Imaginez-vous travaillant sur un service qui interagit avec des dizaines d’autres services.

1. Au bout d’un certain temps, il peut devenir irréaliste de tout exécuter en local à des fins de développement. En effet, il n’est pas certain que votre ordinateur de développement ait suffisamment de ressources pour exécuter l’application entière. Ou bien, votre application dispose peut-être de points de terminaison qui doivent être accessible publiquement (par exemple, votre application répond à un webhook à partir d’une application SaaS).
1. Vous pouvez essayer d’exécuter uniquement les services dont vous dépendez, mais cela signifie que vous devez avoir connaissance de la clôture complète des dépendances (par exemple, des dépendances de dépendances). Ou bien, peut-être ne savez-vous pas bien comment générer et exécuter vos dépendances, car vous n’y avez pas travaillé dessus.
1. Certains développeurs se résolvent à simuler ou à feindre la plupart des dépendances de leurs services. Cela peut parfois être utile, mais la gestion de ces objets fictifs peut vite devenir une tâche de développement à part entière. De plus, votre environnement de développement peut devenir très différent de l’environnement de production, et de légers bogues peuvent s’insinuer.
1. Il s’ensuit qu’il devient difficile d’effectuer le moindre test de bout en bout. Un test d’intégration peut raisonnablement être réalisé après la validation, ce qui signifie que les problèmes sont identifiés à un stade plus avancé dans le cycle de développement.

![](../media/microservices-challenges.png)


## <a name="work-in-a-shared-development-environment"></a>Travailler dans un environnement de développement partagé
Avec Connected Environment, vous pouvez configurer un environnement de développement *partagé* dans Azure. Chaque développeur peut se concentrer simplement sur sa partie de l’application et développer de manière itérative du *code de pré-validation* dans un environnement qui contient déjà tous les autres services et ressources cloud dont dépendent leur scénarios. Les dépendances sont toujours à jour et les développeurs travaillent comme en production.

## <a name="work-in-your-own-space"></a>Travailler dans votre propre espace
Entre le moment où vous développez le code de votre service et le moment où vous êtes en mesure de l’archiver, le code est souvent dans un état incorrect. Vous continuez de le façonner, de le tester et de l’expérimenter de manière itérative avec des solutions. Le concept d’**espace** propre à Connected Environment vous permet de travailler de manière isolée sans craindre de perturber les membres de votre équipe.

> [!Note]
> Avant de continuer, fermez toutes les fenêtres VS Code pour les deux services, puis exécutez `vsce up -d` dans les dossiers racines de chaque service. (Il s’agit d’une limitation de la préversion.)

Voyons où s’exécutent actuellement les services. Exécutez la commande `vsce list` pour obtenir une sortie de ce type :

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------------------
mywebapi     mainline  mywebapi-0.1.0     80/TCP  2m ago     <not attached>
webfrontend  mainline  webfrontend-0.1.0  80/TCP  1m ago     https://webfrontend-contosodev.vsce.io
```

La colonne Space indique que les deux services s’exécutent dans un espace nommé `mainline`. Quiconque ouvrant l’URL publique et accédant à l’application web appelle le chemin de code que nous avons écrit précédemment et qui parcourt les deux services. Maintenant, supposons que vous voulez continuer à développer `mywebapi`. Comment y parvenir sans interrompre les autres développeurs qui utilisent l’environnement de développement ? Pour cela, nous allons configurer notre propre espace.

## <a name="create-a-space"></a>Créer un espace
Pour exécuter notre propre version de `mywebapi` dans un autre espace que `mainline`, créons notre propre espace :
``` 
vsce space create --name scott
```

Dans l’exemple ci-dessus, j’ai attribué mon nom au nouvel espace pour que mes homologues sachent qu’il s’agit de l’espace dans lequel je travaille, mais vous avez toute latitude quant à la désignation et au sens que vous voulez lui donner, par exemple « sprint4 » ou « demo ». 

Exécutez la commande `vsce space list` pour afficher la liste de tous les espaces compris dans l’environnement de développement. Un astérisque (*) s’affiche en regard de l’espace actuellement sélectionné. Dans notre cas, l’espace nommé « scott » a été automatiquement sélectionné pendant sa création. Vous pouvez à tout moment sélectionner un autre espace à l’aide de la commande `vsce space select`.
