---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
## <a name="clean-up"></a>Nettoyer
Pour supprimer entièrement un environnement connecté dans Azure, notamment tous les services qui s’y exécutent, utilisez la commande `vsce env rm`. Ne perdez pas de vue que cette action est irréversible.

L’exemple suivant liste les environnements connectés présents dans votre abonnement Azure actif, puis supprime l’environnement nommé « myenv » qui se trouve dans le groupe de ressources « myenv-rg ».

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

