---
title: "Couleurs de syntaxe dans les &#233;diteurs personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - la coloration de syntaxe"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Couleurs de syntaxe dans les &#233;diteurs personnalis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éditeurs de l'environnement Kit de développement logiciel de Visual Studio, notamment l'éditeur principal, utilisent des services de langage pour identifier les éléments de syntaxe spécifiques et affichage avec des couleurs spécifiées pour une vue donnée de document.  
  
## Spécifications de la colorisation  
 Tous les éditeurs implémentant un coloriseur du service de langage doivent :  
  
1.  Utilisez un objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour gérer le texte à sont colorisés et un objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour fournir une vue du document du texte.  
  
2.  Obtenez une interface à un service de langage particulier en interrogeant le fournisseur de services du VSPackage à l'aide d'un GUID d'identification unique du service de langage.  
  
3.  Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> d'objet qui implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  Cette méthode associe le service de langage à l'implémentation d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que le VSPackage utilise pour gérer le texte qui doit sont colorisés.  
  
## Utilisation principale de l'éditeur d'un coloriseur du service de langage  
 Lorsqu'un service de langage avec un coloriseur est obtenu en une instance du éditeur principal, l'analyse et le rendu du texte par un coloriseur du service de langage se produit automatiquement sans autre intervention de votre part.  
  
 L'IDE de façon transparente :  
  
-   Appelle le coloriseur selon les besoins pour analyser et analyser le texte comme il est ajouté ou modifié dans l'implémentation d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Garantit que l'affichage fourni par la vue du document fournie par l'implémentation d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> est mis à jour et redessiné à l'aide de les informations retournées par le coloriseur.  
  
## Utilisation non fondamentale de l'éditeur d'un coloriseur du service de langage  
 Les instances de l'éditeur non fondamentales peuvent également utiliser un service de colorisation de la syntaxe du service de langage, mais elles doivent explicitement récupérer et appliquer le coloriseur du service et repeindre leur document s'affiche.  
  
 Pour cela requiert un éditeur non fondamental :  
  
1.  Obtenez un objet du coloriseur du service de langage \(qui implémente `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\).  Votre VSPackage procède en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> sur l'interface du service de langage.  
  
2.  Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour demander qu'une étendue de texte particulière sont colorisés.  
  
     La méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retourne un tableau de valeurs, une pour chaque lettre de l'étendue de texte sont colorisés.  Il identifie également l'étendue de texte en tant que type particulier d'élément coloriable, tel qu'un commentaire, un mot clé, ou un type de données.  
  
3.  Utilisez les informations de la colorisation retournées par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour redessiner et afficher son texte.  
  
> [!NOTE]
>  En plus de utiliser un coloriseur du service de langage, un VSPackage peut utiliser le mécanisme à usage général de texte\-coloration de l'environnement Kit de développement logiciel de Visual Studio.  Pour plus d'informations sur ce mécanisme, consultez [Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md).  
  
## Voir aussi  
 [Couleurs de syntaxe dans un Service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [L'implémentation de la coloration de syntaxe](../extensibility/internals/implementing-syntax-coloring.md)   
 [Comment : utiliser des éléments coloriable intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Éléments coloriable personnalisés](../extensibility/internals/custom-colorable-items.md)