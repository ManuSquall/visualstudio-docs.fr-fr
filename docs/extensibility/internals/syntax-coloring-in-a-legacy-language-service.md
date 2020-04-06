---
title: Coloriage Syntax dans un service de langue héritée (fr) Microsoft Docs
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
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704758"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Couleurs de syntaxe dans un service de langage hérité

Visual Studio utilise un service de coloriage pour identifier les éléments de la langue et les afficher avec les couleurs spécifiées dans un éditeur.

## <a name="colorizer-model"></a>Modèle colorisant
 Le service linguistique <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> implémente l’interface, qui est ensuite utilisée par les éditeurs. Cette implémentation est un objet distinct du service linguistique, comme le montre l’illustration suivante :

 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Le service de coloriage syntaxe est distinct du mécanisme général Visual Studio pour coloriser le texte. Pour plus d’informations sur le mécanisme général [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] soutenant la colorisation, voir Using [Fonts and Colors](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Outre le coloriseur, le service de langue peut fournir des articles colorables personnalisés qui sont utilisés par l’éditeur, en annonçant qu’il fournit des articles colorables personnalisés. Vous pouvez le faire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> en implémentant l’interface sur le même objet qui implémente l’interface. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Il renvoie le nombre d’éléments colorables personnalisés lorsque l’éditeur appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode, et il renvoie un élément colorable personnalisé lorsque l’éditeur appelle la méthode.

 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode renvoie un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objet qui implémente l’interface. Si le service linguistique prend en charge des valeurs de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> couleur 24 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> ou élevées, il doit implémenter l’interface sur le même objet que l’interface.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Comment un VSPackage utilise un colorant de service de langue

1. Le VSPackage doit obtenir le service linguistique approprié, qui exige que le service linguistique VSPackage fasse ce qui suit :

    1. Utilisez un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implémentant l’interface pour colorier le texte.

         Le texte est généralement affiché à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> l’aide d’un objet qui implémente l’interface.

    2. Obtenez le service linguistique en interrogeant le fournisseur de services de la VSPackage pour le service linguistique GUID. Les services linguistiques sont identifiés dans le registre par extension de dossier.

    3. Associez le service <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> linguistique <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> au fait d’appeler sa méthode.

2. Le VSPackage peut maintenant obtenir et utiliser l’objet colorateur comme suit:

    > [!NOTE]
    > VSPackages qui utilisent l’éditeur de base n’ont pas à obtenir les objets colorisants d’un service linguistique explicitement. Dès qu’un exemple de l’éditeur de base obtient un service linguistique approprié, il effectue toutes les tâches de colorisation montrées ici.

    1. Obtenez l’objet colorisant du service linguistique, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> le , et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interfaces, en appelant la méthode sur l’objet du service linguistique.

    2. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> la méthode pour obtenir les informations colorisant pour une durée particulière de texte.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>retourne un éventail de valeurs, une pour chaque personnage dans la durée de texte étant colorisée. Les valeurs sont des index dans une liste d’éléments colorables qui est soit la liste d’éléments colorables par défaut maintenue par l’éditeur de base ou une liste d’éléments colorables personnalisés maintenues par le service linguistique lui-même.

    3. Utilisez les informations de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> colorisation retournées par la méthode pour afficher le texte sélectionné.

> [!NOTE]
> En plus d’utiliser un colorant de service de langue, un VSPackage peut également utiliser le mécanisme général de coloriage de texte Visual Studio. Pour plus d’informations sur ce mécanisme, voir [Using Fonts and Colors](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Dans cette section
- [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Discute de la façon dont un éditeur accède à la coloration syntaxe d’un service linguistique et ce que le service linguistique doit mettre en œuvre pour soutenir la coloration syntaxe.

- [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Démontre comment utiliser des articles colorables intégrés du service linguistique.

- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)

 Discute de la façon d’implémenter des articles colorables personnalisés.
