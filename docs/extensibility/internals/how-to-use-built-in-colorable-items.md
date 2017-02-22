---
title: "Comment : utiliser des &#233;l&#233;ments coloriable int&#233;gr&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés"
  - "services de langage, les éléments coloriable intégrés"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment : utiliser des &#233;l&#233;ments coloriable int&#233;gr&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avant d'utiliser les éléments qui autorisent la modification de la couleur prédéfinis, vous devez d'abord signaler à l'environnement de \(IDE\) développement intégré à ne pas fournir vos propres éléments qui autorisent la modification de la couleur personnalisés, qui dans ce cas sont des objets d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> .  Vous faites ceci en définissant une entrée de Registre pour le service de langage.  
  
### Pour utiliser les éléments qui autorisent la modification de la couleur prédéfinis  
  
1.  Sous HKEY\_LOCAL\_MACHINE \\VisualStudio \\*X.Y*\\Languages\\Language Services \\*nom de langue*, où *X.Y* est une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et *nom de langue* est le nom de votre langage, créez une valeur d'entrée du Registre DWORD `RequestStockColors`appelé.  
  
2.  Affectez à la valeur d'entrée du Registre d' `RequestStockColors` à 1.  
  
     Après avoir créé l'entrée du Registre, la méthode de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> de votre coloriseur peut utiliser des membres de l'énumération d' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> pour terminer le tableau d'attributs de couleur pour l'éditeur.  
  
    > [!NOTE]
    >  Ne définissez pas cette entrée du Registre si vous fournissez des éléments qui autorisent la modification de la couleur personnalisés.  Pour plus d'informations, consultez [Éléments coloriable personnalisés](../../extensibility/internals/custom-colorable-items.md).  
  
## Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [L'implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Éléments coloriable personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)