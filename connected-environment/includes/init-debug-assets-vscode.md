---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Initialiser les ressources de débogage avec l’extension VS Code
Tout d’abord, nous devons configurer notre projet de code de sorte que VS Code communique avec notre environnement de développement dans Azure. L’extension VS Code pour Connected Environment fournit une commande d’assistance pour configurer le débogage. 

Ouvrez la **palette de commandes** (via le menu **Affichage | Palette de commandes**) et utilisez la saisie semi-automatique pour taper et sélectionner cette commande : `Connected Environment: Create configuration files for connected development`. 

La configuration du débogage pour Connected Environment est alors ajoutée sous le dossier `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **IMPORTANT** : En raison d’un bogue, fermez et rouvrez VS Code avant de continuer.