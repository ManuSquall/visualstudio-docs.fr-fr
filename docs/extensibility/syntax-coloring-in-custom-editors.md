---
title: Couleurs de syntaxe dans les éditeurs personnalisés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139459"
---
# <a name="syntax-coloring-in-custom-editors"></a>Couleurs de syntaxe dans les éditeurs personnalisés
Éditeurs de Visual Studio environnement SDK, y compris l’éditeur principal, utilisent les services de langage pour identifier les éléments syntaxiques spécifiques et de les afficher avec les couleurs spécifiées pour une vue de document donné.

## <a name="colorization-requirements"></a>Configuration requise de colorisation
 Tous les éditeurs de mise en œuvre de Coloriseur d’un service langage doivent :

1.  Utiliser un objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour gérer le texte à une autre couleur et un objet implémentant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour fournir une vue de document du texte.

2.  Obtenir une interface pour un service de langage particulier en interrogeant le fournisseur de services le VSPackage à l’aide du GUID d’identification du service de langues.

3.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode de l’objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Cette méthode associe le service de langage à le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implémentation VSPackage utilise pour gérer le texte à une autre couleur.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilisation d’éditeur principal de Coloriseur d’un Service langage
 Lorsqu’un service de langage avec un Coloriseur est obtenu par une instance de l’éditeur principal, l’analyse et le rendu de texte par Coloriseur d’un service langage s’effectue automatiquement sans aucune intervention supplémentaire de votre part.

 L’IDE en toute transparence :

-   Appelle la Coloriseur en fonction des besoins d’analyser et d’analyser le texte qu’elle est ajoutée ou modifiée dans l’implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Garantit que l’affichage fourni par la vue de document fournie par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implémentation est mis à jour et mis à jour en utilisant les informations retournées par le Coloriseur.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilisation de l’éditeur non principales de Coloriseur d’un Service langage
 Instances de l’éditeur d’auxiliaires peuvent également utiliser service de coloration de syntaxe d’un service de langage, mais ils doivent explicitement récupérer et appliquer les Coloriseur du service et repeindre leur point de vue de document eux-mêmes.

 Pour ce faire, un éditeur non principal doit :

1.  Obtenir un objet de Coloriseur d’un service de langage (qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Le VSPackage cela en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l’interface du service de langage.

2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour demander qu’une étendue particulière de texte d’une autre couleur.

     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode retourne un tableau de valeurs, d’un pour chaque lettre dans le texte mis en couleur. Il identifie également l’étendue de texte comme un type particulier d’élément coloriable, par exemple un commentaire, le mot clé ou le type de données.

3.  Utilisez les informations de colorisation retournées par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour repeindre et afficher son texte.

> [!NOTE]
> Outre l’utilisation de Coloriseur d’un service langage, un VSPackage peut choisir d’utiliser le mécanisme de coloration de texte Visual Studio environnement SDK à usage général. Pour plus d’informations sur ce mécanisme, consultez [à l’aide des polices et couleurs](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Voir aussi

- [Couleurs de syntaxe dans un service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentation de la coloration de syntaxe](../extensibility/internals/implementing-syntax-coloring.md)
- [Guide pratique pour utiliser des éléments coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md)