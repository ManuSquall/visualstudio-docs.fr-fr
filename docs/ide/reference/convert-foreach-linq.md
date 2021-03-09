---
title: Convertir une boucle foreach en syntaxe LINQ
description: Convertit une boucle foreach qui utilise un IEnumerable en requête LINQ ou un formulaire d’appel LINQ (également appelé méthode LINQ).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ff489e11cc5c61c5e840b4b12d05ba5da46ce41
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466288"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertir une boucle foreach en syntaxe LINQ

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Vous permet de convertir facilement votre boucle *foreach* qui utilise un IEnumerable en requête LINQ ou un formulaire d’appel LINQ (également appelé méthode LINQ).

Dans les **cas suivants :** Vous avez une boucle foreach qui utilise un IEnumerable et vous souhaitez que cette boucle soit lue en tant que requête LINQ.

**Pourquoi :** Vous préférez utiliser la syntaxe LINQ plutôt qu’une boucle foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fait d’une requête une construction de langage de première classe en C#. LINQ peut réduire la quantité de code dans un fichier pour faciliter la lecture et autoriser différentes sources de données à avoir des modèles d’expression de requête similaires.

> [!NOTE]
> La syntaxe LINQ est généralement moins efficace qu’une boucle foreach. Il est judicieux de connaître les compromis de performances qui peuvent se produire lorsque vous utilisez LINQ pour améliorer la lisibilité de votre code.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Convertir une boucle foreach en syntaxe LINQ (refactorisation)

1. Placez votre curseur dans le mot clé `foreach`.

    ![Exemple, Foreach utilisant IEnumerable](media/convert-foreach-to-LINQ.png)

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Exemple, convertir en LINQ (menu)](media/convert-foreach-to-LINQ-codefix.png)

3. Sélectionnez **convertir en LINQ** ou **convertir en LINQ (formulaire d’appel)**.

   ![Exemple, résultat de la requête LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Exemple, résultat du formulaire d’appel LINQ](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Exemple de code

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Fenêtre Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
