---
title: "Comment : utiliser les éléments intégrés coloriable | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 545d5fa19182678ec1610fa7b689332e272f9962
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-built-in-colorable-items"></a>Comment : utiliser des éléments coloriable intégrés
Avant d’utiliser les éléments coloriable intégrés, vous devez tout d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas de vos propres éléments coloriable personnalisés, qu’il seraient dans ce cas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objets. Pour cela, en définissant une entrée de Registre pour le service de langage.  
  
### <a name="to-use-built-in-colorable-items"></a>Utilisation des éléments coloriable intégrés  
  
1.  Sous HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language Services\\*nom de la langue*, où *X.Y* est une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et *nom de la langue* est le nom de votre langue, créez une valeur d’entrée de Registre DWORD appelée `RequestStockColors`.  
  
2.  Définir le `RequestStockColors` valeur d’entrée de Registre à 1.  
  
     Après avoir créé l’entrée de Registre, votre Coloriseur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode peut utiliser les membres de le <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> énumération pour remplir le tableau d’attributs de couleur à utiliser par l’éditeur.  
  
    > [!NOTE]
    >  Ne définissez pas cette entrée de Registre si vous fournissez des éléments coloriable personnalisés. Pour plus d’informations, consultez [les éléments coloriable personnalisé](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Éléments coloriable personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)