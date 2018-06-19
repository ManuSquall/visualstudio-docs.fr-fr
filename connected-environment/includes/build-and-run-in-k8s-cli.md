---
ms.topic: include
ms.openlocfilehash: b10d15b90f7f413d26adf8037c6f52c711a9ed69
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030931"
---
## <a name="build-and-run-code-in-kubernetes"></a>Générer et exécuter du code dans Kubernetes
Exécutons notre code. Dans la fenêtre de terminal, exécutez cette commande à partir du **dossier de code racine**, webfrontend :

```cmd
vsce up
```

Gardez un œil sur la sortie de la commande, vous remarquerez plusieurs choses à mesure de sa progression :
1. Le code source est synchronisé dans l’environnement de développement dans Azure.
1. Une image de conteneur est générée dans Azure, comme l’indiquent les ressources Docker du dossier de votre code.
1. Les objets Kubernetes sont créés à partir de l’image de conteneur spécifiée par le graphique Helm du dossier de votre code.
1. Des informations sur le ou les points de terminaison du conteneur s’affichent à l’écran. Dans notre cas, nous attendons une URL HTTPS publique.
1. En supposant que les étapes ci-dessus aboutissent correctement, la sortie `stdout` (et `stderr`) doit commencer à s’afficher au démarrage du conteneur.

> [!Note]
> Si ces étapes prennent un certain temps lors de la première exécution de la commande `up`, les suivantes sont plus rapides.

## <a name="test-the-web-app"></a>Tester l’application web
Parcourez la sortie de la console à la recherche d’informations sur l’URL publique qui a été créée par la commande `up`. Elles se présentent sous la forme suivante : 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

Après avoir ouvert cette URL dans une fenêtre de navigateur, l’application web doit se charger. La sortie `stdout` et `stderr` s’affiche dans la fenêtre de terminal à mesure que le conteneur s’exécute.
