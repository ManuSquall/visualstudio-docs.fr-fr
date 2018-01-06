---
title: "Couleurs de syntaxe dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd740c437fc7e5f3d355e883d4023bc6edfcde1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un Service de langage hérité
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise un service de coloration de la syntaxe pour identifier les éléments du langage et de les afficher avec les couleurs spécifiées dans un éditeur.  
  
## <a name="colorizer-model"></a>Modèle de Coloriseur  
 Le service de langage implémente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface, qui est ensuite utilisé par les éditeurs. Cette implémentation est un objet distinct à partir du service de langage, comme indiqué dans l’illustration suivante.  
  
 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Modèle de Coloriseur simple  
  
> [!NOTE]
>  Service de coloration de la syntaxe est distincte à partir de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mécanisme pour Coloriser texte. Pour plus d’informations sur les utilisateurs [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mécanisme prenant en charge la colorisation, consultez [à l’aide des polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
 Outre le Coloriseur, le service de langage peut fournir des éléments coloriable personnalisés qui sont utilisées par l’éditeur en publicité qu’il fournit les éléments coloriable personnalisés. Ce faire, vous pouvez implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface sur le même objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Elle retourne le nombre d’éléments coloriable personnalisés lorsque l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (méthode), qui retourne un élément coloriable personnalisé lorsque l’éditeur appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (méthode).  
  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode retourne un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface. Si le service de langage prend en charge les valeurs de couleur 24 bits ou trop élevée, il doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface sur le même objet que le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Comment un VSPackage utilise un Coloriseur de Service de langage  
  
1.  Le VSPackage doit obtenir le service de langage approprié, ce qui nécessite le service de langage VSPackage pour effectuer les opérations suivantes :  
  
    1.  Utiliser un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface à obtenir le texte à une autre couleur.  
  
         Texte s’affiche généralement à l’aide d’un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
    2.  Obtenir le service de langage en interrogeant le fournisseur de services du VSPackage pour le GUID du service de langage. Les services de langage sont identifiées dans le Registre, par extension de fichier.  
  
    3.  Associer le service de langage avec la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en appelant son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> (méthode).  
  
2.  Le VSPackage peut désormais obtenir et utiliser l’objet Coloriseur comme suit :  
  
    > [!NOTE]
    >  Les VSPackages qui utilisent l’éditeur principal n’ont pas obtenir des objets de Coloriseur du service une langue explicitement. Dès qu’une instance de l’éditeur principal Obtient un service de langage approprié, il effectue toutes les tâches de colorisation indiqués ici.  
  
    1.  Obtenir un objet de service de langage Coloriseur, qui implémente le `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfaces, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur le service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objet.  
  
    2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour obtenir les informations de Coloriseur pour une étendue particulière du texte.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Retourne un tableau de valeurs, un pour chaque caractère dans l’étendue de texte mis en couleur. Les valeurs sont des index dans une liste de l’élément coloriable qui est la liste d’élément coloriable par défaut gérée par l’éditeur principal ou d’une liste de l’élément coloriable personnalisé géré par le service de langage lui-même.  
  
    3.  Utilisez les informations de colorisation retournées par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour afficher le texte sélectionné.  
  
> [!NOTE]
>  Outre un Coloriseur de service de langage, un VSPackage peut utiliser l’à usage général [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mécanisme de coloration de texte. Pour plus d’informations sur ce mécanisme, consultez [à l’aide des polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Explique comment un éditeur accède à un service de langage la coloration de syntaxe et ce que le service de langage doit implémenter pour prendre en charge la syntaxe de coloration du.  
  
 [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Montre comment utiliser les éléments intégrés coloriable à partir du service de langage.  
  
 [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)  
 Explique comment implémenter des éléments coloriable personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des polices et couleurs](../../extensibility/using-fonts-and-colors.md)