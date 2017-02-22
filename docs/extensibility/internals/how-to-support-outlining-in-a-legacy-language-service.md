---
title: "Comment&#160;: prendre en charge le mode plan dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), réduire à la commande de définitions"
  - "services de langage prenant en charge de réduire à la commande de définitions"
  - "texte masqué, réduire à la commande de définitions"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: prendre en charge le mode plan dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le mode plan est utilisé pour développer ou réduire les différentes zones de texte. Le plan moyen utilisé peuvent être définies différemment dans des langages différents. Pour plus d'informations, consultez [Mode Plan](../../ide/outlining.md).  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter le mode plan, consultez [Procédure pas à pas : mise en relief](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Ce qui suit montre comment prendre en charge cette commande pour votre service de langage.  
  
### Pour prendre en charge le mode plan  
  
1.  Implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sur votre objet de service de langage.  
  
2.  Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sur l’objet de session en mode plan actuel pour ajouter de nouvelles régions en mode plan.  
  
## Programmation fiable  
 Lorsqu’un utilisateur sélectionne **réduire aux définitions** sur la **mode plan** menu, les appels IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> sur votre service de langage.  
  
 Lorsque cette méthode est appelée, l’IDE passe un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> pointeur \(un pointeur vers une mémoire tampon de texte\) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(un pointeur vers la session active en mode plan\).  
  
 Vous pouvez appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> méthode pour plusieurs régions en mode plan en spécifiant ces régions dans le `rgOutlnReg` paramètre. Le `rgOutlnReg` paramètre est un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> structure. Ce processus vous permet de spécifier différentes caractéristiques de la zone masquée, par exemple si une région particulière est développée ou réduite.  
  
> [!NOTE]
>  Soyez prudent sur le masquage des caractères de nouvelle ligne. Texte masqué doit s’étendre à partir du début de la première ligne au dernier caractère de la dernière ligne dans une section, en laissant le dernier caractère de saut de ligne est visible.  
  
## Voir aussi  
 [Comment : fournir la prise en charge du texte masqué dans un Service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Comment : fournir une prise en charge étendue de plan dans un Service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)