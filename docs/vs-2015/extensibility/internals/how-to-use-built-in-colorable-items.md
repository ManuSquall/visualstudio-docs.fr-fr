---
title: 'Comment : utiliser des éléments coloriables intégrés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839406"
---
# <a name="how-to-use-built-in-colorable-items"></a>Guide pratique pour utiliser des éléments coloriables intégrés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avant d’utiliser les éléments coloriables intégrés, vous devez d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas vos propres éléments coloriables personnalisés, qui, dans ce cas, sont des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objets. Pour ce faire, vous devez définir une entrée de Registre pour le service de langage.  
  
### <a name="to-use-built-in-colorable-items"></a>Pour utiliser des éléments coloriables intégrés  
  
1. Sous HKEY_LOCAL_MACHINE \VisualStudio \\ *x. y*\Languages\Language services \\ *Language Name*, où *X. y* est une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et le nom de la *langue* est le nom de votre langue, créez une valeur d’entrée de Registre DWORD appelée `RequestStockColors` .  
  
2. Définissez la `RequestStockColors` valeur de l’entrée de Registre sur 1.  
  
     Après avoir créé l’entrée de Registre, la méthode de votre Coloriseur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> peut utiliser les membres de l' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> énumération pour remplir le tableau d’attributs de couleur en vue de son utilisation par l’éditeur.  
  
    > [!NOTE]
    > Ne définissez pas cette entrée de Registre si vous fournissez des éléments coloriables personnalisés. Pour plus d’informations, consultez [éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Coloration de la syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Coloration de la syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration de la syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)
