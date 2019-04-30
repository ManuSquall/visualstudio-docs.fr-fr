---
title: Couleurs de syntaxe dans les éditeurs personnalisés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444058"
---
# <a name="syntax-coloring-in-custom-editors"></a>Couleurs de syntaxe dans les éditeurs personnalisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Éditeurs de Visual Studio environnement SDK, y compris l’éditeur principal, utilisent les services de langage pour identifier les éléments syntaxiques spécifiques et de les afficher avec les couleurs spécifiées pour une vue de document donné.  
  
## <a name="colorization-requirements"></a>Exigences de colorisation  
 Tous les éditeurs de mise en œuvre de Coloriseur d’un service de langage doivent :  
  
1. Utiliser un objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour gérer le texte à mettre en couleur et qu’un objet implémentant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour fournir une vue de document du texte.  
  
2. Obtenir une interface pour un service de langage particulier en interrogeant le fournisseur de services du VSPackage à l’aide du GUID d’identification du service de langues.  
  
3. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> méthode de l’objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Cette méthode associe le service de langage avec le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implémentation VSPackage utilise pour gérer le texte est à mettre en couleur.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilisation de l’éditeur principal de Coloriseur d’un Service de langage  
 Lorsqu’un service de langage avec un Coloriseur est obtenu par une instance de l’éditeur principal, l’analyse et le rendu de texte par Coloriseur d’un service de langage se produit automatiquement sans aucune intervention supplémentaire de votre part.  
  
 L’IDE en toute transparence :  
  
- Appelle le Coloriseur en fonction des besoins pour analyser et d’analyser le texte comme il est ajouté ou modifié dans l’implémentation de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
- Garantit que l’affichage fourni par la vue de document fournie par le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implémentation est mis à jour et mis à jour en utilisant les informations retournées par le Coloriseur.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilisation de l’éditeur non-core de Coloriseur d’un Service de langage  
 Instances de l’éditeur de non-core peuvent également utiliser service de la coloration de syntaxe d’un service de langage, mais ils doivent explicitement récupérer et appliquer les Coloriseur du service et repeindre leurs vues de document eux-mêmes.  
  
 Pour ce faire, un éditeur non principales pour :  
  
1. Obtenir un objet de Coloriseur d’un service de langage (qui implémente `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Votre VSPackage pour cela, en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> méthode sur l’interface du service de langage.  
  
2. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode pour demander qu’une étendue particulière de texte d’une autre couleur.  
  
     Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode retourne un tableau de valeurs, une pour chaque lettre dans le texte s’étendent sur mis en couleur. Il identifie également l’étendue de texte comme un type particulier d’élément coloriable, tel qu’un commentaire, le mot clé ou le type de données.  
  
3. Utilisez les informations de colorisation retournées par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> de redessiner et afficher son texte.  
  
> [!NOTE]
> Outre l’utilisation de Coloriseur d’un service langage, un VSPackage peut choisir d’utiliser le mécanisme de coloration de texte Visual Studio environnement SDK à usage général. Pour plus d’informations sur ce mécanisme, consultez [à l’aide des polices et couleurs](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans un Service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration syntaxique](../extensibility/internals/implementing-syntax-coloring.md)   
 [Guide pratique pour Utiliser des éléments Coloriables intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Éléments coloriables personnalisés](../extensibility/internals/custom-colorable-items.md)
