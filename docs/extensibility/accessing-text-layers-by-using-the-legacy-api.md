---
title: L’accès à des couches de texte à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47085216c6f20ca1add535a76ce4f5fb4043a6dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945936"
---
# <a name="access-text-layers-by-using-the-legacy-api"></a>Couches de texte de l’accès à l’aide de l’API héritée
En règle générale, un calque de texte encapsule certains aspects de la disposition du texte. Par exemple, une couche « fonction-à-à la fois » masque le texte avant et après une fonction contenant le signe insertion (point d’insertion de texte).  
  
 Une couche de texte se trouve entre une mémoire tampon et une vue, et modifie la façon que la vue voit le contenu du tampon.  
  
## <a name="text-layer-information"></a>Informations de couche de texte  
 La liste suivante décrit le fonctionnement des couches de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Le texte dans une couche de texte peut être orné avec marqueurs et la coloration syntaxique.  
  
-   Vous ne pouvez actuellement ne peut pas implémenter vos propres couches.  
  
-   Expose une couche <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, qui est dérivée de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. La mémoire tampon de texte elle-même est également implémentée comme une couche, ce qui permet une vue de traiter de manière polymorphe avec les couches sous-jacentes.  
  
-   N’importe quel nombre de couches peut être comprise entre la vue et la mémoire tampon. Chaque couche ne concerne que la couche en dessous, et la vue porte principalement sur la couche supérieure. (La vue ne dispose pas des informations sur la mémoire tampon.)  
  
-   Une couche peut affecter uniquement les couches figurant en dessous. Il ne peut pas affecter les couches au-dessus de lui au-delà des événements standards d’origine.  
  
-   Dans l’éditeur, le texte masqué, le texte synthétique et le retour automatique à sont implémentées en tant que couches. Vous pouvez implémenter le texte masqué et synthétique sans interagir directement avec les couches. Pour plus d’informations, consultez [le mode plan dans un service de langage hérité](../extensibility/internals/outlining-in-a-legacy-language-service.md) et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Chaque couche de texte a son propre système de coordonnées local qui est exposée via la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interface. Par exemple, la couche de retour à la ligne peut contenir les deux lignes tandis que la mémoire tampon de texte sous-jacente peut contenir qu’une seule ligne.  
  
-   La vue communique avec des couches via la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interface. Utilisez cette interface pour rapprocher les coordonnées de vue avec les coordonnées de la mémoire tampon.  
  
-   Une couche telles que la couche de texte synthétique provient le texte doit fournir une implémentation locale de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   En outre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, une couche de texte doit implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et déclencher les événements dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personnaliser des menus et contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)