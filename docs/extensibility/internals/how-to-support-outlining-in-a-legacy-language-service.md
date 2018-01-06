---
title: "Comment : prendre en charge le mode plan dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa57b0d09cb8422a9dde1f70306d2f3808b0384e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Comment : prendre en charge le mode plan dans un Service de langage hérité
Mode plan est utilisé pour développer ou réduire les différentes zones de texte. Le mode plan est utilisé peut être défini différemment par différents langages. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md).  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter le mode plan, consultez [procédure pas à pas : mise en relief](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Le texte suivant montre comment prendre en charge de cette commande pour votre service de langage.  
  
### <a name="to-support-outlining"></a>Pour prendre en charge le mode plan  
  
1.  Implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sur votre objet de service de langage.  
  
2.  Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sur l’objet de session en mode plan actuel pour ajouter de nouvelles régions en mode plan.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Lorsqu’un utilisateur sélectionne **réduire aux définitions** sur la **mode plan** menu, les appels IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> sur votre service de langage.  
  
 Lorsque cette méthode est appelée, l’IDE passe un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> pointeur (il s’agit d’un pointeur vers une mémoire tampon de texte) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (il s’agit d’un pointeur vers la session en mode plan).  
  
 Vous pouvez appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> méthode pour plusieurs régions en mode plan en spécifiant ces régions dans le `rgOutlnReg` paramètre. Le `rgOutlnReg` paramètre est un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> structure. Ce processus permet de spécifier différentes caractéristiques de la région masquée, par exemple si une région particulière est développée ou réduite.  
  
> [!NOTE]
>  Soyez prudent sur le masquage des caractères de nouvelle ligne. Texte masqué doit s’étendre à partir du début de la première ligne au dernier caractère de la dernière ligne dans une section, laissant le dernier caractère de saut de ligne visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : prendre en charge le texte masqué dans un Service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Guide pratique pour fournir la prise en charge étendue du Mode Plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)