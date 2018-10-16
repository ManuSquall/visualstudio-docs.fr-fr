---
title: Couleurs de syntaxe dans un Service de langage hérité | Microsoft Docs
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
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f57d4c8b3c606fa5f954755d6a7f07c2ab00a89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253837"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilise un service de coloration pour identifier les éléments du langage et de les afficher avec les couleurs spécifiées dans un éditeur.  
  
## <a name="colorizer-model"></a>Modèle de Coloriseur  
 Le service de langage implémente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface, qui est ensuite utilisé par les éditeurs. Cette implémentation est un objet distinct du service de langage, comme indiqué dans l’illustration suivante.  
  
 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modèle de Coloriseur simple  
  
> [!NOTE]
>  La service de coloration de la syntaxe est distincte à partir de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mécanisme pour la colorisation de texte. Pour plus d’informations sur le grand [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mécanisme prenant en charge la colorisation, consultez [à l’aide des polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
 Outre le Coloriseur, le service de langage peut fournir des éléments coloriables personnalisés qui sont utilisés par l’éditeur par la publicité qu’il fournit les éléments coloriables personnalisés. Vous pouvez le faire en implémentant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface sur le même objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Elle retourne le nombre d’éléments coloriables personnalisés lors de l’éditeur appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> méthode et qu’elle retourne un élément coloriable personnalisé lorsque l’éditeur appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (méthode).  
  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode retourne un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface. Si le service de langage prend en charge les valeurs de couleur 24 bits ou élevé, il doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface sur le même objet que le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Comment un VSPackage utilise un Coloriseur de Service de langage  
  
1.  Le VSPackage doit obtenir le service de langage approprié, ce qui oblige le service de langage VSPackage effectuer les opérations suivantes :  
  
    1.  Utiliser un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface permettant d’obtenir le texte à mettre en couleur.  
  
         Texte est généralement affiché à l’aide d’un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
    2.  Obtenir le service de langage en interrogeant le fournisseur de services du VSPackage du service de langage GUID. Services de langage sont identifiées dans le Registre par extension de fichier.  
  
    3.  Associer le service de langage avec le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en appelant son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> (méthode).  
  
2.  Le VSPackage peut désormais obtenir et utiliser l’objet de Coloriseur comme suit :  
  
    > [!NOTE]
    >  Les VSPackages qui utilisent l’éditeur principal n’est pas obligé d’obtenir explicitement les objets de Coloriseur du service un langage. Dès qu’une instance de l’éditeur principal Obtient un service de langage approprié, il effectue toutes les tâches de colorisation indiqués ici.  
  
    1.  Obtenir un objet de Coloriseur du service de langage, qui implémente le `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfaces, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur le service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objet.  
  
    2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour obtenir les informations de Coloriseur pour une étendue particulière de texte.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Retourne un tableau de valeurs, un pour chaque caractère dans l’étendue de texte mis en couleur. Les valeurs sont des index dans une liste d’élément coloriable est la liste d’élément coloriable par défaut gérée par l’éditeur principal ou une liste de l’élément coloriable personnalisé géré par le service de langage lui-même.  
  
    3.  Utilisez les informations de colorisation retournées par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour afficher le texte sélectionné.  
  
> [!NOTE]
>  Outre un Coloriseur de service de langage, un VSPackage peut utiliser l’à usage général [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mécanisme de coloration de texte. Pour plus d’informations sur ce mécanisme, consultez [à l’aide des polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Explique comment un éditeur accède à un service de langage la coloration syntaxique et ce que le service de langage doit implémenter pour prendre en charge la syntaxe de la coloration de la.  
  
 [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Montre comment utiliser des éléments coloriables prédéfinis à partir du service de langage.  
  
 [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)  
 Explique comment implémenter des éléments coloriables personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des polices et des couleurs](../../extensibility/using-fonts-and-colors.md)

