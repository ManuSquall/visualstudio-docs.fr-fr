---
title: Convertir une boucle foreach en syntaxe LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
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
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094219"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertir une boucle foreach en syntaxe LINQ

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de convertir facilement votre boucle *de préach qui* utilise une IEnumerable en requête LINQ ou un formulaire d’appel LINQ (également connu sous le nom de méthode LINQ).

**Quand :** Vous avez une boucle de préach qui utilise un IEnumerable, et vous voulez que cette boucle soit lue sous forme de requête LINQ.

**Pourquoi:** Vous préférez utiliser la syntaxe LINQ plutôt qu’une boucle de prédachage. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fait d’une requête une construction de langage de première classe en C#. LINQ peut réduire la quantité de code dans un fichier pour faciliter la lecture et autoriser différentes sources de données à avoir des modèles d’expression de requête similaires.

> [!NOTE]
> La syntaxe LINQ est généralement moins efficace qu’une boucle foreach. Il est judicieux de connaître les compromis de performances qui peuvent se produire lorsque vous utilisez LINQ pour améliorer la lisibilité de votre code.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Convertir une boucle foreach en syntaxe LINQ (refactorisation)

1. Placez votre curseur dans le mot clé `foreach`.

    ![Exemple, Foreach utilisant IEnumerable](media/convert-foreach-to-LINQ.png)

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Exemple, convertir en LINQ (menu)](media/convert-foreach-to-LINQ-codefix.png)

3. Sélectionnez **Convertir en LINQ** ou **convertir en Linq (formulaire d’appel)**.

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
