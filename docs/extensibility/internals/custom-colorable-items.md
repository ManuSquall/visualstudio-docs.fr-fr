---
title: Éléments Coloriables personnalisés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1d18a6fe142a3b405742dd9e74c1376e713687
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312910"
---
# <a name="custom-colorable-items"></a>Éléments coloriables personnalisés
Vous pouvez remplacer la liste des types pour la colorisation, telles que les mots clés et des commentaires, en implémentant des éléments coloriables personnalisés dans le cadre de votre service de langage.

## <a name="user-settings-of-colorable-items"></a>Paramètres de l’utilisateur d’éléments coloriables
 Vous pouvez afficher le **polices et couleurs** boîte de dialogue en sélectionnant **Options** sur le **outils** menu, puis en sélectionnant **polices et couleurs** sous **environnement**. Lorsque vous sélectionnez un affichage, tel que **éditeur de texte** ou **fenêtre de commande**, le **afficher les éléments** zone de liste affiche tous les éléments coloriables pour cet affichage. Vous pouvez afficher et modifier la police, la taille, la couleur de premier plan et la couleur d’arrière-plan pour chaque élément coloriable. Vos choix est stockées dans un cache dans le Registre et accessibles par le nom de l’élément coloriable.

## <a name="presentation-of-colorable-items"></a>Présentation d’éléments coloriables
 Étant donné que l’IDE gère les substitutions d’utilisateur d’éléments coloriables dans les **polices et couleurs** boîte de dialogue, vous devez uniquement fournir chaque élément coloriable personnalisé avec un nom. Ce nom est ce qui apparaît dans le **afficher les éléments** liste. Les éléments coloriables s’affichent dans l’ordre alphabétique. Pour regrouper des éléments coloriables personnalisés de votre service de langage, vous pouvez commencer chaque nom avec votre nom de la langue, par exemple **NewLanguage - commentaire** et **NewLanguage - mot clé**.

> [!CAUTION]
> Vous devez inclure le nom du langage dans le nom de l’élément coloriable pour éviter les conflits avec des noms d’élément coloriable existants. Si vous modifiez le nom d’un de vos éléments coloriables pendant le développement, vous devez réinitialiser le cache a été créé à la première fois que vos éléments coloriables ont eu accès. Vous pouvez réinitialiser le cache expérimental avec le **CreateExpInstance** outil, qui est installé avec le SDK de Visual Studio, généralement dans le répertoire :
>
> *C:\Program Files (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Pour réinitialiser le cache, entrez **CreateExpInstance /Reset**. Pour plus d’informations sur **CreateExpInstance**, consultez [CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md).

 Le premier élément dans votre liste d’éléments coloriables n’est jamais référencé. Le premier élément correspond à un index de l’élément coloriable égale à 0, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit toujours les couleurs de texte par défaut et les attributs de cet élément. Gestion de cet élément non référencé, le plus simple consiste à fournir un élément coloriable espace réservé comme le premier élément dans la liste.

## <a name="implement-custom-colorable-items"></a>Implémenter des éléments coloriables personnalisés

1. Définir ce qui doit être colorisé dans votre langue, par exemple mot clé, opérateur et identificateur.

2. Créez une énumération de ces éléments coloriables.

3. Associer les types de jetons retournées à partir d’un analyseur ou le scanneur avec les valeurs énumérées.

    Par exemple, les valeurs représentant les types de jetons peut être les mêmes valeurs dans l’énumération d’éléments coloriables personnalisés.

4. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode dans votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> d’objet, de remplir la liste des attributs avec les valeurs à partir de votre énumération d’éléments coloriables personnalisés correspondant aux types de jeton retournés à partir de l’analyseur ou le scanneur.

5. Dans la même classe qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface et ses deux méthodes, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

6. Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Si vous souhaitez prendre en charge les valeurs de couleur 24 bits ou élevé, vous devez également implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.

8. Dans votre objet de service de langage, créez une liste qui contient votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objets, un pour chaque élément coloriable votre analyseur ou le scanneur peut identifier.

    Vous pouvez accéder à chaque élément dans la liste à l’aide de la valeur correspondante à partir de l’énumération d’éléments coloriables personnalisés. Utilisez les valeurs d’énumération en tant qu’index dans la liste. Le premier élément dans la liste n’est jamais accessible, car il correspond au texte par défaut de style qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toujours gère lui-même. Pour cela, vous pouvez compenser en insérant un élément coloriable espace réservé au début de votre liste.

9. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (méthode), retourner le nombre d’éléments dans votre liste d’éléments coloriables personnalisés.

10. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (méthode), retourner l’élément coloriable demandé à partir de votre liste.

    Pour obtenir un exemple montrant comment implémenter le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.

## <a name="see-also"></a>Voir aussi
- [Modèle d’un service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Couleurs de syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentez la coloration syntaxique](../../extensibility/internals/implementing-syntax-coloring.md)
- [Guide pratique pour Utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)