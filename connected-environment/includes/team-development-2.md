---
ms.topic: include
ms.openlocfilehash: 9da28d29dc431f2f6ec92a01c397244147042f12
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
2. Appuyez sur F5 (ou tapez `vsce up` dans la fenêtre de terminal) pour exécuter le service. Il s’exécute alors automatiquement dans l’espace `scott` nouvellement sélectionné. 
1. Nous pouvons le vérifier en exécutant à nouveau `vsce list`. En premier lieu, vous remarquerez qu’une instance de `mywebapi` s’exécute maintenant dans l’espace `scott` (la version s’exécutant dans `mainline` s’exécute toujours, mais elle n’est pas répertoriée). En deuxième lieu, l’URL du point d’accès de `webfrontend` est précédée du préfixe « scott- ». Cette URL est unique à l’espace `scott` et signifie que les demandes envoyées à l’« URL scott » tentent d’abord un routage vers les services de l’espace`scott` avant de se rabattre sur les services de l’espace `mainline`.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Cette fonctionnalité intégrée de Connected Environment vous permet de tester le code de bout en bout dans un environnement partagé sans contraindre chaque développeur à recréer la pile complète de services dans son espace. Notez que ce routage nécessite le transfert d’en-têtes de propagation dans le code de votre application, comme nous l’avons vu dans l’étape précédente de ce guide.

## <a name="test-code-in-a-space"></a>Tester du code dans un espace
Pour tester la nouvelle version de `mywebapi` avec `webfrontend`, ouvrez votre navigateur en indiquant l’URL du point d’accès public de webfrontend, puis accédez à la page À propos. Votre nouveau message doit alors s’afficher.

À présent, supprimez l’élément « scott- » de l’URL et actualisez le navigateur. L’ancien comportement est rétabli (mis en évidence par la version `mywebapi` s’exécutant dans `mainline`).