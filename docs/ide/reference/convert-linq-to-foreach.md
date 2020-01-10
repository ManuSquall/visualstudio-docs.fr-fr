---
title: Refactoriser du code pour convertir une requête LINQ en une instruction foreach
description: Convertit une requête LINQ écrite dans une syntaxe de requête en une instruction foreach.
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bb2cdf96d7f7829ff6a6d1394160548da2adae7f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595746"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactorisation pour convertir LINQ en une instruction foreach

Utilisez cette refactorisation pour convertir une [syntaxe de requête LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) en une instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Cette refactorisation s’applique à :

- C#

## <a name="how-to-use-it"></a>Utilisation

1. Sélectionnez toute la requête LINQ en commençant par `from`.

   > [!NOTE]
   > Cette refactorisation sert uniquement à convertir des requêtes LINQ exprimées avec une syntaxe de requête et non avec une syntaxe de méthode.

1. Appuyez sur **Ctrl**+ **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu des actions rapides pour convertir LINQ en foreach](media/convert-linq-to-foreach.png)

1. Sélectionnez **Convertir en 'foreach'** . Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

> [!NOTE]
> Pour C#, le code généré par ces refactorisations utilise un type explicite ou [var](/dotnet/csharp/language-reference/keywords/var) pour la variable d’itération de la boucle `foreach`. Le type du code généré, explicite ou implicite, dépend des paramètres de style de code qui se trouvent dans la portée. Ces paramètres de style de code particuliers sont configurés au niveau de la machine sous **Outils** > **Options** > **Éditeur de texte** > **C#**  > **Style de code** > **Général** >  **\'Préférences var**, ou au niveau de la solution dans un fichier [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types). Si vous modifiez un paramètre de style de code dans **Options**, rouvrez le fichier de code pour appliquer les modifications.

## <a name="see-also"></a>Voir aussi

- [LINQ](/dotnet/standard/using-linq)
- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
