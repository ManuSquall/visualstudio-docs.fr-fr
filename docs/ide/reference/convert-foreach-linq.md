---
title: Convertir une boucle foreach en syntaxe LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f0b9685ce6d4cf8ee6d4253c79759508cf43915e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968472"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertir une boucle foreach en syntaxe LINQ

Cette refactorisation s’applique à :

- C#

**Quoi :** Permet de convertir facilement une boucle *foreach* utilisant un IEnumerable en requête LINQ ou formulaire d’appel LINQ (aussi connu sous le nom de méthode LINQ).

**Quand :** Vous avez une boucle foreach qui utilise un IEnumerable et vous souhaiteriez qu’elle soit lue en tant que requête LINQ.

**Pourquoi :** Vous préférez utiliser la syntaxe LINQ plutôt qu’une boucle foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) fait d’une requête une construction de langage de première classe en C#. LINQ peut réduire la quantité de code dans un fichier pour faciliter la lecture et autoriser différentes sources de données à avoir des modèles d’expression de requête similaires.

> [!NOTE]
> La syntaxe LINQ est généralement moins efficace qu’une boucle foreach. Il est judicieux de connaître les compromis de performances qui peuvent se produire lorsque vous utilisez LINQ pour améliorer la lisibilité de votre code.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Convertir une boucle foreach en syntaxe LINQ (refactorisation)

1. Placez votre curseur dans le mot clé `foreach`.

    ![Exemple, Foreach utilisant IEnumerable](media/convert-foreach-to-LINQ.png)

2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Exemple, convertir en LINQ (menu)](media/convert-foreach-to-LINQ-codefix.png)

3. Sélectionnez **Convertir en LINQ** ou **Convertir en LINQ (formulaire d’appel)**.

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
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
