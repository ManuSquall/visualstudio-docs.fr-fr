---
title: Refactoriser du code pour convertir une boucle for en instruction foreach
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactorisation pour effectuer une conversion entre une boucle for et une instruction foreach

Ces refactorisations s’appliquent à :

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertir une boucle for en instruction foreach

Si vous avez une boucle [for](/dotnet/csharp/language-reference/keywords/for) dans votre code, vous pouvez utiliser cette refactorisation pour la convertir en instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Pourquoi convertir

Les raisons pour lesquelles vous voulez convertir une boucle [for](/dotnet/csharp/language-reference/keywords/for) en instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) sont notamment les suivantes :

- Vous n’utilisez pas la variable du nombre d’itérations à l’intérieur de la boucle, sauf en tant qu’index pour accéder à l’élément.

- Vous souhaitez simplifier votre code et réduire la probabilité d’erreurs de logique dans l’initialiseur, la condition et les instructions d’itération.

### <a name="how-to-use-it"></a>Utilisation

1. Placez votre curseur sur la première ligne de la boucle `for`.

1. Appuyez sur **Ctrl**+**.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu Convertir en 'foreach'](media/convert-to-foreach.png)

1. Sélectionnez **Convertir en 'foreach'**. Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertir une instruction foreach en boucle for

Si vous avez une instruction [foreach](/dotnet/csharp/language-reference/keywords/for) dans votre code, vous pouvez utiliser cette refactorisation pour la convertir en boucle [for](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Pourquoi convertir

Les raisons pour lesquelles vous voulez convertir une instruction [foreach](/dotnet/csharp/language-reference/keywords/for) en boucle [for](/dotnet/csharp/language-reference/keywords/foreach-in) sont notamment les suivantes :

- Vous souhaitez utiliser la variable du nombre d’itérations à l’intérieur de la boucle, et pas uniquement pour accéder à l’élément.

- Vous [itérez au sein d’un tableau multidimensionnel ](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) et souhaitez davantage de contrôle sur les éléments du tableau.

### <a name="how-to-use-it"></a>Utilisation

1. Placez votre curseur sur la première ligne de l’instruction `foreach`.

1. Appuyez sur **Ctrl**+**.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu Convertir en 'for'](media/convert-to-for.png)

1. Sélectionnez **Convertir en 'for'**. Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

1. Étant donné que la refactorisation introduit une nouvelle variable du nombre d’itérations, la zone **Renommer** s’affiche dans l’angle supérieur droit de l’éditeur. Si vous souhaitez choisir un autre nom pour la variable, tapez-le et appuyez sur **Entrée** ou sélectionnez **Appliquer** dans la zone **Renommer**. Si vous ne souhaitez pas choisir un nouveau nom, appuyez sur **Échap** ou sélectionnez **Appliquer** pour faire disparaître la zone **Renommer**.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)