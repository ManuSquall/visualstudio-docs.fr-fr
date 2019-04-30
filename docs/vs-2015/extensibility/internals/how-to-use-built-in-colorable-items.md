---
title: 'Procédure : Utiliser des éléments Coloriables intégrés | Microsoft Docs'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436131"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procédure : Utiliser des éléments coloriables intégrés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avant d’utiliser des éléments colorables intégrés, vous devez tout d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas de vos propres éléments coloriables personnalisés, ce qui seraient dans ce cas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objets. Pour cela, vous devez en définissant une entrée de Registre pour le service de langage.  
  
### <a name="to-use-built-in-colorable-items"></a>Pour utiliser des éléments coloriables intégrés  
  
1. Sous HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language Services\\*Nom_langage*, où *X.Y* est une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et *Nom_langage* est le nom de votre langage, créez une valeur d’entrée de Registre DWORD appelée `RequestStockColors`.  
  
2. Définir le `RequestStockColors` valeur d’entrée de Registre sur 1.  
  
     Après avoir créé l’entrée de Registre, votre Coloriseur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode peut utiliser les membres de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> énumération pour remplir le tableau d’attributs de couleur pour une utilisation par l’éditeur.  
  
    > [!NOTE]
    > Ne définissez pas cette entrée de Registre si vous fournissez des éléments coloriables personnalisés. Pour plus d’informations, consultez [éléments Coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration syntaxique](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Éléments Coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)   
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)
