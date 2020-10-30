---
title: Refactoriser pour convertir une boucle for en instruction foreach
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 68ed736a1e3a07c7cd3f67ea9c936821cf4ac78c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045913"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactorisation pour effectuer une conversion entre une boucle for et une instruction foreach

Cet article décrit les refactorisations Actions rapides qui effectuent une conversion entre deux structures de boucles. Il précise les raisons pour lesquelles vous pouvez passer d’une boucle [for](/dotnet/csharp/language-reference/keywords/for) à une instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) dans votre code.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertir une boucle for en instruction foreach

Si vous avez une boucle [for](/dotnet/csharp/language-reference/keywords/for) dans votre code, vous pouvez utiliser cette refactorisation pour la convertir en instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Cette refactorisation s’applique à :

- C#

- Visual Basic

> [!NOTE]
> La refactorisation Action Rapide **Convertir en foreach** est disponible uniquement pour les boucles [for](/dotnet/csharp/language-reference/keywords/for) qui contiennent les trois composants : un initialiseur, une condition et un itérateur.

### <a name="why-convert"></a>Pourquoi convertir

Les raisons pour lesquelles vous voulez convertir une boucle [for](/dotnet/csharp/language-reference/keywords/for) en instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) sont notamment les suivantes :

- Vous n’utilisez pas la variable de boucle locale à l’intérieur de la boucle, sauf en tant qu’index pour accéder aux éléments.

- Vous souhaitez simplifier votre code et réduire la probabilité d’erreurs de logique dans l’initialiseur, la condition et l’itérateur.

### <a name="how-to-use-it"></a>Comment l’utiliser

1. Placez le point insertion dans le mot clé `for`.

1. Appuyez sur **CTRL** + **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu Convertir en 'foreach'](media/convert-to-foreach.png)

1. Sélectionnez **Convertir en 'foreach'** . Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer** .

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertir une instruction foreach en boucle for

Si vous avez une instruction [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) ou [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) dans votre code, vous pouvez utiliser cette refactorisation pour la convertir en boucle [for](/dotnet/csharp/language-reference/keywords/for).

Cette refactorisation s’applique à :

- C#

- Visual Basic

### <a name="why-convert"></a>Pourquoi convertir

Les raisons pour lesquelles vous voulez convertir une instruction [foreach](/dotnet/csharp/language-reference/keywords/for) en boucle [for](/dotnet/csharp/language-reference/keywords/foreach-in) sont notamment les suivantes :

- Vous souhaitez utiliser la variable de boucle locale à l’intérieur de la boucle, et pas uniquement pour accéder à l’élément.

- Vous [itérez au sein d’un tableau multidimensionnel ](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) et souhaitez davantage de contrôle sur les éléments du tableau.

### <a name="how-to-use-it"></a>Comment l’utiliser

1. Placez le point insertion dans le mot clé `foreach` ou `For Each`.

1. Appuyez sur **CTRL** + **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu Convertir en 'for'](media/convert-to-for.png)

1. Sélectionnez **Convertir en 'for'** . Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer** .

1. Étant donné que la refactorisation introduit une nouvelle variable du nombre d’itérations, la zone **Renommer** s’affiche dans l’angle supérieur droit de l’éditeur. Si vous souhaitez choisir un autre nom pour la variable, tapez-le et appuyez sur **Entrée** ou sélectionnez **Appliquer** dans la zone **Renommer** . Si vous ne souhaitez pas choisir un nouveau nom, appuyez sur **Échap** ou sélectionnez **Appliquer** pour faire disparaître la zone **Renommer** .

> [!NOTE]
> Pour C#, le code généré par ces refactorisations utilise un type explicite ou [var](/dotnet/csharp/language-reference/keywords/var) pour le type des éléments dans la collection. Le type du code généré, explicite ou implicite, dépend des paramètres de style de code qui se trouvent dans la portée. Ces paramètres de style de code particuliers sont configurés au niveau de l’ordinateur sous **Outils**  >  **options**  >  **éditeur de texte**  >  **C#**  >  **style**  >  **général**  >  **\' var** , ou au niveau de la solution dans un fichier [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Si vous modifiez un paramètre de style de code dans **Options** , rouvrez le fichier de code pour appliquer les modifications.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
