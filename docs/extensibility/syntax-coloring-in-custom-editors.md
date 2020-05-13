---
title: Coloriage Syntax dans les éditeurs personnalisés (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699340"
---
# <a name="syntax-coloring-in-custom-editors"></a>Couleurs de syntaxe dans les éditeurs personnalisés
Les éditeurs de Visual Studio Environment SDK, y compris l’éditeur de base, utilisent les services linguistiques pour identifier des éléments syntaxiques spécifiques et les afficher avec des couleurs spécifiées pour une vue de document donnée.

## <a name="colorization-requirements"></a>Exigences de colorisation
 Tous les éditeurs qui mettent en œuvre le coloriage d’un service linguistique doivent :

1. Utilisez un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implémentant pour gérer le texte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à coloriser et un objet implémentant pour fournir une vue de document du texte.

2. Obtenir une interface à un service linguistique particulier en interrogeant le fournisseur de services du VSPackage en utilisant le GUID d’identification du service de langues.

3. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> la méthode de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>mise en œuvre de l’objet . Cette méthode associe le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> service linguistique à la mise en œuvre que le VSPackage utilise pour gérer le texte qui doit être colorisé.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilisation de l’éditeur de base du coloriseur d’un service linguistique
 Lorsqu’un service linguistique avec colorateur est obtenu par un exemple de l’éditeur de base, l’analyse et le rendu du texte par le colorateur d’un service linguistique se produit automatiquement sans nécessiter d’intervention supplémentaire de votre part.

 L’IDE de manière transparente :

- Appelle le colorateur au besoin pour analyser et analyser le texte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>comme il est ajouté ou modifié dans la mise en œuvre de .

- Veille à ce que l’affichage fourni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> par la vue du document fourni par la mise en œuvre soit mis à jour et repeint à l’aide des informations retournées par le colorateur.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilisation non essentielle de l’éditeur du coloriseur d’un service linguistique
 Les instances d’éditeur non-core peuvent également utiliser le service de colorisation syntaxe d’un service linguistique, mais elles doivent explicitement récupérer et appliquer le colorant du service, et repeindre leurs vues de documents elles-mêmes.

 Pour ce faire, un éditeur non-core doit :

1. Obtenir l’objet colorisant d’un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> service <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>linguistique (qui met en œuvre et ). Le VSPackage le fait <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> en appelant la méthode sur l’interface du service linguistique.

2. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> la méthode pour demander qu’une durée particulière de texte soit colorisée.

     La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode renvoie un tableau de valeurs, une pour chaque lettre dans la durée de texte étant colorisée. Il identifie également la durée du texte comme un type particulier d’élément colorable, tel qu’un commentaire, un mot clé ou un type de données.

3. Utilisez les informations de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> colorisation retournées pour repeindre et afficher son texte.

> [!NOTE]
> En plus d’utiliser le coloriste d’un service linguistique, un VSPackage peut choisir d’utiliser le mécanisme général de coloriage de texte Visual Studio Environment SDK. Pour plus d’informations sur ce mécanisme, voir [Using Fonts and Colors](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Voir aussi

- [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentation de la coloration de syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Guide pratique pour utiliser des éléments coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md)
