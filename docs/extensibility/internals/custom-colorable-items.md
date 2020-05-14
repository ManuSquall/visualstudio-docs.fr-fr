---
title: Articles colorables personnalisés ( Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708997"
---
# <a name="custom-colorable-items"></a>Articles colorables personnalisés
Vous pouvez passer outre à la liste des types de colorisation, tels que les mots clés et les commentaires, en implémentant des éléments colorables personnalisés dans le cadre de votre service linguistique.

## <a name="user-settings-of-colorable-items"></a>Paramètres de l’utilisateur des éléments colorables
 Vous pouvez afficher la boîte de dialogue **Fonts and Colors** en sélectionnant **des options** sur le menu **Tools,** puis en sélectionnant **des polices et des couleurs** sous **Environnement.** Lorsque vous sélectionnez un affichage, tel que **Text Editor** ou **Command Window**, la boîte de liste **d’éléments d’affichage** affiche tous les éléments colorables pour cet affichage. Vous pouvez afficher et modifier la police, la taille, la couleur de premier plan, et la couleur de fond pour chaque élément colorable. Vos choix sont stockés dans un cache dans le registre et accessibles par le nom d’élément colorable.

## <a name="presentation-of-colorable-items"></a>Présentation d’objets colorables
 Parce que l’IDE gère les remplacements de l’utilisateur des articles colorables dans la boîte de dialogue **Fonts and Colors,** vous n’avez qu’à fournir chaque élément colorable personnalisé avec un nom. Ce nom est ce qui apparaît dans la liste **des éléments d’affichage.** Les éléments colorables apparaissent par ordre alphabétique. Pour regrouper les articles colorables personnalisés de votre service linguistique, vous pouvez commencer chaque nom avec votre nom de langue, par exemple **NewLanguage - Commentaire** et **NewLanguage - Mot-clé**.

> [!CAUTION]
> Vous devez inclure le nom de la langue dans le nom d’élément colorable pour éviter les collisions avec les noms d’objets colorables existants. Si vous changez le nom d’un de vos éléments colorables pendant le développement, vous devez réinitialiser le cache qui a été créé la première fois que vos articles colorables ont été consultés. Vous pouvez réinitialiser le cache expérimental avec l’outil **CreateExpInstance,** qui est installé avec le Visual Studio SDK, généralement dans le répertoire :
>
> *C : Fichiers de programme (x86) - Microsoft Visual Studio 14.0-VSSDK-VisualStudioIntegration-Tools-Bin*
>
> Pour réinitialiser le cache, entrez **CreateExpInstance /Reset**. Pour plus d’informations sur **CreateExpInstance**, voir [CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md).

 Le premier élément de votre liste d’éléments colorables n’est jamais référencé. Le premier élément correspond à un index d’élément colorable de 0, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit toujours les couleurs et les attributs de texte par défaut pour cet article. La façon la plus simple de traiter cet article non référé est de fournir un élément colorable de placeholder dans votre liste comme premier élément.

## <a name="implement-custom-colorable-items"></a>Implémentez des articles colorables personnalisés

1. Définissez ce qui doit être colorisé dans votre langue, par exemple mot-clé, opérateur et identifiant.

2. Créez un recensement de ces articles colorables.

3. Associez les types de jetons retournés d’un analyseur ou d’un scanner aux valeurs énumérées.

    Par exemple, les valeurs représentant les types de jetons pourraient être les mêmes valeurs dans le recensement des éléments colorables personnalisés.

4. Dans votre implémentation de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> méthode dans votre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objet, remplissez la liste des attributs avec les valeurs de votre énumération d’éléments colorables personnalisés correspondant aux types de jetons retournés du parser ou du scanner.

5. Dans la même classe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> qui implémente l’interface, implémenter l’interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> et ses deux méthodes, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

6. Implémentez l'interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Si vous souhaitez prendre en charge des valeurs de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> couleur 24 ou élevées, implémentez également l’interface.

8. Dans votre objet de service linguistique, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> créez une liste qui contient vos objets, un pour chaque élément colorable que votre parseur ou scanner peut identifier.

    Vous pouvez accéder à chaque élément de la liste en utilisant la valeur correspondante du recensement des éléments colorables personnalisés. Utilisez les valeurs de recensement comme un index dans la liste. Le premier élément de la liste n’est jamais accessible, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] car il correspond au style texte par défaut qui se comporte toujours. Vous pouvez compenser cela en insérant un élément colorable de placeholder au début de votre liste.

9. Dans votre mise <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> en œuvre de la méthode, retournez le nombre d’éléments dans votre liste d’éléments colorables personnalisés.

10. Dans votre mise <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> en œuvre de la méthode, retournez l’élément colorable demandé de votre liste.

    Pour un exemple de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> façon de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>mettre en œuvre le et les interfaces, voir .

## <a name="see-also"></a>Voir aussi
- [Modèle d’un service linguistique hérité](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Coloriage Syntax dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloriage Syntax dans un service linguistique hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentez la coloration syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Comment: Utilisez des articles colorables intégrés](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
