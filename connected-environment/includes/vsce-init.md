---
ms.topic: include
ms.openlocfilehash: 394e31bf0660557c1eba571006cacf213263c07e
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031071"
---
## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Initialiser le code pour le développement Docker et Kubernetes
Pour le moment, nous disposons d’une application web de base qui peut s’exécuter localement. Nous allons maintenant la mettre en conteneur en créant des ressources qui définissent le conteneur de l’application et la façon dont il sera déployé dans Kubernetes. Cette opération est facile à réaliser avec Connected Environment : 

1. Lancez VS Code et ouvrez le dossier `webfrontend`. (Vous pouvez ignorer les invites par défaut d’ajout de ressources de débogage ou de restauration du projet.)
1. Ouvrez le terminal intégré dans VS Code (via le menu **Affichage | Terminal intégré**).
1. Exécutez cette commande (vérifiez que **webfrontend** est votre dossier actif) :

```cmd
vsce init --public
```

La commande ```init``` de l’interface CLI Connected Environment génère des ressources Docker et Kubernetes avec les paramètres par défaut :
* `./Dockerfile` décrit l’image du conteneur de l’application et la façon dont le code source est généré et s’exécute dans le conteneur.
* Un [graphique Helm](https://docs.helm.sh) sous `./charts/webfrontend` décrit la façon dont le conteneur est déployé dans Kubernetes.

Pour l’instant, il n’est pas utile de comprendre l’intégralité du contenu de ces fichiers. Cependant, il est important de noter que **les mêmes ressources de configuration en tant que code Kubernetes et Docker peuvent être utilisées du développement jusqu’à la production, et ainsi offrir une meilleure cohérence entre les différents environnements.**
 
Un fichier nommé `./vsce.yaml` est également généré par la commande `init` ; il s’agit du fichier de configuration de Connected Environment. Il complète les artefacts Docker et Kubernetes avec une configuration supplémentaire qui autorise une expérience de développement itératif dans Azure. Par exemple, le graphique Helm par défaut n’expose aucun point de terminaison public. Or, il est parfois utile d’ouvrir temporairement un point de terminaison public pendant le développement de façon à tester du code, par exemple, à partir d’un appareil mobile ou de l’URL d’un webhook. Un fichier vsce.yaml créé avec `init --public` remplace les paramètres par défaut Helm pour exposer un point de terminaison public en phase de développement uniquement.
