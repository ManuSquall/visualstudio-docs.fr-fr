---
title: "Éléments coloriable personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b637e59b1e436c42b6b15f0dddaa1ed2ef6ff03c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="custom-colorable-items"></a>Éléments coloriable personnalisés
Vous pouvez remplacer la liste des types pour la colorisation, telles que les mots clés et des commentaires, en implémentant des éléments coloriable personnalisés dans le cadre de votre service de langage.  
  
## <a name="user-settings-of-colorable-items"></a>Paramètres utilisateur des propriétés  
 Vous pouvez afficher le **polices et couleurs** boîte de dialogue en sélectionnant **Options** sur la **outils** menu, puis en sélectionnant **polices et couleurs** sous **environnement**. Lorsque vous sélectionnez un affichage, tel que **éditeur de texte** ou **fenêtre commande**, le **afficher les éléments** zone de liste affiche tous les éléments coloriable pour qui s’affichent. Vous pouvez afficher et modifier la police, la taille, la couleur de premier plan et la couleur d’arrière-plan pour chaque élément coloriable. Vos choix est stockées dans un cache dans le Registre et accessibles par le nom de l’élément coloriable.  
  
## <a name="presentation-of-colorable-items"></a>Présentation des éléments coloriable  
 Étant donné que l’IDE gère les substitutions par l’utilisateur d’éléments coloriable dans le **polices et couleurs** boîte de dialogue, vous devez uniquement fournir chaque élément coloriable personnalisé avec un nom. Ce nom est ce qui s’affiche dans le **afficher les éléments** liste. Les éléments coloriable s’affichent dans l’ordre alphabétique. Pour regrouper des éléments de votre service de langage de coloriable personnalisé, vous pouvez commencer chaque nom avec le nom de votre langue, par exemple **NewLanguage - commentaire** et **NewLanguage - mot clé**.  
  
> [!CAUTION]
>  Vous devez inclure le nom du langage dans le nom de l’élément coloriable pour éviter les conflits avec des noms d’élément coloriable existants. Si vous modifiez le nom de l’un de vos éléments coloriable pendant le développement, vous devez réinitialiser le cache a été créé la première fois que vos éléments coloriable accessibles. Vous pouvez réinitialiser le cache expérimental avec l’outil CreateExpInstance, qui est installé avec Visual Studio SDK, généralement dans le répertoire  
>   
>  **C:\Program fichiers (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Pour réinitialiser le cache, appelez `CreateExpInstance /Reset`. Pour plus d’informations sur CreateExpInstance, consultez [utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Le premier élément dans votre liste de propriétés n’est jamais référencé. Le premier élément correspond à un index de l’élément coloriable 0, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit toujours les couleurs de texte par défaut et les attributs de cet élément. Traiter cet élément non référencé, le plus simple consiste à fournir un élément coloriable d’espace réservé comme le premier élément dans la liste.  
  
## <a name="implementing-custom-colorable-items"></a>Implémenter des éléments coloriable personnalisés  
  
1.  Définir ce qui doit être coloré dans votre langue, par exemple (mot clé), opérateur et identificateur.  
  
2.  Créer une énumération de ces éléments coloriable.  
  
3.  Associer les types de jetons retournés à partir d’un analyseur ou le moteur d’analyse avec les valeurs énumérées.  
  
     Par exemple, les valeurs représentant les types de jetons peut être les mêmes valeurs dans l’énumération des éléments coloriable personnalisé.  
  
4.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode dans votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> d’objet, le remplissage de la liste des attributs avec les valeurs de votre énumération éléments coloriable personnalisé correspondant aux types de jetons retournés à partir de l’analyseur ou l’analyseur.  
  
5.  Dans la même classe qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> d’interface, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface et ses deux méthodes, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Si vous souhaitez prendre en charge les valeurs de couleur 24 bits ou trop élevée, vous devez également implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.  
  
8.  Dans votre objet de service de langage, créez une liste qui contient votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objets, un pour chaque élément coloriable votre analyseur ou l’analyseur peut identifier.  
  
     Vous pouvez accéder à chaque élément dans la liste à l’aide de la valeur correspondante à partir de l’énumération des éléments coloriable personnalisé. Utilisez les valeurs d’énumération en tant qu’index dans la liste. Le premier élément dans la liste n’est jamais accessible, car il correspond au texte de la valeur par défaut de style qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toujours gère elle-même. Pour cela, vous pouvez compenser en insérant un élément coloriable d’espace réservé au début de votre liste.  
  
9. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (méthode), retourner le nombre d’éléments dans votre liste coloriable personnalisé.  
  
10. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (méthode), retourner l’élément coloriable demandé à partir de votre liste.  
  
 Pour obtenir un exemple montrant comment implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle d’un Service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implémentation de la coloration de syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Guide pratique pour utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)