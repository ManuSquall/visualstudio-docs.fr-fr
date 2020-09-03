---
title: Éléments coloriables personnalisés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708997"
---
# <a name="custom-colorable-items"></a>Éléments coloriables personnalisés
Vous pouvez remplacer la liste de types pour la coloration, tels que les mots clés et les commentaires, en implémentant des éléments coloriables personnalisés dans le cadre de votre service de langage.

## <a name="user-settings-of-colorable-items"></a>Paramètres utilisateur d’éléments coloriables
 Vous pouvez afficher la boîte de dialogue **polices et couleurs** en sélectionnant **options** dans le menu **Outils** , puis en sélectionnant **polices et couleurs** sous **environnement**. Lorsque vous sélectionnez un affichage, tel que **éditeur de texte** ou **fenêtre commande**, la zone de liste **éléments affichés** affiche tous les éléments coloriables pour cet affichage. Vous pouvez afficher et modifier la police, la taille, la couleur de premier plan et la couleur d’arrière-plan pour chaque élément coloriable. Vos choix sont stockés dans un cache dans le registre et sont accessibles par le nom de l’élément coloriable.

## <a name="presentation-of-colorable-items"></a>Présentation des éléments coloriables
 Étant donné que l’IDE gère les remplacements utilisateur d’éléments coloriables dans la boîte de dialogue **polices et couleurs** , vous devez fournir uniquement chaque élément coloriable personnalisé avec un nom. Ce nom apparaît dans la liste **éléments affichés** . Les éléments coloriables apparaissent par ordre alphabétique. Pour regrouper les éléments coloriables personnalisés de votre service de langage, vous pouvez commencer chaque nom par le nom de votre langue, par exemple **newLanguage-comment** et **newLanguage-Keyword**.

> [!CAUTION]
> Vous devez inclure le nom de la langue dans le nom de l’élément coloriable pour éviter les collisions avec les noms d’éléments coloriables existants. Si vous modifiez le nom de l’un de vos éléments coloriables pendant le développement, vous devez réinitialiser le cache qui a été créé la première fois que vous avez accédé à vos éléments coloriables. Vous pouvez réinitialiser le cache expérimental avec l’outil **CreateExpInstance** , qui est installé avec le kit de développement logiciel (SDK) Visual Studio, généralement dans le répertoire suivant :
>
> *C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Pour réinitialiser le cache, entrez **CreateExpInstance/Reset**. Pour plus d’informations sur **CreateExpInstance**, consultez [utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Le premier élément de votre liste d’éléments coloriables n’est jamais référencé. Le premier élément correspond à un index d’élément coloriable de 0 et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit toujours les couleurs et les attributs de texte par défaut pour cet élément. Le moyen le plus simple de traiter cet élément non référencé consiste à fournir un élément colorable d’espace réservé dans votre liste comme premier élément.

## <a name="implement-custom-colorable-items"></a>Implémenter des éléments coloriables personnalisés

1. Définissez ce qui doit être coloré dans votre langage, par exemple le mot clé, l’opérateur et l’identificateur.

2. Créez une énumération de ces éléments coloriables.

3. Associez les types de jetons retournés par un analyseur ou un scanneur aux valeurs énumérées.

    Par exemple, les valeurs représentant les types de jetons peuvent avoir les mêmes valeurs dans l’énumération d’éléments coloriables personnalisés.

4. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode dans votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objet, remplissez la liste des attributs avec les valeurs de votre énumération d’éléments coloriables personnalisés correspondant aux types de jetons retournés par l’analyseur ou le scanneur.

5. Dans la même classe qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface, implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface et ses deux méthodes, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Si vous souhaitez prendre en charge des valeurs de couleur 24 bits ou élevées, implémentez également l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.

8. Dans votre objet de service de langage, créez une liste qui contient vos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objets, un pour chaque élément coloriable que votre analyseur ou scanneur peut identifier.

    Vous pouvez accéder à chaque élément de la liste à l’aide de la valeur correspondante de l’énumération des éléments coloriables personnalisés. Utilisez les valeurs d’énumération en tant qu’index dans la liste. Le premier élément de la liste n’est jamais accessible, car il correspond au style de texte par défaut qui se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère toujours lui-même. Vous pouvez compenser cela en insérant un élément colorable d’espace réservé au début de la liste.

9. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> méthode, retournez le nombre d’éléments dans votre liste d’éléments coloriables personnalisés.

10. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> méthode, retournez l’élément coloriable demandé dans votre liste.

    Pour obtenir un exemple de la façon d’implémenter les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces et, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Voir aussi
- [Modèle d’un service de langage hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Coloration de la syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloration de la syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémenter la coloration syntaxique](../../extensibility/internals/implementing-syntax-coloring.md)
- [Comment : utiliser des éléments coloriables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
