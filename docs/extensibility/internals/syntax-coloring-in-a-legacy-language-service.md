---
title: Coloration de la syntaxe dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186319"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité

Visual Studio utilise un service de coloration pour identifier les éléments du langage et les afficher avec les couleurs spécifiées dans un éditeur.

## <a name="colorizer-model"></a>Modèle Coloriseur
 Le service de langage implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, qui est ensuite utilisée par les éditeurs. Cette implémentation est un objet distinct du service de langage, comme indiqué dans l’illustration suivante :

 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Le service de coloration de syntaxe est distinct du mécanisme général Visual Studio pour coloriser le texte. Pour plus d’informations sur le mécanisme de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] général qui prend en charge la coloration, consultez [utilisation des polices et des couleurs](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Outre le Coloriseur, le service de langage peut fournir des éléments coloriables personnalisés qui sont utilisés par l’éditeur, en annonçant qu’il fournit des éléments coloriables personnalisés. Pour ce faire, vous pouvez implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> sur le même objet qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Elle retourne le nombre d’éléments coloriables personnalisés lorsque l’éditeur appelle la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et retourne un élément coloriable personnalisé individuel lorsque l’éditeur appelle la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 La méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> retourne un objet qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Si le service de langage prend en charge les valeurs de couleur 24 bits ou élevées, il doit implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> sur le même objet que l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Comment un VSPackage utilise un service de langage Coloriseur

1. Le VSPackage doit disposer du service de langage approprié, qui nécessite que le VSPackage du service de langage effectue les opérations suivantes :

    1. Utilisez un objet qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour que le texte soit mis en couleur.

         Le texte est généralement affiché à l’aide d’un objet qui implémente l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Procurez-vous le service de langage en interrogeant le fournisseur de services du VSPackage pour connaître le GUID du service de langage. Les services de langage sont identifiés dans le registre par l’extension de fichier.

    3. Associez le service de langage au <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en appelant sa méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. Le VSPackage peut maintenant obtenir et utiliser l’objet Coloriseur comme suit :

    > [!NOTE]
    > Les VSPackages qui utilisent l’éditeur principal n’ont pas besoin d’obtenir explicitement les objets Coloriseur d’un service de langage. Dès qu’une instance de l’éditeur principal obtient un service de langage approprié, il effectue toutes les tâches de colorisation indiquées ici.

    1. Obtenez l’objet Coloriseur du service de langage, qui implémente les interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>, en appelant la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> sur l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> du service de langage.

    2. Appelez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour obtenir les informations de Coloriseur pour une étendue de texte particulière.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retourne un tableau de valeurs, une pour chaque caractère de l’étendue de texte qui est coloriée. Les valeurs sont des index dans une liste d’éléments coloriables qui est soit la liste d’éléments de couleur par défaut gérée par l’éditeur principal, soit une liste d’éléments coloriable personnalisée gérée par le service de langage lui-même.

    3. Utilisez les informations de colorisation retournées par la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour afficher le texte sélectionné.

> [!NOTE]
> Outre l’utilisation d’un service de langage Coloriseur, un VSPackage peut également utiliser le mécanisme de coloration de texte de Visual Studio à usage général. Pour plus d’informations sur ce mécanisme, consultez [utilisation des polices et des couleurs](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Dans cette section
- [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Explique comment un éditeur accède à la coloration de la syntaxe d’un service de langage et ce que le service de langage doit implémenter pour prendre en charge la coloration de la syntaxe.

- [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Montre comment utiliser des éléments coloriables intégrés à partir du service de langage.

- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)

 Explique comment implémenter des éléments coloriables personnalisés.