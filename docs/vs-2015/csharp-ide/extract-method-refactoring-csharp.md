---
title: Extraire la méthode refactorisation (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667545"
---
# <a name="extract-method-refactoring-c"></a>Extraire la méthode (Refactorisation C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' **extraction de méthode** est une opération de refactorisation qui fournit un moyen simple de créer une nouvelle méthode à partir d’un fragment de code dans un membre existant.

 À l’aide de la **méthode Extract**, vous pouvez créer une nouvelle méthode en extrayant une sélection de code à partir du bloc de code d’un membre existant. La nouvelle méthode extraite contient le code sélectionné et le code sélectionné dans le membre existant est remplacé par un appel à la nouvelle méthode. Transformer un fragment de code en sa propre méthode vous permet de réorganiser rapidement et avec précision du code pour une meilleure réutilisation et une meilleure lisibilité.

 La **méthode Extract** présente les avantages suivants :

- Encourage les meilleures pratiques de codage en soulignant les méthodes discrètes et réutilisables.

- Encourage l’auto-documentation du code via une bonne organisation.

     Lorsque des noms descriptifs sont utilisés, les méthodes de haut niveau peuvent se lire plus comme une série de commentaires.

- Encourage la création de méthodes plus fines pour simplifier la substitution.

- Réduit la duplication du code.

### <a name="to-use-extract-method"></a>Pour utiliser l’extraction de méthode

1. Créez une application console nommée `ExtractMethod`, puis remplacez `Program` par l'exemple de code suivant.

    ```csharp
    class A
    {
        const double PI = 3.141592;

        double CalculatePaintNeeded(double paintPerUnit, double radius)
        {
            // Select any of the following:
            // 1. The entire next line of code.
            // 2. The right-hand side of the next line of code.
            // 3. Just "PI *" of the right-hand side of the next line
            //    of code (to see the prompt for selection expansion).
            // 4.  All code within the method body.
            // ...Then invoke Extract Method.

            double area = PI * radius * radius;

            return area / paintPerUnit;
        }
    }
    ```

2. Sélectionnez le fragment de code que vous souhaitez extraire :

    ```csharp
    double area = PI * radius * radius;
    ```

3. Dans le menu **Refactoriser** , cliquez sur **extraire la méthode**.

     La boîte de dialogue **extraire la méthode** s’affiche.

     Vous pouvez également taper le raccourci clavier CTRL + R, M pour afficher la boîte de dialogue **extraire la méthode** .

     Vous pouvez également cliquer avec le bouton droit sur le code sélectionné, pointer sur **Refactoriser**, puis cliquer sur **extraire la méthode** pour afficher la boîte de dialogue **extraire la méthode** .

4. Spécifiez un nom pour la nouvelle méthode, par exemple `CircleArea` , dans la zone **nouveau nom** de la méthode.

     Un aperçu de la nouvelle signature de méthode s’affiche sous la signature de la **méthode d’aperçu**.

5. Cliquez sur **OK**.

## <a name="remarks"></a>Notes
 Quand vous utilisez la commande **extract Method** , la nouvelle méthode est insérée à la suite du membre source de la même classe.

## <a name="partial-types"></a>Types partiels
 Si la classe est un type partiel, la **méthode Extract** génère immédiatement la nouvelle méthode qui suit le membre source. La **méthode Extract** détermine la signature de la nouvelle méthode, en créant une méthode statique quand aucune donnée d’instance n’est référencée par le code dans la nouvelle méthode.

## <a name="generic-type-parameters"></a>Paramètres de type générique
 Lorsque vous extrayez une méthode ayant un paramètre de type générique sans contrainte, le code généré n’ajoute pas le `ref` modificateur à ce paramètre, sauf si une valeur lui est assignée. Si la méthode extraite prend en charge les types référence comme argument de type générique, vous devez ajouter manuellement le `ref` modificateur au paramètre dans la signature de la méthode.

## <a name="anonymous-methods"></a>Méthodes anonymes
 Si vous tentez d’extraire une partie d’une méthode anonyme qui contient une référence à une variable locale qui est déclarée ou référencée en dehors de la méthode anonyme, Visual Studio vous avertit des modifications sémantiques potentielles.

 Quand une méthode anonyme utilise la valeur d’une variable locale, la valeur est obtenue au moment de l’exécution de la méthode anonyme. Quand une méthode anonyme est extraite dans une autre méthode, la valeur de la variable locale est obtenue au moment de l’appel à la méthode extraite.

 L’exemple suivant illustre cette modification sémantique. Si ce code est exécuté, **11** est imprimé sur la console. Si vous utilisez la **méthode Extract** pour extraire la région de code qui est marquée par les commentaires de code dans sa propre méthode, puis exécuter le code refactorisé, **10** sera imprimé sur la console.

```csharp
class Program
{
    delegate void D();
    D d;
    static void Main(string[] args)
    {
        Program p = new Program();
        int i = 10;
        /*begin extraction*/
            p.d = delegate { Console.WriteLine(i++); };
        /*end extraction*/
        i++;
        p.d();
    }
}
```

 Pour contourner cette situation, créez les variables locales utilisées dans les champs de méthode anonyme de la classe.

## <a name="see-also"></a>Voir aussi
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)