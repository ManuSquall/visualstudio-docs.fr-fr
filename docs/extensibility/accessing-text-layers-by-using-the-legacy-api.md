---
title: "L&#39;acc&#232;s &#224; des calques de texte &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - calques de texte"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# L&#39;acc&#232;s &#224; des calques de texte &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une couche de texte encapsule en général un aspect de disposition du texte.  Par exemple, les masque d'une couche de « fonction\-à\-un\-fois » texte avant et après une fonction contenant le signe insertion \(point d'insertion de texte\).  
  
 Une couche de texte réside entre une mémoire tampon et une vue, et elle modifie la façon dont la vue comment afficher le contenu de la mémoire tampon.  
  
## Les informations de couche de texte  
 La liste suivante décrit comment les couches de texte s'exécutent dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Le texte dans une couche de texte peut être orné avec la coloration de syntaxe et le.  
  
-   Vous ne pouvez actuellement pas implémenter vos propres couches.  
  
-   une couche expose <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, qui est dérivée d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>.  La mémoire tampon de texte lui\-même est également implémentée en tant que couche, qui permet à une vue pour traiter polymorphically les couches sous\-jacentes.  
  
-   Plusieurs couches peuvent reposer entre l'affichage et la mémoire tampon.  Chaque couche traite uniquement la couche dessous, et la vue traite en grande partie de la couche supérieure.  \(La vue a des informations à propos de la mémoire tampon.\)  
  
-   Une couche peut affecter uniquement les couches inférieures à elle.  Il ne peut pas affecter les couches au\-dessus au delà de lancer les événements standard.  
  
-   Dans l'éditeur, le texte masqué, le texte synthétique, et le retour automatique à la ligne sont implémentées comme des couches.  vous pouvez implémenter le texte masqué et synthétique sans interagir directement avec les couches.  Pour plus d'informations, consultez [Mode plan dans un Service de langage hérité](../extensibility/internals/outlining-in-a-legacy-language-service.md) et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Chaque couche de texte a son propre système de coordonnées local qui est exposé via l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> .  La couche de ligne\-enveloppe, par exemple, peut contenir deux lignes pendant que la mémoire tampon sous\-jacente peut contenir qu'une seule ligne.  
  
-   La vue communique avec les couches via l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> .  Utilisez cette interface pour rapprocher des coordonnées de vue contenant les coordonnées de mémoire tampon.  
  
-   Toute couche comme la couche synthétique de texte qui lance le texte doit fournir une implémentation locale d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Outre l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, une couche de texte doit implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et déclencher des événements dans <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../extensibility/syntax-coloring-in-custom-editors.md)   
 [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personnalisation des Menus et contrôles d’édition à l’aide de l’API héritée](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)