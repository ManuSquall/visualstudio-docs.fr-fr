---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "Extraire la méthode (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Extraire la méthode (Refactorisation C#)
**Extraire la méthode** est une opération de refactorisation qui offre un moyen simple pour créer une nouvelle méthode à partir d’un fragment de code dans un membre existant.  
  
 À l’aide de **extraire la méthode**, vous pouvez créer une nouvelle méthode en extrayant une sélection de code à partir de l’intérieur du bloc de code d’un membre existant. La nouvelle méthode extraite contient le code sélectionné, et le code sélectionné dans le membre existant est remplacé par un appel à la nouvelle méthode. Transformer un fragment de code en sa propre méthode vous permet de rapidement et avec précision réorganiser le code pour une meilleure lisibilité et réutilisation.  
  
 **Extraire la méthode** présente les avantages suivants :  
  
-   Encourage les pratiques de codage en mettant en évidence les méthodes discrètes et réutilisables.  
  
-   Encourage le code auto-documenté via une bonne organisation.  
  
     Lorsque des noms descriptifs sont utilisés, de haut niveau de méthodes peuvent lire comme une série de commentaires.  
  
-   Encourage la création de méthodes à granularité fine pour simplifier la substitution.  
  
-   Réduit la duplication de code.  
  
### <a name="to-use-extract-method"></a>Pour utiliser extraire la méthode  
  
1.  Créez une application console nommée `ExtractMethod`, puis remplacez `Program` par l'exemple de code suivant.  
  
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
  
2.  Sélectionnez le fragment de code que vous souhaitez extraire :  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Sur le **refactoriser** menu, cliquez sur **extraire la méthode**.  
  
     Le **extraire la méthode** boîte de dialogue s’affiche.  
  
     Ou bien, vous pouvez également taper le raccourci clavier CTRL + R, M pour afficher la **extraire la méthode** boîte de dialogue.  
  
     Vous pouvez également cliquer sur le code, pointez sur **refactoriser**, puis cliquez sur **extraire la méthode** pour afficher les **extraire la méthode** boîte de dialogue.  
  
4.  Spécifiez un nom pour la nouvelle méthode, tel que `CircleArea`, dans le **nouveau nom de la méthode** boîte.  
  
     Un aperçu de la nouvelle signature de méthode s’affiche sous **Signature de méthode aperçu**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez la **extraire la méthode** de commande, la nouvelle méthode est insérée à la suite du membre source dans la même classe.  
  
## <a name="partial-types"></a>Types partiels  
 Si la classe est un type partiel, puis **extraire la méthode** génère la nouvelle méthode qui suit immédiatement le membre de la source. **Extraire la méthode** détermine la signature de la nouvelle méthode, en créant une méthode statique lorsque aucune donnée d’instance n’est référencée par le code dans la nouvelle méthode.  
  
## <a name="generic-type-parameters"></a>Paramètres de type générique  
 Lorsque vous extrayez une méthode qui a un paramètre de type générique sans contrainte, le code généré n’ajoutera pas le `ref` modificateur à ce paramètre, sauf si une valeur lui est attribuée. Si la méthode extraite prend en charge les types référence comme argument de type générique, vous devez ajouter manuellement le `ref` modificateur de paramètre dans la signature de méthode.  
  
## <a name="anonymous-methods"></a>Méthodes anonymes  
 Si vous essayez d’extraire une partie d’une méthode anonyme qui inclut une référence à une variable locale qui est déclarée ou référencée en dehors de la méthode anonyme, Visual Studio vous avertit des changements sémantiques potentiels.  
  
 Lorsqu’une méthode anonyme utilise la valeur d’une variable locale, la valeur est obtenue au moment où que la méthode anonyme est exécutée. Lorsqu’une méthode anonyme est extraite dans une autre méthode, la valeur de la variable locale est obtenue au moment de l’appel à la méthode extraite.  
  
 L’exemple suivant illustre ce changement sémantique. Si ce code est exécuté, **11** seront imprimés dans la console. Si vous utilisez **extraire la méthode** pour extraire la région de code qui est marquée par les commentaires de code dans sa propre méthode, puis exécutez le code refactorisé, puis **10** seront imprimés dans la console.  
  
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
  
 Pour contourner ce problème, vérifiez les variables locales qui sont utilisées dans les champs de méthode anonyme de la classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](refactoring-csharp.md)