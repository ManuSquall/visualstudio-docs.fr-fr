---
title: Accès aux couches de texte à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148023"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Accès aux couches de texte à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une couche de texte encapsule généralement un aspect de la disposition du texte. Par exemple, une couche « fonction à la fois » masque le texte avant et après une fonction contenant le signe insertion (point d’insertion de texte).  
  
 Une couche de texte réside entre une mémoire tampon et une vue, et elle modifie la façon dont la vue voit le contenu de la mémoire tampon.  
  
## <a name="text-layer-information"></a>Informations sur la couche de texte  
 La liste suivante décrit le fonctionnement des couches de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Le texte d’une couche de texte peut être orné avec les couleurs de syntaxe et les marqueurs.  
  
- Actuellement, vous ne pouvez pas implémenter vos propres couches.  
  
- Une couche expose <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , qui est dérivée de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . La mémoire tampon de texte elle-même est également implémentée en tant que couche, ce qui permet à une vue de gérer les manière polymorphe avec les couches sous-jacentes.  
  
- Un nombre quelconque de couches peut se situer entre la vue et la mémoire tampon. Chaque couche traite uniquement la couche située au-dessous, et la vue traite en grande partie avec la couche la plus haute. (La vue contient des informations sur la mémoire tampon.)  
  
- Une couche peut affecter uniquement les couches qui se trouvent en dessous de celle-ci. Il ne peut pas affecter les couches qui le précèdent au-delà des événements standard d’origine.  
  
- Dans l’éditeur, le texte masqué, le texte synthétique et le retour automatique à la ligne sont implémentés en tant que couches. Vous pouvez implémenter du texte masqué et synthétique sans interagir directement avec les couches. Pour plus d’informations, consultez [mode plan dans un service de langage hérité](../extensibility/internals/outlining-in-a-legacy-language-service.md) et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Chaque couche de texte a son propre système de coordonnées local qui est exposé par le biais de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interface. La couche de retour à la ligne, par exemple, peut contenir deux lignes tandis que la mémoire tampon sous-jacente ne peut contenir qu’une seule ligne.  
  
- La vue communique avec les couches par le biais de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interface. Utilisez cette interface pour rapprocher les coordonnées de vue avec des coordonnées de mémoire tampon.  
  
- Toute couche, telle que la couche de texte synthétique qui provient du texte, doit fournir une implémentation locale de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>En outre, une couche de texte doit implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et déclencher les événements dans l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Coloration de la syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personnalisation des contrôles et menus de l’éditeur à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
