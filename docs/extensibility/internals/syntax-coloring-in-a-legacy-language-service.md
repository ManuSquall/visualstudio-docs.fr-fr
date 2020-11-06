---
title: Coloration de la syntaxe dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d0cc0dcf40ab9231e3af6208ab2f844c69f3398
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414553"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité

Visual Studio utilise un service de coloration pour identifier les éléments du langage et les afficher avec les couleurs spécifiées dans un éditeur.

## <a name="colorizer-model"></a>Modèle Coloriseur
 Le service de langage implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface, qui est ensuite utilisée par les éditeurs. Cette implémentation est un objet distinct du service de langage, comme indiqué dans l’illustration suivante :

 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Le service de coloration de syntaxe est distinct du mécanisme général Visual Studio pour coloriser le texte. Pour plus d’informations sur le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mécanisme général de prise en charge de la coloration, consultez [utilisation des polices et des couleurs](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

 Outre le Coloriseur, le service de langage peut fournir des éléments coloriables personnalisés qui sont utilisés par l’éditeur, en annonçant qu’il fournit des éléments coloriables personnalisés. Pour ce faire, vous pouvez implémenter l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface sur le même objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface. Elle retourne le nombre d’éléments coloriables personnalisés lorsque l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> méthode et retourne un élément coloriable personnalisé individuel lorsque l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode.

 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode retourne un objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface. Si le service de langage prend en charge les valeurs de couleur 24 bits ou élevées, il doit implémenter l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface sur le même objet que l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interface.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Comment un VSPackage utilise un service de langage Coloriseur

1. Le VSPackage doit disposer du service de langage approprié, qui nécessite que le VSPackage du service de langage effectue les opérations suivantes :

    1. Utilisez un objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface pour faire en sorte que le texte soit mis en couleur.

         Le texte est généralement affiché à l’aide d’un objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.

    2. Procurez-vous le service de langage en interrogeant le fournisseur de services du VSPackage pour connaître le GUID du service de langage. Les services de langage sont identifiés dans le registre par l’extension de fichier.

    3. Associez le service de langage au <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en appelant sa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode.

2. Le VSPackage peut maintenant obtenir et utiliser l’objet Coloriseur comme suit :

    > [!NOTE]
    > Les VSPackages qui utilisent l’éditeur principal n’ont pas besoin d’obtenir explicitement les objets Coloriseur d’un service de langage. Dès qu’une instance de l’éditeur principal obtient un service de langage approprié, il effectue toutes les tâches de colorisation indiquées ici.

    1. Obtenez l’objet Coloriseur du service de langage, qui implémente les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaces, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l’objet du service de langage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour obtenir les informations de Coloriseur pour une étendue de texte particulière.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retourne un tableau de valeurs, une pour chaque caractère de l’étendue de texte qui est coloriée. Les valeurs sont des index dans une liste d’éléments coloriables qui est soit la liste d’éléments de couleur par défaut gérée par l’éditeur principal, soit une liste d’éléments coloriable personnalisée gérée par le service de langage lui-même.

    3. Utilisez les informations de colorisation retournées par la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour afficher le texte sélectionné.

> [!NOTE]
> Outre l’utilisation d’un service de langage Coloriseur, un VSPackage peut également utiliser le mécanisme de coloration de texte de Visual Studio à usage général. Pour plus d’informations sur ce mécanisme, consultez [utilisation des polices et des couleurs](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="in-this-section"></a>Dans cette section
- [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Explique comment un éditeur accède à la coloration de la syntaxe d’un service de langage et ce que le service de langage doit implémenter pour prendre en charge la coloration de la syntaxe.

- [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Montre comment utiliser des éléments coloriables intégrés à partir du service de langage.

- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)

 Explique comment implémenter des éléments coloriables personnalisés.