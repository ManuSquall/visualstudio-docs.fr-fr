---
title: Débogage à l’aide de la visionneuse de la boutique | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654891"
---
# <a name="debugging-by-using-the-store-viewer"></a>Débogage à l'aide de la visionneuse de banque d'information
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avec la visionneuse du Store, vous pouvez examiner l’état d’un *magasin* utilisé par [!INCLUDE[dsl](../includes/dsl-md.md)]. La visionneuse du Store affiche tous les éléments de modèle de domaine qui se trouvent dans un magasin spécifique, ainsi que les propriétés d’élément et les liens entre les éléments.

## <a name="opening-store-viewer"></a>Ouverture de la visionneuse du Store
 Lorsque vous êtes dans la build expérimentale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], arrêtez votre code à un point d’arrêt où une instance du magasin contient des informations sur le modèle. Ensuite, ouvrez la visionneuse de magasin en tapant la commande suivante dans la fenêtre **exécution** :

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> Vous devez remplacer `mystore` par le nom de votre instance de Store. En outre, si vous ajoutez l’espace de noms à votre code, vous pouvez taper la commande permettant d’afficher la visionneuse de magasin sans l’espace de noms complet :
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 La méthode `Show` a plusieurs surcharges. Vous pouvez spécifier une instance d’un magasin ou d’une partition en tant que paramètre.

 Vous pouvez également placer la ligne de code qui affiche la visionneuse de magasin n’importe où dans votre code où le paramètre que vous transmettez à la méthode `Show` est dans la portée. Cette action affiche la visionneuse de magasin lorsque la ligne de code s’exécute comme un instantané du contenu du magasin.

### <a name="using-store-viewer"></a>Utilisation de la visionneuse du Store
 Lorsque la visionneuse du magasin s’ouvre, une fenêtre de Windows Forms non modale s’affiche, comme le montre l’illustration suivante.

 ![](../modeling/media/storeviewer2.png "storeviewer2")Visionneuse du Store

 La visionneuse du Store comporte trois volets : le volet gauche, le volet supérieur droit et le volet inférieur droit. Le volet gauche est une arborescence des types dans le membre `DomainDataDirectory` d’un magasin. Si vous développez le nœud de partition et cliquez sur un élément, les propriétés de l’élément s’affichent dans le volet supérieur droit. Si l’élément est lié à d’autres éléments, les éléments supplémentaires s’affichent dans le volet inférieur droit. Si vous double-cliquez sur un élément dans le volet inférieur droit, l’élément est mis en surbrillance dans le volet gauche.

## <a name="see-also"></a>Voir aussi
 [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
