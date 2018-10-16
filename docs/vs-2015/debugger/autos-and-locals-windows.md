---
title: Automatique et variables locales Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94b583fee7f0e03fae3f194f1614d82016136e13
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191319"
---
# <a name="autos-and-locals-windows"></a>Fenêtres Variables locales et Automatique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre **Automatique** (lors du débogage, **CTRL+ALT+V, A**, ou **Déboguer/Fenêtres/Automatique**) et la fenêtre **Variables locales** (lors du débogage, **CTRL+ALT+V, L**, ou **Déboguer/Fenêtres/Variables locales**) s’avèrent particulièrement utiles quand vous voulez voir les valeurs de variables pendant le débogage. La fenêtre **Variables locales** affiche les variables définies dans la portée locale, qui est généralement la fonction ou méthode en cours d’exécution. La fenêtre **Automatique** affiche les variables utilisées autour de la ligne actuelle (l’emplacement où le débogueur est arrêté). Les variables affichées sont différentes selon les langages. Consultez quelles variables s’affichent dans la fenêtre automatique ? ci-dessous.  
  
 Si vous avez besoin de plus d’informations sur le débogage de base, consultez [Getting Started with the Debugger](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Examen des objets dans les fenêtres Automatique et Variables locales  
 Les tableaux et les objets sont affichés dans les fenêtres Automatique et Variables locales en tant que contrôles d’arborescence. Cliquez sur la flèche située à gauche du nom de variable pour développer la vue et afficher les champs et propriétés. Voici un exemple d’un <xref:System.IO.FileStream> de l’objet dans le **variables locales** fenêtre :  
  
 ![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Quelles variables s’affichent dans la fenêtre Automatique ?  
 Vous pouvez utiliser la fenêtre **Automatique** dans le code C#, Visual Basic et C++. La fenêtre **Automatique** ne prend pas en charge JavaScript ni F#.  
  
 En C# et Visual Basic, la fenêtre **Automatique** affiche n’importe quelle variable utilisée sur la ligne actuelle ou précédente. Par exemple, si vous déclarez quatre variables et les définissez comme suit :  
  
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
  
 Si vous définissez un point d’arrêt sur la ligne `c = 3`et exécutez le débogueur, la fenêtre **Automatique** doit ressembler à ceci quand l’exécution s’arrête :  
  
 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")  
  
 Notez que la valeur de `c` est 0, car la ligne `c = 3` n’a pas encore été exécutée.  
  
 En C++, la fenêtre **Automatique** affiche les variables utilisées au moins trois lignes avant la ligne actuelle (la ligne à laquelle l’exécution est arrêtée). Si vous déclarez six variables :  
  
```cpp  
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
  
 Si vous définissez un point d’arrêt sur la ligne `e = 5;` et exécutez le débogueur, la fenêtre **Automatique** doit ressembler à ceci quand l’exécution s’arrête :  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos-Cplus")  
  
 Notez que la variable e n’est pas initialisée, car le code de la ligne `e = 5;` n’a pas encore été exécuté.  
  
 Vous pouvez également voir les valeurs de retour des fonctions et des méthodes dans certaines circonstances. Consultez [View return values of method calls](#bkmk_returnValue) ci-dessous.  
  
##  <a name="bkmk_returnValue"></a> View return values of method calls  
 Dans le code .NET et C++, vous pouvez examiner les valeurs de retour quand vous effectuez un pas à pas principal ou sortant dans un appel de méthode. Cette fonctionnalité est utile quand le résultat d’un appel de méthode n’est pas stocké dans une variable locale, par exemple quand une méthode est utilisée comme paramètre ou valeur de retour d’une autre méthode.  
  
 Le code C# suivant ajoute les valeurs de retour de deux fonctions :  
  
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
  
 Définissez un point d’arrêt sur la ligne int `x = sumVars(a, b) + subtractVars(c, d);` .  
  
 Démarrez le débogage et, quand l’exécution s’arrête au premier point d’arrêt, appuyez sur **F10 (Pas à pas principal)**. Vous devez voir les éléments suivants dans la fenêtre **Automatique** :  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Pourquoi les valeurs de variables s’affichent-elles parfois en rouge dans les fenêtres Variables locales et Automatique ?  
 Vous pouvez remarquer que la valeur d’une variable est parfois en rouge dans les fenêtres **Variables locales** et **Automatique** . Il s’agit de valeurs de variables qui ont été modifiées depuis la dernière évaluation. Le changement peut provenir d’une session de débogage précédente, ou refléter la modification de la valeur dans la fenêtre.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Modification du format numérique d’une fenêtre de variable  
 Le format numérique par défaut est décimal, mais vous pouvez le remplacer par le format hexadécimal. Cliquez avec le bouton droit à l’intérieur de la fenêtre **Variables locales** ou **Automatique** et sélectionnez **Affichage hexadécimal**. La modification affecte toutes les fenêtres du débogueur.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Modification d’une valeur dans une fenêtre de variable  
 Vous pouvez modifier les valeurs de la plupart des variables qui apparaissent dans les fenêtres **Automatique**, **Variables locales**, **Espion**et **Espion express** . Pour plus d’informations sur les fenêtres **Espion** et **Espion express** , consultez [Watch and QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Double-cliquez sur la valeur que vous souhaitez modifier et ajoutez la nouvelle valeur.  
  
 Vous pouvez entrer une expression pour une valeur, par exemple `a + b`. Le débogueur accepte la plupart des expressions de langage valides.  
  
 Dans le code C++ natif, vous devrez peut-être qualifier le contexte d’un nom de variable. Pour plus d’informations, consultez [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
 Toutefois, soyez vigilant lorsque vous modifiez des valeurs. Voici quelques problèmes possibles :  
  
-   Évaluer certaines expressions peut modifier la valeur d’une variable ou affecter d’une manière ou d’une autre l’état de votre programme. Par exemple, l’évaluation de `var1 = ++var2` modifie la valeur de `var1` et `var2`.  
  
     Les expressions qui modifient les données sont réputées pour avoir des [effets secondaires](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))qui peuvent produire des résultats inattendus si vous n’êtes pas informé. Assurez-vous que vous comprenez les conséquences d’une telle modification avant de l’effectuer.  
  
-   Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans la variable à virgule flottante, même une modification apparemment anodine risque d’entraîner des changements de certains bits de poids faible.  
  
## <a name="debug-location-toolbar"></a>Barre d’outils Emplacement de débogage  
 Vous pouvez utiliser la barre d’outils **Emplacement de débogage** pour sélectionner la fonction, le thread ou le processus souhaité. Définissez un point d’arrêt et démarrez le débogage. (Si vous ne voyez pas cette barre d’outils, vous pouvez l’activer en cliquant dans une partie vide de la zone de la barre d’outils. Vous devez voir une liste de barres d’outils ; sélectionnez **Emplacement de débogage**). Lorsque le point d’arrêt est atteint, l’exécution s’arrête et vous pouvez voir la barre d’outils Emplacement de débogage, qui est la ligne inférieure de l’image suivante :  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Vous pouvez également remplacer le contexte par différents appels de fonction, threads ou processus en double-cliquant sur l’élément dans la fenêtre **Pile des appels** , **Threads** ou **Processus** .  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres du débogueur](../debugger/debugger-windows.md)





