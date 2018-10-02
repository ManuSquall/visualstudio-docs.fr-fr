---
title: Débogage à l’aide de la visionneuse de Store | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0955cae279ece70498ce05584d6b17d6e254f89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501631"
---
# <a name="debugging-by-using-the-store-viewer"></a>Débogage à l'aide de la visionneuse de banque d'information
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [débogage à l’aide de la visionneuse de Store](https://docs.microsoft.com/visualstudio/modeling/debugging-by-using-the-store-viewer).  
  
Avec la visionneuse Store, vous pouvez examiner l’état d’un *stocker* utilisé par [!INCLUDE[dsl](../includes/dsl-md.md)]. La visionneuse Store affiche tous les éléments de modèle de domaine qui se trouvent dans un magasin spécifique, ainsi que les propriétés de l’élément et les liens entre les éléments.  
  
## <a name="opening-store-viewer"></a>Visionneuse de l’ouverture Store  
 Lorsque vous êtes dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] expérimentale de build, arrêtez votre code à un point d’arrêt où une instance de la banque contient des informations sur le modèle. Ensuite, ouvrir la visionneuse de Store en tapant la commande suivante dans le **immédiat** fenêtre :  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Vous devez remplacer `mystore` par le nom de votre instance store. En outre, si vous ajoutez l’espace de noms à votre code, vous pouvez taper la commande d’affichage Store visionneuse sans l’espace de noms qualifié complet :  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 Le `Show` méthode a plusieurs surcharges. Vous pouvez spécifier une instance d’un magasin ou une partition en tant que paramètre.  
  
 Comme alternative, vous pouvez placer la ligne de code qui affiche la visionneuse de Store n’importe où dans votre code où le paramètre que vous passez à la `Show` méthode est dans la portée. Cette action affiche la visionneuse Store lors de la ligne de code s’exécute en tant qu’instantané du contenu de la banque.  
  
### <a name="using-store-viewer"></a>À l’aide de la visionneuse de Store  
 Lorsque la visionneuse de Store s’ouvre, une fenêtre de Windows Forms non modale s’affiche, comme le montre l’illustration suivante.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Visionneuse de Store  
  
 La visionneuse de Store comporte trois volets : les volets de gauche, en haut à droite et en bas à droite. Le volet gauche est une arborescence des types dans le `DomainDataDirectory` membre d’un magasin. Si vous développez le nœud de la Partition et cliquez sur un élément, les propriétés de l’élément s’affichent dans le volet supérieur droit. Si l’élément est lié à d’autres éléments, les éléments supplémentaires apparaissent dans le volet en bas à droite. Si vous double-cliquez sur un élément dans le volet en bas à droite, l’élément est mis en surbrillance dans le volet gauche.  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)



