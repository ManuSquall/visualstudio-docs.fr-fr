---
title: 'Comment : utiliser des éléments Coloriables intégrés | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b537c28f34faff1eff0502642236413f2ade2da1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942158"
---
# <a name="how-to-use-built-in-colorable-items"></a>Comment : utiliser des éléments coloriables intégrés
Avant d’utiliser des éléments colorables intégrés, vous devez tout d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas de vos propres éléments coloriables personnalisés, ce qui seraient dans ce cas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objets. Pour cela, vous devez en définissant une entrée de Registre pour le service de langage.  
  
## <a name="to-use-built-in-colorable-items"></a>Pour utiliser des éléments coloriables intégrés  
  
1. Sous **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language Services\\< nom de la langue\>**, où \<X.Y > est une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et \<Nom_langage > est le nom de votre langage, créez une valeur d’entrée de Registre DWORD appelée **RequestStockColors**.  
  
2. Définir le **RequestStockColors** valeur d’entrée de Registre à *1*.  
  
    Après avoir créé l’entrée de Registre, votre Coloriseur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode peut utiliser les membres de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> énumération pour remplir le tableau d’attributs de couleur pour une utilisation par l’éditeur.  
  
   > [!NOTE]
   >  Ne définissez pas cette entrée de Registre si vous fournissez des éléments coloriables personnalisés. Pour plus d’informations, consultez [éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration syntaxique](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [Inscrire un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)