---
title: Simplifier une expression LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957554"
---
# <a name="simplify-linq-expression"></a>Simplifier une expression LINQ

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Refactorise des instances de `SomeEnumerableType.Where(<LambdaExpression>).Single()` à pour, ainsi `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` que les méthodes énumérables suivantes : `SingleOrDefault()` , `Last()` , `LastOrDefault()` ,,, `Any()` `Count()` `First()` et `FirstOrDefault()` .

Dans les **cas suivants :**  Toutes les instances où la méthode appelle `Single()` , `SingleOrDefault()` , etc. n’ont pas d’arguments et sont précédées d’une `Where()` expression. L’entrée de l' `Where()` expression ne peut pas être construite comme une arborescence de l’expression.

**Pourquoi :** La suppression de l’appel inutile à l’énumérable pour la `.Where()` méthode améliore les performances et la lisibilité.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans l' `SomeEnumerableType.Where(<LambdaExpression>).Single()` instance de Visual Studio.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionner **simplifier l’expression LINQ**

   ![Convertir typeof en nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
