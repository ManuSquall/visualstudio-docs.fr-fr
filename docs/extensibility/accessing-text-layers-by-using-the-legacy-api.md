---
title: "L’accès à des couches de texte à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54a981a57605ccb93062ac0678b1e8b5673c6d1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>L’accès à des couches de texte à l’aide de l’API héritée
Généralement, un calque de texte encapsule un aspect de la disposition du texte. Par exemple, une couche de « fonction-à-un-temps » masque le texte avant et après une fonction contenant le point d’insertion (point d’insertion de texte).  
  
 Une couche de texte se trouve entre une mémoire tampon et une vue, et modifie la façon que la vue peut voir le contenu du tampon.  
  
## <a name="text-layer-information"></a>Informations de couche de texte  
 La liste suivante décrit le fonctionnement des couches de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Le texte dans une couche de texte peut être orné avec marqueurs et la coloration de syntaxe.  
  
-   Vous ne pouvez actuellement ne peut pas implémenter votre propre couches.  
  
-   Une couche expose <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, qui est dérivée de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. La mémoire tampon de texte lui-même est également implémentée comme une couche, ce qui permet une vue afin de traiter les couches sous-jacentes manière polymorphe.  
  
-   Peut se trouver à n’importe quel nombre de couches entre la vue et de la mémoire tampon. Chaque couche porte uniquement sur la couche en dessous, et la vue porte principalement sur la couche supérieure. (La vue ne dispose pas des informations sur la mémoire tampon.)  
  
-   Une couche peut affecter uniquement les couches figurant en dessous. Il ne peut pas affecter les couches au-dessus de lui au-delà des événements standard d’origine.  
  
-   Dans l’éditeur, le texte masqué, le texte synthétique et le retour automatique à sont implémentés en tant que couches. Vous pouvez implémenter le texte masqué et synthétique sans interagir directement avec les couches. Pour plus d’informations, consultez [mode plan dans un Service de langage hérité](../extensibility/internals/outlining-in-a-legacy-language-service.md) et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Chaque couche de texte a son propre système de coordonnées local qui est exposée via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interface. Par exemple, la couche de renvoi à la ligne peut contenir les deux lignes pendant que la mémoire tampon sous-jacente peut contenir qu’une seule ligne.  
  
-   La vue communique avec les couches via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interface. Cette interface permet de concilier les coordonnées de la vue avec les coordonnées de la mémoire tampon.  
  
-   Une des couches telles que la couche de texte synthétique provenant de texte doit fournir une implémentation locale de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   En outre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, une couche de texte doit implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et déclencher les événements dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)   
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personnalisation des Menus et des contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)