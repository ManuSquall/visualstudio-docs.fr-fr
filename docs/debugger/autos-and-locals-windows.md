---
title: Inspecter des variables - fenêtres automatique et variables locales | Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 584704471f9346611f240a3a24e0d45cf2eec364
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068352"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Inspecter des variables dans les fenêtres automatique et variables locales

Le **automatique** et **variables locales** windows affichent les valeurs des variables pendant le débogage. Les fenêtres sont disponibles uniquement pendant une session de débogage. Le **automatique** fenêtre affiche les variables utilisées autour du point d’arrêt actuel. Le **variables locales** fenêtre affiche les variables définies dans la portée locale, qui est généralement la méthode ou la fonction active. S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [corriger les bogues en écrivant mieux C# code](../debugger/write-better-code-with-visual-studio.md) et [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

 Le **automatique** fenêtre n’est disponible pour C#, code Visual Basic, C++ et Python, mais pas pour JavaScript ou F#.
  
Pour ouvrir le **automatique** fenêtre, pendant le débogage, sélectionnez **déboguer** > **Windows** > **automatique**, ou appuyez sur **Ctrl**+**Alt**+**V** > **A**.  

Pour ouvrir le **variables locales** fenêtre, pendant le débogage, sélectionnez **déboguer** > **Windows** > **variables locales**, ou appuyez sur **Alt**+**4**.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [des visualisations de données dans Visual Studio pour Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Utiliser les fenêtres automatique et variables locales

Affichent les tableaux et les objets dans le **automatique** et **variables locales** windows en tant que contrôles d’arborescence. Sélectionnez la flèche vers la gauche d’un nom de variable pour développer la vue pour afficher les champs et propriétés. Voici un exemple d’un <xref:System.IO.FileStream?displayProperty=fullName> de l’objet dans le **variables locales** fenêtre :

![Variables locales-FileStream](../debugger/media/locals-filestream.png "FileStream de variables locales")

Une valeur de rouge dans le **variables locales** ou **automatique** fenêtre signifie que la valeur a changé depuis la dernière évaluation. Le changement peut provenir d’une précédente session de débogage, ou parce que vous avez modifié la valeur dans la fenêtre.

Le format numérique par défaut dans les fenêtres du débogueur est décimal. Pour modifier cette valeur au format hexadécimal, cliquez sur le **variables locales** ou **automatique** fenêtre et sélectionnez **affichage hexadécimal**. Cette modification affecte toutes les fenêtres du débogueur.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Modifier les valeurs des variables dans la fenêtre automatique ou variables locales

Pour modifier les valeurs de la plupart des variables dans le **automatique** ou **variables locales** windows, double-cliquez sur la valeur et entrez la nouvelle valeur.

Vous pouvez entrer une expression pour une valeur, par exemple `a + b`. Le débogueur accepte la plupart des expressions de langage valides.

Dans le code C++ natif, vous devrez peut-être qualifier le contexte d’un nom de variable. Pour plus d’informations, consultez [Opérateur de contexte (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Assurez-vous que vous comprenez les conséquences avant de modifier des valeurs et les expressions. Certains problèmes possibles sont :
>
>-   Évaluer certaines expressions peut modifier la valeur d’une variable ou affecter d’une manière ou d’une autre l’état de votre programme. Par exemple, l’évaluation `var1 = ++var2` modifie la valeur des deux `var1` et `var2`. Ces expressions sont réputées pour avoir [effets](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Effets secondaires peuvent provoquer des résultats inattendus si vous n’êtes pas informé.
>
>-   Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Même une modification apparemment anodine peut entraîner des modifications à certaines des bits dans la variable à virgule flottante.

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Modifier le contexte pour la fenêtre automatique ou variables locales

Vous pouvez utiliser la **emplacement de débogage** barre d’outils pour sélectionner une fonction souhaitée, le thread ou le processus, ce qui modifie le contexte pour le **automatique** et **variables locales** windows.

Pour activer la **emplacement de débogage** barre d’outils, cliquez dans une partie vide de la zone de barre d’outils, puis sélectionnez **emplacement de débogage** à partir de la liste déroulante, ou sélectionnez **vue**  >   **Barres d’outils** > **emplacement de débogage**.

Définissez un point d’arrêt et démarrez le débogage. Lorsque le point d’arrêt est atteint, les pauses d’exécution et que vous pouvez voir l’emplacement dans le **emplacement de débogage** barre d’outils.

![Barre d’outils emplacement de débogage](../debugger/media/debuglocationtoolbar.png "barre d’outils emplacement de débogage")

## <a name="bkmk_whatvariables"></a> Variables dans la fenêtre automatique (C#, C++, Visual Basic, Python)

 Affichent les variables différentes dans différents langages le **automatique** fenêtre.

 - En C# et en Visual Basic, la fenêtre **Automatique** affiche les variables utilisées sur la ligne actuelle ou précédente. Par exemple, dans C# ou Visual Basic du code, déclarez les variables de quatre suivantes :

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Définissez un point d’arrêt sur la ligne `c = 3;`, et démarrez le débogueur. Lors de l’exécution s’arrête, le **automatique** fenêtre s’affiche :

   ![Automatique-CSharp](../debugger/media/autos-csharp.png "automatique-CSharp")

   La valeur de `c` est 0, car la ligne `c = 3` n’a pas encore été exécutée.

 - En C++, le **automatique** fenêtre affiche les variables utilisées dans au moins trois lignes avant la ligne actuelle où l’exécution est suspendue. Par exemple, dans le code C++, déclarez six variables :

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Définissez un point d’arrêt sur la ligne `e = 5;` et exécutez le débogueur. Lors de l’exécution s’arrête, le **automatique** fenêtre s’affiche :

    ![Automatique-C++](../debugger/media/autos-cplus.png "automatique-C++")

    La variable `e` n’est pas initialisée, car la ligne `e = 5` n’a pas encore été exécutée.

##  <a name="bkmk_returnValue"></a> View return values of method calls
 Dans le code .NET et C++, vous pouvez examiner les valeurs de retour dans le **automatique** fenêtre lorsque vous arrivez sur ou hors d’un appel de méthode. Appel de méthode d’affichage valeurs de retour peuvent être utiles lorsqu’elles ne sont pas stockées dans des variables locales. Une méthode peut être utilisée en tant que paramètre, ou en tant que la valeur de retour d’une autre méthode.

 Par exemple, ce qui suit C# code ajoute les valeurs de retour de deux fonctions :

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

Pour afficher les valeurs de retour de la `sumVars()` et `subtractVars()` des appels de méthode dans la fenêtre automatique :

1. Définissez un point d’arrêt sur la ligne `int x = sumVars(a, b) + subtractVars(c, d);` .  
   
1. Démarrez le débogage et lors de l’exécution s’arrête au point d’arrêt, sélectionnez **pas à pas principal** ou appuyez sur **F10**. Vous devez voir les valeurs de retournés suivantes dans le **automatique** fenêtre :  
   
  ![Valeur de retour automatique C# ](../debugger/media/autosreturnvaluecsharp2.png "valeur de retour automatiqueC#")  
  
## <a name="see-also"></a>Voir aussi  
 [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)  
 [Corriger les bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md)  
 [Premier aperçu de débogage](../debugger/debugger-feature-tour.md) [fenêtres du débogueur](../debugger/debugger-windows.md)
