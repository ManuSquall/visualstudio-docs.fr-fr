---
title: "Couleurs de syntaxe dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "coloration de syntaxe"
  - "services de langage, la coloration de syntaxe"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Couleurs de syntaxe dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise un service de coloration pour identifier des éléments du langage et de les afficher avec des couleurs spécifiées dans un éditeur.  
  
## modèle de coloriseur  
 Le service de langage implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> , qui est ensuite utilisée par les éditeurs.  Cette implémentation est un objet distinct du service de langage, comme indiqué dans l'illustration suivante.  
  
 ![Graphique Coloriseur SVC](../../extensibility/internals/media/figlgsvccolorizer.png "FigLgSvcColorizer")  
modèle simple de coloriseur  
  
> [!NOTE]
>  le service de coloration de syntaxe est séparé du mécanisme de général [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour le texte colorizing.  Pour plus d'informations sur le mécanisme de général [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] prenant en charge colorizing, consultez [Utilisation de polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
 En plus de le coloriseur, le service de langage peut fournir des éléments qui autorisent la modification de la couleur personnalisés utilisés par l'éditeur en publiant ce qui fournissent les éléments qui autorisent la modification de la couleur personnalisés.  Vous pouvez le faire en implémentant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> sur le même objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Il retourne le nombre d'éléments personnalisés qui autorisent la modification de la couleur lorsque l'éditeur appelle la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> , et elle retourne un élément coloriable personnalisé spécifique lorsque l'éditeur appelle la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
 La méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> retourne un objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  Si le service prend en charge du langage 24 bits ou des valeurs de 65536 couleurs, il doit implémenter l'interface de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> sur le même objet que l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  
  
## Comment un VSPackage utilise un coloriseur de service de langage  
  
1.  Le VSPackage doit obtenir le service de langage appropriée, qui exige du service de langage VSPackage pour effectuer les opérations suivantes :  
  
    1.  Utilisez un objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour obtenir le texte pour sont colorisés.  
  
         Le texte est généralement affichée à l'aide d'un objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
    2.  Obtenez le service de langage en interrogeant le fournisseur de services du VSPackage pour le service de langage GUID.  Les services linguistiques sont identifiés dans le Registre par l'extension.  
  
    3.  Associez le service de langage avec <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en appelant sa méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .  
  
2.  le VSPackage peut maintenant obtenir et utiliser l'objet de coloriseur comme suit :  
  
    > [!NOTE]
    >  VSPackages qui utilisent l'éditeur principal ne doivent pas obtenir des objets du coloriseur d'un service de langage explicitement.  Dès qu'une instance du éditeur principal obtiendra un service de langage de langue appropriée, elle effectue toutes les tâches de la colorisation présentées ici.  
  
    1.  Obtenez l'objet du coloriseur du service de langage, qui implémente `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, et les interfaces d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> sur l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> du service de langage.  
  
    2.  Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour obtenir des informations de coloriseur pour une étendue de texte particulière.  
  
         l'<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> retourne un tableau de valeurs, une pour chaque caractère de l'étendue de texte sont colorisés.  Les valeurs sont des index dans une liste d'éléments coloriable qui est la liste d'éléments coloriable par défaut contenue par l'éditeur principal ou une liste d'éléments coloriable personnalisée gérée par le service de langage lui\-même.  
  
    3.  Utilisez les informations de la colorisation retournées par la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> pour afficher le texte sélectionné.  
  
> [!NOTE]
>  En plus de utiliser un coloriseur de service de langage, un VSPackage peut également utiliser le mécanisme à usage général de coloration de texte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Pour plus d'informations sur ce mécanisme, consultez [Utilisation de polices et couleurs](../../extensibility/using-fonts-and-colors.md).  
  
## Dans cette section  
 [L'implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)  
 Décrit comment un éditeur accède à une coloration de syntaxe du service de langage et le contenu du service de langage doit implémenter pour prendre en charge la coloration de syntaxe.  
  
 [Comment : utiliser des éléments coloriable intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Montre comment utiliser les éléments qui autorisent la modification de la couleur prédéfinis du service de langage.  
  
 [Éléments coloriable personnalisés](../../extensibility/internals/custom-colorable-items.md)  
 Explique comment implémenter les éléments qui autorisent la modification de la couleur personnalisés.  
  
## Voir aussi  
 [Utilisation de polices et couleurs](../../extensibility/using-fonts-and-colors.md)