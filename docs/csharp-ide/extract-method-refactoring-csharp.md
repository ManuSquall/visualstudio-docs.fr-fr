---
title: "Extraire la m&#233;thode (Refactorisation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactorisation [C#], Extraire la méthode"
  - "Extraire la méthode (opération de refactorisation C#)"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extraire la m&#233;thode (Refactorisation&#160;C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Extraire la méthode** est une opération de refactorisation qui offre un moyen simple de créer une nouvelle méthode à partir d'un fragment de code dans un membre existant.  
  
 **Extraire la méthode** vous permet de créer une nouvelle méthode en extrayant une sélection de code de l'intérieur du bloc de code d'un membre existant.  La nouvelle méthode extraite contient le code sélectionné, et le code sélectionné dans le membre existant est remplacé par un appel à la nouvelle méthode.  Transformer un fragment de code en sa propre méthode vous donne la possibilité de réorganiser rapidement et correctement le code pour une meilleure réutilisation et lisibilité.  
  
 **Extraire la méthode** présente les avantages suivants :  
  
-   Encourage l'application des méthodes conseillées pour le codage en mettant l'accent sur l'utilisation de méthodes discrètes et réutilisables.  
  
-   Encourage le code auto\-documenté via une bonne organisation.  
  
     Lorsque des noms descriptifs sont utilisés, les méthodes de haut niveau peuvent se lire comme une série de commentaires.  
  
-   Encourage la création de méthodes spécifiques pour simplifier la substitution.  
  
-   Réduit la duplication de code.  
  
### Pour utiliser Extraire la méthode  
  
1.  Créez une application console nommée `ExtractMethod`, puis remplacez `Program` par l'exemple de code suivant.  
  
    ```c#  
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
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  Dans le menu **Refactoriser**, cliquez sur **Extraire méthode**.  
  
     La boîte de dialogue **Extraire la méthode** s'affiche.  
  
     Vous pouvez également utiliser le raccourci clavier CTRL\+R, M pour afficher la boîte de dialogue **Extraire la méthode**.  
  
     Vous pouvez également cliquer avec le bouton droit sur le code sélectionné, pointer sur **Refactoriser**, puis cliquer sur **Extraire la méthode** pour afficher la boîte de dialogue **Extraire la méthode**.  
  
4.  Spécifiez un nom pour la nouvelle méthode, tel que `CircleArea`, dans la zone de texte **Nouveau nom de la méthode**.  
  
     Un aperçu de la nouvelle signature de méthode s'affiche sous **Afficher un aperçu de la signature de la méthode**.  
  
5.  Cliquez sur **OK**.  
  
## Notes  
 Lorsque vous utilisez la commande **Extraire la méthode**, la nouvelle méthode est insérée à la suite du membre source dans la même classe.  
  
## Types partiels  
 Si la classe est un type partiel, **Extraire la méthode** génère la nouvelle méthode qui suit immédiatement le membre de source.  **Extraire la méthode** détermine la signature de la nouvelle méthode, en créant une méthode statique lorsque aucune donnée d'instance n'est référencée par le code dans la nouvelle méthode.  
  
## Paramètres de type générique  
 Lorsque vous extrayez une méthode qui a un paramètre de type générique sans contrainte, le code généré n'ajoutera pas le modificateur `ref` à ce paramètre à moins qu'une valeur lui soit assignée.  Si la méthode extraite prend en charge des types référence comme argument de type générique, vous devez ajouter manuellement le modificateur `ref` au paramètre dans la signature de méthode.  
  
## Méthodes anonymes  
 Si vous essayez d'extraire une partie d'une méthode anonyme qui inclut une référence à une variable locale qui est soit déclarée soit référencée en dehors de la méthode anonyme, Visual Studio vous avertit des changements sémantiques potentiels.  
  
 Lorsqu'une méthode anonyme utilise la valeur d'une variable locale, la valeur est obtenue au moment où la méthode anonyme est exécutée.  Lorsqu'une méthode anonyme est extraite dans une autre méthode, la valeur de la variable locale est obtenue au moment de l'appel à la méthode extraite.  
  
 L'exemple suivant illustre ce changement sémantique.  Si ce code est exécuté, **11** sera imprimé dans la console.  Si vous utilisez **Extraire la méthode** pour extraire la région de code qui est marquée par les commentaires de code dans sa propre méthode, puis exécutez le code refactorisé, **10** sera imprimé dans la console.  
  
```c#  
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
  
 Pour contourner cette situation, transformez en champs de la classe les variables locales qui sont utilisées dans la méthode anonyme.  
  
## Voir aussi  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)