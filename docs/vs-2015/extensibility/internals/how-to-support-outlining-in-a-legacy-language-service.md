---
title: 'Comment : prendre en charge le mode plan dans un Service de langage hérité | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97fb82459540e897d88283d0c09ba3a81b265c00
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299258"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Comment : prendre en charge le mode plan dans un Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le mode plan est utilisé pour développer ou réduire des différentes régions du texte. Le moyen le mode plan est utilisé peut être défini différemment par différents langages. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md).  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter le mode plan, consultez [procédure pas à pas : mise en relief](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Ce qui suit montre comment prendre en charge de cette commande pour votre service de langage.  
  
### <a name="to-support-outlining"></a>Pour prendre en charge le mode plan  
  
1.  Implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> sur votre objet de service de langage.  
  
2.  Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sur l’objet de session en mode plan actuel pour ajouter de nouvelles régions en mode plan.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Lorsqu’un utilisateur sélectionne **réduire aux définitions** sur le **mode plan** menu, les appels IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> sur votre service de langage.  
  
 Lorsque cette méthode est appelée, l’IDE passe un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> pointeur (il s’agit d’un pointeur vers une mémoire tampon de texte) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (il s’agit d’un pointeur vers la session active en mode plan).  
  
 Vous pouvez appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> méthode pour plusieurs régions en mode plan en spécifiant ces régions dans le `rgOutlnReg` paramètre. Le `rgOutlnReg` paramètre est un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> structure. Ce processus vous permet de pour spécifier des caractéristiques différentes de la zone masquée, telles que si une région particulière est développée ou réduite.  
  
> [!NOTE]
>  Soyez prudent sur le masquage des caractères de nouvelle ligne. Texte masqué est souhaitable d’étendre à partir du début de la première ligne au dernier caractère de la dernière ligne dans une section, en laissant le caractère de nouvelle ligne final est visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : fournir la prise en charge de texte masqué dans un Service de langage hérité](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Guide pratique pour fournir la prise en charge étendue du Mode Plan dans un service de langage hérité](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

