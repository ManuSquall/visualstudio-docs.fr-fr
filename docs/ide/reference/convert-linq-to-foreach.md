---
title: Convertir une requête LINQ en instruction foreach
ms.custom: SEO-VS-2020
description: Refactorisez le code pour convertir toute requête LINQ écrite dans une syntaxe de requête en une instruction foreach.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 09d29df994ef6e4f2d96a5dcae53642ec33739c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971126"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactorisation pour convertir LINQ en une instruction foreach

Utilisez cette refactorisation pour convertir une [syntaxe de requête LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) en une instruction [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Cette refactorisation s’applique à :

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Comment l’utiliser

1. Sélectionnez toute la requête LINQ en commençant par `from`.

   > [!NOTE]
   > Cette refactorisation sert uniquement à convertir des requêtes LINQ exprimées avec une syntaxe de requête et non avec une syntaxe de méthode.

1. Appuyez sur **CTRL** + **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Menu des actions rapides pour convertir LINQ en foreach](media/convert-linq-to-foreach.png)

1. Sélectionnez **Convertir en 'foreach'**. Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

> [!NOTE]
> Pour C#, le code généré par ces refactorisations utilise un type explicite ou [var](/dotnet/csharp/language-reference/keywords/var) pour la variable d’itération de la boucle `foreach`. Le type du code généré, explicite ou implicite, dépend des paramètres de style de code qui se trouvent dans la portée. Ces paramètres de style de code particuliers sont configurés au niveau de l’ordinateur sous **Outils**  >  **options**  >  **éditeur de texte**  >  **C#**  >  **style**  >  **général**  >  **\' var**, ou au niveau de la solution dans un fichier [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Si vous modifiez un paramètre de style de code dans **Options**, rouvrez le fichier de code pour appliquer les modifications.

## <a name="see-also"></a>Voir aussi

- [LINQ](/dotnet/standard/using-linq)
- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
