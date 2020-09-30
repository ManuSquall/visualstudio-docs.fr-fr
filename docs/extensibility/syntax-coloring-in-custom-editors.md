---
title: Coloration de la syntaxe dans les éditeurs personnalisés | Microsoft Docs
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
ms.openlocfilehash: dec1cf1e3ec4301b1f219f7345957877ea420528
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585639"
---
# <a name="syntax-coloring-in-custom-editors"></a>Couleurs de syntaxe dans les éditeurs personnalisés
Éditeurs du kit de développement logiciel (SDK) de l’environnement Visual Studio, y compris l’éditeur de base, utilisent les services de langage pour identifier des éléments syntaxiques spécifiques et les afficher avec les couleurs spécifiées pour un affichage de document donné.

## <a name="colorization-requirements"></a>Exigences en matière de colorisation
 Tous les éditeurs qui implémentent le Coloriseur d’un service de langage doivent :

1. Utilisez un objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour gérer le texte à colorer et un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> qui implémente pour fournir une vue de document du texte.

2. Obtenez une interface pour un service de langage particulier en interrogeant le fournisseur de services du VSPackage à l’aide du GUID d’identification du service de langages.

3. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode de l’objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Cette méthode associe le service de langage à l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implémentation que le VSPackage utilise pour gérer le texte à colorer.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilisation par l’éditeur principal de l’Coloriseur d’un service de langage
 Lorsqu’un service de langage avec un Coloriseur est obtenu par une instance de l’éditeur principal, l’analyse et le rendu du texte par le Coloriseur d’un service de langage se produit automatiquement sans nécessiter d’autre intervention de votre part.

 L’IDE de manière transparente :

- Appelle le Coloriseur en fonction des besoins pour analyser et analyser le texte au fur et à mesure de son ajout ou de sa modification dans l’implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Garantit que l’affichage fourni par l’affichage de document fourni par l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implémentation est mis à jour et repeint à l’aide des informations retournées par le Coloriseur.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Éditeur non principal utilisation du Coloriseur d’un service de langage
 Les instances de l’éditeur non-Core peuvent également utiliser le service de colorisation de syntaxe du service de langage, mais elles doivent récupérer et appliquer explicitement le Coloriseur du service, puis repeindre leurs vues de document.

 Pour ce faire, un éditeur non principal doit :

1. Obtenez l’objet Coloriseur d’un service de langage (qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Pour ce faire, le VSPackage appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l’interface du service de langage.

2. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour demander qu’une étendue de texte particulière soit coloriée.

     La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode retourne un tableau de valeurs, une pour chaque lettre de l’étendue de texte qui est coloriée. Elle identifie également l’étendue de texte en tant que type particulier d’élément coloriable, tel qu’un commentaire, un mot clé ou un type de données.

3. Utilisez les informations de colorisation retournées par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour redessiner et afficher son texte.

> [!NOTE]
> Outre l’utilisation du Coloriseur d’un service de langage, un VSPackage peut choisir d’utiliser le mécanisme de coloration de texte du kit de développement logiciel (SDK) de l’environnement Visual Studio à usage général. Pour plus d’informations sur ce mécanisme, consultez [utilisation des polices et des couleurs](../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015&preserve-view=true).

## <a name="see-also"></a>Voir aussi

- [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentation de la coloration de syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Guide pratique pour utiliser des éléments coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md)